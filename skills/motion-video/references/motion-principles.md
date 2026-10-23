# Motion principles

Read this when building the motion tokens (SKILL.md step 6), timing a storyboard, or when a preview "feels off" and you need a number to change. Values are house defaults at 30fps; deviate with a written reason.

## Frame math at 30fps

1 frame = 33.3ms. Convert once, in `timing.ts`: `frames = Math.round(ms / 1000 * 30)`.

| ms | 100 | 150 | 200 | 250 | 300 | 400 | 500 | 600 | 700 | 1000 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| frames | 3 | 5 | 6 | 8 | 9 | 12 | 15 | 18 | 21 | 30 |

## Timing ranges

| Motion | Duration | Frames @30 | Notes |
| --- | --- | --- | --- |
| Micro (tick appears, button press, cursor click pulse) | 150–300ms | 5–9 | Ease out or `crisp` spring |
| Element entrance | 400–700ms | 12–21 | Default 18 frames. Bigger or heavier elements take the longer end |
| Element exit | 70–80% of its entrance | 9–15 | Exits accelerate away; or skip the exit and hard cut |
| Scene transition (crossfade, push, wipe) | 300–600ms | 9–18 | Default 12. Hard cut on a beat is the default transition |
| Camera move on UI (zoom, pan) | 600–1200ms | 18–36 | Default 27. Hold before and after |
| Hold after a camera move lands | reading time of what it reveals | see below | Never move again before the viewer has read it |

## Easing set (the only curves in the video)

| Token | Curve | Use |
| --- | --- | --- |
| `standard` | `cubic-bezier(0.2, 0, 0, 1)` | Small UI changes, colour/state changes |
| `enter` | `cubic-bezier(0.16, 1, 0.3, 1)` | Entrances: quick start, long soft landing |
| `exit` | `cubic-bezier(0.4, 0, 1, 1)` | Exits: accelerate out of frame |
| `move` | `cubic-bezier(0.65, 0, 0.35, 1)` | On-screen to on-screen moves, camera zoom and pan |
| `linear` | `linear` | Only for continuous motion (a slow drift, a progress bar tied to time) |

In Remotion: `Easing.bezier(x1, y1, x2, y2)` passed to `interpolate(..., {easing})`.

## Spring presets (Remotion `spring()`)

Damping ratio ζ = damping / (2 × √(stiffness × mass)). ζ ≥ 1 never overshoots; below 1, overshoot ≈ e^(−πζ/√(1−ζ²)).

| Preset | Config | ζ | Overshoot | Use |
| --- | --- | --- | --- | --- |
| `settle` | `{damping: 200}` (stiffness 100, mass 1 defaults) | 10 | none | Calm entrances, text. Overdamped curves have a long tail, so always pass `durationInFrames` (for example 18) |
| `crisp` | `{damping: 26, stiffness: 170, mass: 1}` | 26 / (2 × 13.04) ≈ 1.0 | none visible | Default for UI elements, ticks, cards |
| `pop` | `{damping: 18, stiffness: 180, mass: 1}` | 18 / (2 × 13.42) = 0.67 | ≈ 6% | The one emphasis moment per video (the signature element). Never on text |
| Remotion default | `{damping: 10, stiffness: 100, mass: 1}` | 0.5 | ≈ 16% | Too bouncy for product video; do not use unconfigured `spring()` |

Measure how long a preset takes with `measureSpring({fps: 30, config})` from `remotion` before budgeting it into a scene.

## Reading time and holds

- On-screen text holds for at least 1.5s + 0.3s per word: frames = 45 + 9 × words. "Which client is blocked?" (4 words) needs 81 frames (2.7s).
- The hold counts from the moment the text is fully legible (entrance finished), not from the first frame it appears.
- 2–7 words per text card, at most 2 lines. More words means a second card or fewer words, never a shorter hold.
- A number or a detail revealed by a zoom needs its own hold: 1s minimum plus the reading rule if it has words.
- Text appears with its VO line: land it 0–4 frames before the matching word is spoken, never more than 6 frames after.

