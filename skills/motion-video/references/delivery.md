# Delivery

Read this when rendering is done and you are encoding deliverables (SKILL.md step 9): platform specs, ffmpeg recipes, the website hero loop, poster frames, loudness, and size budgets. Platform rules change often; everything in the specs table is "verify current" against the platform's own help pages before publishing.

## ffmpeg setup

- A system ffmpeg (`ffmpeg -version`) is best: it has `loudnorm`, `subtitles` (libass), and `libwebp`, which minimal builds may lack.
- In a Remotion project, `npx remotion ffmpeg` and `npx remotion ffprobe` work with no install, but the bundled binary only encodes H.264, H.265, VP8, VP9, and ProRes (verify current). In the 4.0.538 build it had `loudnorm` and `palettegen` but not `ebur128` or `subtitles`. Use it for MP4 and WebM; use a system ffmpeg for loudness measurement and subtitle burn-in.
- Render Remotion masters with `--color-space=bt709`. Without it, the 4.0.538 default produced full-range `yuvj420p` files; with it, limited-range `yuv420p` tagged BT.709, which is what YouTube recommends for SDR. If a source is already full range (`color_range=pc` in ffprobe), add `out_range=tv` to the `scale` filter when re-encoding.
- Commands below are single-line so they run unchanged in PowerShell, bash, and zsh. On Windows, two-pass encodes write the first pass to `NUL` instead of `/dev/null`.

## Defaults that make files play everywhere

| Setting | Value | Why |
| --- | --- | --- |
| Codec | H.264 (`libx264`) in MP4 | Universal playback; YouTube recommends H.264 High profile in MP4 |
| Pixel format | `-pix_fmt yuv420p` | 4:2:0 is what browsers, phones, and platforms decode reliably; 4:4:4 or 10-bit fails in places |
| Dimensions | Even numbers; scale with `-2` (`scale=1280:-2`) | yuv420p requires even width and height |
| Rate control | CRF. 18 = visually near-lossless master; 20–23 for uploads; 24–28 for web loops | x264 CRF scale is 0–51, default 23, sane range 17–28; +6 roughly halves the size |
| Preset | `-preset slow` | Smaller file at the same quality; use `medium` if time matters |
| Fast start | `-movflags +faststart` | Moves the index (moov atom) to the front so web playback starts before the download finishes |
| Audio | AAC, 48kHz, 192–320 kbps stereo | 48kHz matches YouTube's recommendation and Remotion's default |
| Frame rate | Keep the source rate (30) | Never convert 30 to 60 or 24 at encode time |

## Platform specs (verify current)

| Deliverable | Aspect | Resolution | fps | Length guidance | Captions | File |
| --- | --- | --- | --- | --- | --- | --- |
| YouTube | 16:9 | 1920x1080 (3840x2160 if the source is crisp at 4K) | 30 | Launch 60–90s; demos 2–3 min | Upload `.srt`/`.vtt`; burned-in optional | MP4, H.264 High, AAC 48kHz, faststart |
| YouTube Shorts | 9:16 | 1080x1920 | 30 | 15–45s; vertical or square uploads up to 3 min are classed as Shorts (verify current) | Burned in | MP4 H.264 |
| Instagram Reels | 9:16 | 1080x1920 | 30 | 15–45s; Instagram reports that Reels over 3 min are not recommended to new audiences (verify current) | Burned in | MP4 H.264 |
| TikTok | 9:16 | 1080x1920 | 30 | 15–45s; maximum durations vary by account and region | Burned in | MP4 H.264 |
| LinkedIn feed | 1:1 or 4:5 (16:9 accepted) | 1080x1080 / 1080x1350 | 30 | 30–90s; organic maximums reported between 10 and 15 min, 5GB | Upload `.srt` and burn in | MP4 H.264 |
| X | 16:9 or 1:1 | 1920x1080 / 1080x1080 | 30 | Under 2:20 (140s) and 512MB for non-Premium accounts (verify current) | Burned in (feed autoplays muted) | MP4 H.264, AAC |
| Product Hunt gallery | 16:9 | 1920x1080 | 30 | Under about 2 min | Burned in or YouTube captions | Listing takes a YouTube link at the time of writing (verify in the submission form) |
| Website hero loop | 16:9 or 16:10 | 1600–1920 wide | 24–30 | 6–12s, seamless loop, no audio | None (must read without words) or one text card | MP4 H.264 + WebM VP9, poster image |
| README / email GIF | 16:10 | 800–1000 wide | 12–15 | 3–6s | None | GIF (or MP4 where supported) |

