# Demo craft

Read this when the script shows product UI, filmed or animated. These rules make a demo honest and readable on a phone.

## Honest speed

- Show real UI at real speed by default. Viewers judge speed from what they see.
- Cut dead time (loading, long typing, navigation) with jump cuts, not fake instant results.
- Speed-ups are fine for setup and typing. If speed is part of the claim ("in 10 seconds"), disclose any speed-up on screen ("2x") and keep the claimed action at 1x.
- Never speed up the "before" in a before/after, and never slow it down to look worse.
- Animated UI follows the real product's layout, copy, and states. If the product does not exist yet, the animation carries a "Concept" label for its full time on screen.

## One idea per scene

- Each scene shows one action and one result. Two things happening at once means two scenes.
- Keep the same sample data across scenes (same client names, same numbers) so the viewer follows one story.
- The scene's on-screen text names the result, not the feature ("Blocked: waiting on client", not "Status tracking").

## Cursor choreography

- Plan the cursor path before recording: start near the first target, move in straight lines or gentle arcs, arrive, pause 0.3 to 0.5s, click.
- One click per beat. No wandering, no circling to point at things, no hover-hunting.
- Hide the cursor when idle; enlarge or highlight it (ring or soft glow) when it matters.
- Click feedback: a subtle ring on click and an optional soft click SFX, aligned to the frame the UI changes.
- In motion builds, specify the cursor as an asset with start point, end point, and click frame per scene.

## Zoom to detail

- Zoom whenever the viewer must read something in the UI. Default 1.5 to 2x; up to 3x for a single field or cell.
- Zoom in on the element just before the action, hold through the result, zoom out to re-orient. Ease in and out over 0.4 to 0.6s.
- No more than one zoom move every 2 to 3s. Constant zooming reads as nervous.
- Never zoom into a blank area or across a scene cut.

## Readable text sizes

The size math: a 16:9 video in a phone feed shows about 390pt wide (common phones are 360 to 430pt). 1920px to 390pt scales by about 0.2, so 60px renders near 12pt, the smallest comfortable reading size. A 1080-wide frame (1:1, 4:5, 9:16) filling the same width scales by about 0.36, so 48px renders near 17pt; the extra margin covers platform overlays and a phone held at arm's length.

| Frame | Minimum text height | Key lines and titles |
| --- | --- | --- |
| 16:9, 1920x1080 | 60px | 90 to 120px |
| 1:1 or 4:5, 1080 wide | 48px | 72 to 96px |
| 9:16, 1080x1920 | 48px | 72 to 110px |

UI text must reach the same minimum after zoom. Worked check: 16px CSS text at 150% browser zoom records at 24px; reaching 60px needs a 2.5x zoom. If that is too tight a crop, enlarge the UI (browser zoom or a larger demo font) instead.

For 9:16 from a desktop product: record a narrow window (about 1080 wide at 150% zoom) or design a vertical layout for the motion build. Do not shrink a 16:9 recording into the middle of the frame.

## On-screen text pace

- Card hold time: at least 1.5s + 0.3s per word. 4 words: 2.7s. 7 words: 3.6s. This caps cards at about 2 words per second.
- At most one text card and the captions on screen at once.
- 2 to 7 words per card, at most 2 lines, sentence case.
- Never put on-screen text over a UI area the viewer needs to read.

## Safe zones

Keep text, faces, and key UI inside these areas. Approximate; each platform publishes and changes its overlay, so verify current before export.

| Frame | Keep clear |
| --- | --- |
| 9:16, 1080x1920 (TikTok, Reels, Shorts) | Top about 250px (account, search), bottom about 400px (caption, audio, CTA bar), left about 60px, right about 160px (like, comment, share rail) |
| 1:1 or 4:5 feed | About 5% margin on all sides; LinkedIn and X may overlay controls at the bottom |
| 16:9 (YouTube, website) | About 5% title-safe margin; bottom 15% clear when captions are on |

The resulting 9:16 safe box is roughly x 60 to 920, y 250 to 1520 (860 x 1270px).

## Screen recording setup

- Record at 1920x1080 or 2560x1440 with browser zoom at 125 to 150%. Export at 1080p minimum, 30fps (60fps if the UI motion is fast).
- Clean browser profile: no bookmarks bar, no extensions, no personal tabs, notifications off (OS and app).
- Seed a demo account with plausible sample data. Label it "Sample data" if a viewer could mistake it for a real customer. No real customer PII.
- Tools like Screen Studio or Descript add automatic zooms and cursor smoothing; still plan the path.
- Rehearse each flow 2 to 3 times, record each scene as its own take, and paste long strings instead of typing.