## Stagger

- 2–4 frames (66–133ms) between items in a group. Default 3.
- Whole group finishes inside 600ms (18 frames) where possible; past 8–10 items, stagger rows, not cells.
- Stagger in reading order (left to right, top to bottom) unless the story needs the reverse.

## Distance and scale

- Entrances travel 2–5% of the frame height: 24–54px at 1080p, 40–96px on 9:16. Large travel reads as a gimmick.
- Scale entrances start at 0.9–0.96, not 0. Starting from 0 is a template look.
- Zoom on UI: 1.4–2.0x. Never past the capture scale of the screenshot (2x capture, 2x zoom maximum).

## Anticipation and overshoot

- Use once or twice per video, on the element the story is about (the blocked row, the result number). Everywhere else: no overshoot.
- Anticipation: a 2–4 frame move of 4–8px in the opposite direction before a large move. Only on deliberate, physical-feeling moves.
- Never overshoot text, captions, or the logo.

## Focal point and hierarchy

- One focal point per frame. If two things move at once, one is primary (moves first, travels further, highest contrast) and the other follows within 4–8 frames with less travel, or only fades.
- Three tiers at most: primary moves, secondary follows, tertiary fades or stays still.
- Squint test on a still: blur it. The focal point must still be the brightest or most contrasting area.
- Dim or blur the rest of the UI (opacity 0.35–0.5 overlay) when zoomed to a detail, rather than adding arrows.

## Direction

- Pick one axis for "forward" in the story (usually left to right, or bottom to top on 9:16) and keep it: new content enters from the forward side, old content leaves the other way.
- Detail panels enter from the same side every time.
- A reverse move means "going back". Use it only when the story goes back.

## Kinetic typography

- Animate by line or phrase, not by letter. Word-by-word reveals only for 7 words or fewer, paced at the speaking rate (about 2.5 words per second, 12 frames per word).
- One animated text element on screen at a time. Supporting text appears static.
- No bouncing, rotating, or elastic text. Keep the baseline still; animate opacity, small y offset, or a mask reveal.
- Emphasis is a weight or colour change on one word, not motion on every word.
- Tracking animations (letter-spacing) under 0.02em total change, or not at all.

## Camera moves on UI

- Sequence: wide (establish, hold 1–1.5s) → move (27 frames, `move` easing) → hold on the detail (reading time) → pull back or cut.
- Move in one direction at a time. Do not zoom and pan in opposite directions at once.
- Set `transform-origin` to the centre of the target element, checked in the Studio at the end frame.
- At most one camera move per scene. Two moves in a row: cut between them instead.
- No constant slow drift on UI; it makes text harder to read. A slow push (1.0 to 1.05 over the scene) is fine on non-text visuals.

## Cursor choreography

- Cursor about 40–48px tall at 1080p (larger than real) with a subtle shadow so it reads on any UI.
- Moves follow a slight arc, 12–20 frames per move, `move` easing. Straight robotic lines look synthetic.
- Pause 6–10 frames over a target before clicking; click = 6-frame scale to 0.9 and back plus a ring pulse that fades over 9 frames.
- Hide the cursor when it is not doing something. Never wiggle it to show "activity".

## Type scale for video

Text sizes are set for a phone held at arm's length, the worst case for every deliverable.

- 16:9 at 1920x1080: base 40px, ratio 1.414 → 40, 56.6, 80, 113. Tokens: body 40, title 56, headline 80, display 112, caption 44, minimum 32 (3% of frame height).
- 9:16 at 1080x1920 (width governs): base 48px, ratio 1.333 → 48, 64, 85.3, 113.7. Tokens: body 48, title 64, headline 84, display 112, caption 56, minimum 40.
- 1:1 at 1080x1080: base 44px, ratio 1.333 → 44, 58.7, 78.2, 104.3. Tokens: body 44, title 60, headline 80, display 104, caption 48, minimum 36.
- Line height 1.05–1.15 for display, 1.25–1.35 for body and captions. Captions at most 2 lines of about 32–42 characters.
- Weight: 400 minimum for body at these sizes; 600 for captions. Hairline display faces only at 80px and above.