## Recipes

### Inspect a file

```powershell
ffprobe -v error -show_entries stream=codec_name,pix_fmt,color_range,width,height,r_frame_rate -show_entries format=duration,size -of compact out/launch-16x9.mp4
```

Check: `h264`, `yuv420p` (not `yuvj420p`), `color_range=tv`, expected dimensions, `30/1`, expected duration in seconds = frames / 30.

### Re-encode a master for upload

```powershell
ffmpeg -i out/launch-16x9.mp4 -c:v libx264 -preset slow -crf 20 -pix_fmt yuv420p -c:a aac -b:a 192k -ar 48000 -movflags +faststart deliver/launch-16x9-youtube.mp4
```

### Normalise a screen recording before using it as a source

Screen recorders often write variable frame rate, which drifts against a 30fps timeline.

```powershell
ffmpeg -i raw/recording.mov -vf "fps=30,scale=1920:-2:flags=lanczos" -c:v libx264 -crf 16 -preset slow -pix_fmt yuv420p -an public/ui/recording-30fps.mp4
```

### Cut a range from a master (frame-accurate)

Seconds = frame / 30. Re-encoding makes the cut exact; stream copy (`-c copy`) snaps to keyframes and is not frame-accurate.

```powershell
ffmpeg -ss 11.5 -i out/launch-16x9.mp4 -t 8.5 -c:v libx264 -crf 20 -preset slow -pix_fmt yuv420p -c:a aac -b:a 192k -movflags +faststart deliver/clip-board.mp4
```

For social cutdowns, prefer rendering selected scene ranges directly from Remotion (`--frames=0-89,345-869,1440-1559` concatenates ranges in one file; verify audio continuity at each join) or, better, a dedicated composition for the cut so text timing is designed for it.

### Measure and set loudness

About -14 LUFS integrated with true peaks at or below -1 dBTP is a common target for YouTube and social uploads. Platforms publish little about their normalisation and change it; verify current guidance. Speech-led website video can sit around -16 LUFS because it plays on laptop speakers next to silence.

Measure:

```powershell
ffmpeg -hide_banner -i out/launch-16x9.mp4 -vn -af ebur128=peak=true -f null NUL
```

Read `I:` (integrated, LUFS) and `Peak:` (true peak) in the summary at the end of the output. On macOS/Linux use `-f null -` instead of `NUL`.

Normalise (single pass; good enough for short videos):

```powershell
ffmpeg -i out/launch-16x9.mp4 -c:v copy -af loudnorm=I=-14:TP=-1:LRA=11 -c:a aac -b:a 192k -ar 48000 -movflags +faststart deliver/launch-16x9-loud.mp4
```

Mix rule: VO is the reference; music sits about 15–20 dB under it and ducks further under dense lines; SFX are felt, not heard.

### Burn captions with ffmpeg (if not burned in the composition)

Prefer the caption component in the composition: it uses the brand font and respects safe zones per aspect. If you must burn an `.srt` afterwards (needs an ffmpeg built with libass):

```powershell
ffmpeg -i out/launch-9x16.mp4 -vf "subtitles=captions.srt:force_style='FontName=IBM Plex Sans,FontSize=14,MarginV=120'" -c:v libx264 -crf 20 -pix_fmt yuv420p -c:a copy -movflags +faststart deliver/launch-9x16-captioned.mp4
```

`FontSize` here is in libass script units, not pixels; check a still and adjust. Escaping Windows paths inside `subtitles=` is fragile; run from the folder that holds the `.srt`.

## Website hero loop

Target: 6–12s, silent, seamless, under a size budget, with a poster and a reduced-motion fallback. Build it as its own composition (for example `Hero-loop`, 240 frames) where the last frame flows into the first: every element that moves returns to its frame-0 state by the final frame, or the loop ends on a hard cut that matches frame 0.

Render silent, then encode both formats:

```powershell
npx remotion render src/index.ts Hero-loop out/hero-master.mp4 --codec=h264 --crf=16 --color-space=bt709 --muted
ffmpeg -i out/hero-master.mp4 -an -vf "scale=1600:-2:flags=lanczos" -c:v libx264 -preset slow -crf 26 -maxrate 2.5M -bufsize 5M -pix_fmt yuv420p -movflags +faststart deliver/hero.mp4
ffmpeg -i out/hero-master.mp4 -an -vf "scale=1600:-2:flags=lanczos" -c:v libvpx-vp9 -crf 36 -b:v 0 -row-mt 1 deliver/hero.webm
```

