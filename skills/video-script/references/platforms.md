# Platforms

Read this in step 11 when planning cutdowns and exports. Platform limits, overlays, and features change often. Everything marked "verify current" must be checked in the platform's own upload screen or help centre before export; do not quote these as fact to the founder.

## Spec sheet

| Platform | Aspect | Launch length to aim for | Captions | First frame / thumbnail | Verify current |
| --- | --- | --- | --- | --- | --- |
| X | 16:9 or 1:1 | 30 to 60s | Burn in, or upload an SRT | Autoplays muted; the first frame plus a text overlay is the thumbnail | Max length for the account type |
| LinkedIn | 1:1 or 4:5 for the feed, 16:9 if embedded elsewhere | 30 to 90s | Upload an SRT, and burn in for the feed cut | Custom thumbnail supported; design one | Length limits, thumbnail support on mobile |
| Product Hunt | 16:9 via a YouTube link in the gallery | 60 to 90s, under about 2 min | On the YouTube upload | Gallery images and thumbnail sizes per the `launch` channel notes (1270x760, 240x240 at the time of writing) | Submission form fields and sizes |
| YouTube | 16:9, 1080p or higher | 60s to 3 min | Upload SRT or VTT; check auto-captions | Custom thumbnail, 1280x720 | Chapter rules (first at 0:00, at least 3, each 10s or longer at the time of writing) |
| YouTube Shorts | 9:16, 1080x1920 | 15 to 45s | Burn in | Pick a frame; the title carries search | Max Shorts length |
| TikTok | 9:16, 1080x1920 | 15 to 45s | Burn in, or native captions | Pick a cover frame with 3 to 5 words inside the safe zone | Safe-zone overlay, sound licensing for business accounts |
| Instagram Reels | 9:16, 1080x1920 | 15 to 45s | Burn in | Cover shows on the profile grid cropped; keep the title centred | Grid crop ratio, max length |
| Website hero loop | 16:10 or 16:9 | 6 to 10s, silent, seamless loop | None needed if the UI reads alone | Poster image (AVIF or JPG) shown before play and under reduced motion | Browser codec support |
| Website demo | 16:9 | 60 to 90s | VTT track, captions on by default for muted autoplay | Poster frame from the product moment | none |

Rules that hold regardless of platform changes:
- Upload video natively; a bare link gets less reach on X and LinkedIn (heuristic).
- Keep launch posts in the lengths above even when the platform allows longer.
- One cut per aspect. Never letterbox a 16:9 inside 9:16.

## First frame and thumbnail

The first frame is the thumbnail in most feeds before autoplay starts. Design it as a still:

- 3 to 5 words of text at key-line size (see `demo-craft.md`), inside the safe zone.
- The product's real moment or the founder's face, not a logo.
- High contrast at phone size; test it at 25% zoom.
- For YouTube, design a separate 1280x720 thumbnail; it can differ from the first frame but must not promise what the video does not show.

## Website hero loop budget

- 6 to 10s, one action start to finish, last frame matching the first.
- Silent: no audio track at all (smaller file, and browsers allow muted autoplay).
- File size: target under about 2MB, hard ceiling about 3MB. Export MP4 (H.264) plus WebM (VP9 or AV1); 1280 to 1600px wide is usually enough for a hero.
- Markup: `muted`, `playsinline`, `loop`, `autoplay`, a poster, and a visible pause control (moving content over 5s needs pause, stop, or hide under WCAG 2.2.2).
- Under `prefers-reduced-motion`, show the poster and do not autoplay.

## Cutdown map from a 60s master

| Cut | Aspect | Length | Source | VO budget | Notes |
| --- | --- | --- | --- | --- | --- |
| Master | 16:9 | 60s | All scenes | 115 to 135 | Website, YouTube, Product Hunt |
| Feed cut | 1:1 or 4:5 | 30 to 60s | Master, reframed | Per length | LinkedIn, X; captions burned in |
| Vertical | 9:16 | 30s | Hook, turn, 2 product scenes, CTA | 58 to 67 | TikTok, Reels, Shorts; reframed or rebuilt in vertical |
| Teaser | 9:16 or 1:1 | 15s | Hook plus one payoff | 29 to 33 | Pre-launch |
| Hero loop | 16:10 | 6 to 10s | One product scene | none | Silent, seamless |
| GIF | 16:10 | 3 to 6s | The key action | none | Product Hunt gallery, README, email |