## Contrast

Every text/background pair at 4.5:1 or more (3:1 only for text at 80px and above, a house rule stricter than WCAG's large-text threshold because video is viewed small), measured against the actual pixels behind it. Text over footage or busy UI gets a solid or 80%+ opacity backing. Compute, do not guess:

```js
// WCAG contrast ratio, e.g. contrast('#59625C', '#F6F3EA')
function contrast(a, b) {
  const lum = (hex) => {
    const [r, g, b] = hex.replace('#', '').match(/.{2}/g).map((h) => {
      const c = parseInt(h, 16) / 255;
      return c <= 0.03928 ? c / 12.92 : ((c + 0.055) / 1.055) ** 2.4;
    });
    return 0.2126 * r + 0.7152 * g + 0.0722 * b;
  };
  const [hi, lo] = [lum(a), lum(b)].sort((x, y) => y - x);
  return Math.round(((hi + 0.05) / (lo + 0.05)) * 100) / 100;
}
```

## Product UI in video

| Source | When | Rules |
| --- | --- | --- |
| Recreated UI as components | UI is simple (lists, boards, cards), needs animating per element, or does not exist yet | Match real spacing and type; sample data only; label "Prototype" or "Concept" if it is not shipped |
| Real screenshots | UI exists and is visually dense | Capture at 2x (`deviceScaleFactor: 2`, or Retina); seeded demo account; crop to the region that matters |
| Screen recordings | Real interaction matters (drag, typing, loading) | Constant frame rate, 1080p+ at 125–150% browser zoom, clean profile, notifications off; speed up dead time |

- Never fake a feature. Recreated UI shows only what exists or is labelled.
- Strip real customer names, emails, and amounts. Sample data reads as plausible but fictional.
- Simplify recreated UI to the elements the scene is about. Removing chrome is fine; adding features is not.
- Social 9:16 safe zones (approximate; verify current overlays): keep text and key UI out of the top 250px, bottom 350px, and right 140px of a 1080x1920 frame.
- Captions are burned in for every social cut. The website and YouTube get `.srt`/`.vtt` files as well.

## Audio sync

- Frames per beat = 60 × fps / BPM = 1800 / BPM at 30fps. 120 BPM = 15 frames, 100 BPM = 18, 90 BPM = 20.
- Non-integer results (128 BPM = 14.06) drift if you add a rounded beat repeatedly. Place beat n at `Math.round(n * 1800 / BPM)` from the music's first downbeat.
- Cut on beats; put major section changes on bar lines (4 beats). Not every beat needs a cut; 1.5–3s between cuts is the usual range.
- Lock the VO first (scratch read on a phone is enough to time against), then time animation to the VO, then fit music. Music is edited to the picture, not the reverse.
- SFX (ticks, clicks, whooshes) only where an on-screen event happens, 0–2 frames before the visual event, quiet. Not on every element.

## The "AI template" look (banned by default)

Each needs a subject-specific reason written in the plan to survive:

- Random particle fields, floating dots, bokeh, or light leaks as background filler.
- Generic glowing gradients, purple-to-blue washes, neon on dark by default.
- Spinning or extruded 3D logos, logo reveals as the opening shot.
- Every word bouncing, typewriter text everywhere, text that rotates in.
- Floating tilted device mockups orbiting in 3D space.
- Glitch, RGB split, or shake transitions on a calm B2B product.
- Stock "whoosh" on every transition.
- Kinetic-type lists of features ("Fast. Simple. Powerful.").
- Counters ticking up to invented numbers.

What replaces them: the customer's material world (the spreadsheet, the ledger, the clipboard), real or honestly labelled UI, one signature motion idea repeated with discipline, and restraint everywhere else.