If a file is over budget: raise CRF by 2 and re-encode (each +6 roughly halves the size), then reduce width to 1280, then shorten the loop. Do not drop below 24fps.

VP9 notes: constant quality mode needs `-crf` together with `-b:v 0`; the VP9 CRF scale is 0–63, with 15–35 the usual range (31 suggested for 1080p by the ffmpeg wiki); `-row-mt 1` speeds up encoding.

Poster frame (the frame shown before playback and under reduced motion; pick a frame that explains the product without motion):

```powershell
npx remotion still src/index.ts Hero-loop out/hero-poster.png --frame=150
ffmpeg -i out/hero-poster.png -vf "scale=1600:-2" -q:v 3 deliver/hero-poster.jpg
```

Without Remotion: `ffmpeg -ss 5 -i deliver/hero.mp4 -frames:v 1 -q:v 3 deliver/hero-poster.jpg`. Convert to AVIF/WebP with the site's image pipeline.

Embed (hand the files and this snippet to `website-design`, which owns placement):

```html
<video class="hero-loop" muted loop playsinline preload="metadata"
       poster="/video/hero-poster.jpg" width="1600" height="900" aria-hidden="true">
  <source src="/video/hero.webm" type="video/webm">
  <source src="/video/hero.mp4" type="video/mp4">
</video>
<button type="button" class="hero-loop-toggle" aria-pressed="false">Pause animation</button>
<script>
  const v = document.querySelector('.hero-loop');
  const btn = document.querySelector('.hero-loop-toggle');
  const reduce = window.matchMedia('(prefers-reduced-motion: reduce)');
  // Autoplay only when the visitor has not asked for reduced motion; otherwise the poster stays.
  if (!reduce.matches) v.play().catch(() => {});
  btn.addEventListener('click', () => {
    const pause = !v.paused;
    pause ? v.pause() : v.play();
    btn.setAttribute('aria-pressed', String(pause));
    btn.textContent = pause ? 'Play animation' : 'Pause animation';
  });
</script>
```

`aria-hidden="true"` is right only when the loop is decorative and the page text already says what it shows. If the loop carries information, remove it and describe the loop in adjacent text. A loop longer than 5 seconds needs the pause control (WCAG 2.2.2).

## GIF (README, email, Product Hunt gallery)

```powershell
ffmpeg -i deliver/clip-board.mp4 -vf "fps=15,scale=900:-1:flags=lanczos,split[a][b];[a]palettegen[p];[b][p]paletteuse" -loop 0 deliver/board.gif
```

GIFs are large: keep them 3–6s and under about 5MB (heuristic). Lower fps to 12 or width to 720 before cutting duration.

## Size budgets

Bitrate needed for a size target: video kbps = (size in MB × 8000) / seconds − audio kbps.

| Deliverable | Budget (heuristic) | Example |
| --- | --- | --- |
| Website hero loop | ≤ 3MB for 8s (≤ 5MB for 12s) | 3 × 8000 / 8 = 3000 kbps total, so `-maxrate 2.5M` leaves headroom |
| Social upload | No tight budget; quality first (CRF 18–20). Platforms re-encode | 50s at about 8 Mbps is about 50MB |
| Email or README GIF | ≤ 5MB | 4s at 900px, 15fps |
| Ads | Check the ad platform's own limit | LinkedIn and X ads have stricter limits than organic posts |

For a hard size limit, use two-pass with the computed bitrate instead of CRF:

```powershell
ffmpeg -y -i out/hero-master.mp4 -an -c:v libx264 -preset slow -b:v 2600k -pass 1 -f null NUL
ffmpeg -i out/hero-master.mp4 -an -c:v libx264 -preset slow -b:v 2600k -pass 2 -pix_fmt yuv420p -movflags +faststart deliver/hero.mp4
```

## Delivery checklist

- Every file probed: codec, `yuv420p`, dimensions, 30fps, duration matches the storyboard to the frame.
- Captions: burned into every social cut; `.srt`/`.vtt` alongside the YouTube, LinkedIn, and website files; spelling of product names checked by hand.
- Loudness measured and recorded per file with audio.
- Hero loop: both formats under budget, poster exported, loop seam checked by playing it 3 times.
- File names say what they are: `<project>-<cut>-<aspect>-v<n>.mp4` (for example `launch-30s-9x16-v2.mp4`).
- Masters and raw recordings kept out of git; deliverables in one folder with a short `README` listing each file and where it goes.
