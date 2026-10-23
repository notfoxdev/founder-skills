# Storyboard hand-off for motion-video

Read this in step 10 when the production mode is motion graphics or hybrid. `video-script` owns the words, story, and timing; `motion-video` owns the build (animation code, rendering, easing values). This block is the contract between them. Write it once the script and VO are locked, then end with "Use `motion-video` to build it."

## Block format

One fenced `yaml` block per cut (master first, then each cutdown that is rebuilt rather than re-edited).

```yaml
storyboard:
  title: <project and cut name>
  version: 1
  fps: 30
  resolution: 1920x1080          # 1080x1920 for 9:16, 1080x1080 for 1:1, 1080x1350 for 4:5
  aspect: "16:9"
  duration_s: 60
  duration_frames: 1800          # duration_s x 30
  safe_area: <e.g. "5% title-safe" or "9:16 box x60-920 y250-1520">
  style:
    source: <website-design entry or [NEED: palette and type]>
    palette: { <name>: "<hex>", ... }
    type: { display: <font>, body: <font>, mono: <font> }
    min_text_px: 60              # per the size table in demo-craft.md
  audio:
    vo: <who, file name or [NEED: VO recording]>
    music: { mood: <one line>, bpm: <n>, frames_per_beat: <1800 / bpm>, source: <[NEED: licensed track]> }
  labels:
    - { text: "Concept", scenes: [<ids>], position: top-left, persistent: true }
  scenes:
    - id: S01
      beat: hook                 # hook | problem | turn | product | proof | cta | end
      start_s: 0.0
      start_frame: 0
      duration_s: 2.0
      duration_frames: 60
      on_screen_text: "<exact words, or none>"
      visual: <what is on screen, in concrete nouns: objects, UI state, data>
      motion: <intent in plain verbs and feel: what moves, from where to where, and why>
      transition_out: <cut | match cut | push | wipe | morph | fade> on <beat/bar or frame>
      vo: "<exact line, or none>"
      audio: <music cue and SFX with the frame they hit>
      assets:
        - { name: <asset>, type: <svg | screenshot | recording | font | photo | audio>, status: <have | NEED> }
```

## Field rules

- `id`: S01, S02, ... in order. Cutdown scenes use C01, C02, ... and may add `from: <master id>`, listing only the fields that change (timing, layout, text, VO); everything else is inherited from the master scene.
- Seconds and frames: frames = seconds x 30, whole frames only. `start_frame` of each scene = previous `start_frame` + previous `duration_frames`. The scene frames must sum exactly to `duration_frames`.
- Durations: whole beats when BPM is known (frames per beat = 1800 / BPM; 15 at 120 BPM). Big changes on bar lines. Minimum 1.5s per scene except the hook and a deliberate flash cut.
- `on_screen_text`: the exact words, held per the hold rule (1.5s + 0.3s per word) inside the scene, at or above `min_text_px`.
- `visual`: what the viewer sees, using the same sample data as every other scene. Say if UI is real (`screenshot`, `recording`) or a concept.
- `motion`: intent, not implementation. "Cells slide into rows like a ledger being ruled, quick and orderly, settle by frame 20" is right. Easing curves, spring values, and component names are `motion-video`'s call.
- `transition_out`: one per scene; the last scene uses `end`.
- `vo`: exact words; the scene's words divided by `duration_s` must be 2.7 or less.
- `audio`: music changes and SFX tied to a frame offset inside the scene ("tick SFX at +18f").
- `assets`: every logo, screenshot, photo, font, and track the scene needs, with `have` or `NEED`. Anything `NEED` also appears in the answer's Open items.

## Honesty rules carried into the build

- Any UI not built in the product is listed in `labels` with a persistent "Concept" or "Prototype" label.
- No logos, customer names, quotes, or numbers in any field unless they trace to `company.md`, the founder, or a permission on file.
- Sample data is labelled "Sample data" if a viewer could mistake it for a real customer.
- Nothing flashes more than 3 times per second. Provide a reduced-motion poster frame (name the scene and frame).

## Pre-hand-off checks

| Check | Pass when |
| --- | --- |
| Frame sum | Scene frames add up to `duration_frames` |
| Start frames | Each equals the running total |
| VO pace | Every scene 2.7 words per second or less |
| Text holds | Every card held at least 1.5s + 0.3s per word |
| Beat grid | Durations are whole beats (if BPM set) |
| Labels | Every concept scene covered |
| Assets | Every `NEED` listed in Open items with an owner |

Close the section with exactly: "Use `motion-video` to build it."
