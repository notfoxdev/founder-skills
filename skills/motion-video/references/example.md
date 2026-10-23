# Worked example: motion-video

> Illustrative and fictional (Ledgerline fixture). Calibrates depth and format only; never reuse its content, palette, or timings in a real answer.

**Request:** "Turn our launch script into a 50-second video with Remotion. Make it pop, maybe a 3D logo spin at the start."

**Context used:** `evals/fixture-company.md` as `.foundora/company.md`. Validation stage, two full-time founders, no revenue, 2 concierge pilots starting next week, no product UI exists. Tone: direct, tables over paragraphs, US spelling. `.foundora/journal.md` holds two earlier decisions: website-design chose ledger paper `#F6F3EA`, ink `#1B2420`, tick-red `#A3341F`, Libre Caslon Display with IBM Plex Sans/Mono; video-script wrote a 60s demo with a painful-moment hook on the close spreadsheet and a prototype labelled on screen. No logo file, VO recording, or music in the repo.

Hard parts shown: the license check before choosing the tool, pushback on the 3D logo open, a text card that failed the reading rule and was retimed, a VO line too dense for its scene, no product UI (labelled prototype), and `[NEED: ...]` for every missing asset.

---

## Recommendation
Build a 52s 16:9 master in Remotion (Free License fits a 2-person company; one question below), plus a 1:1 LinkedIn master, a 27s 9:16 cut, and an 8s silent hero loop. No 3D logo spin: the first 2 seconds must show the problem, and a spinning logo is the most recognizable template opening there is. The logo lands on the end card instead, on a hand-drawn tick that is the video's one signature motion. Rendering waits on `[NEED: VO recording]`, `[NEED: licensed music track]`, and `[NEED: wordmark SVG]`; everything else is buildable today with scratch timing.

One question: will anyone besides you and Priya (a contractor, freelancer, or agency) work on this Remotion project? If yes, the team may count as 4+ under Remotion's terms and needs a Company License; I'd switch to the license-free HTML capture path rather than buy one for a single video.

## Brief
- Goal: make the launch feel real and drive waitlist signups | Platforms: landing page, LinkedIn, YouTube `[ASSUMPTION]`, Shorts/Reels cut
- Length: 52.0s (1560 frames at 30fps) | Aspects: 16:9 master, 1:1, 9:16 cutdown, 16:9 hero loop
- Source: video-script's 60s demo (journal), trimmed to 52s; video-script owns the words, edits flagged below
- VO: `[NEED: VO recording]`, timed now against a scratch read at 2.5 words/s | Music: `[NEED: licensed track, ideally 120 BPM]`
- Tool: Remotion 4.x, Free License `[ASSUMPTION: 2 people, no contractors on the project]` (verify current terms at remotion.dev/docs/license)
- Founder asks I pushed back on: 3D logo spin at the start (replaced by the tick end card); "make it pop" (read as: tighter pacing and one emphasis moment, not more motion)

## Storyboard (30fps)

Rule applied: text holds 45 + 9 × words frames after it is fully in. Every cut lands on a beat at 120 BPM (all scene starts are multiples of 15 frames).

| ID | Time | Frames (start–end, dur) | On-screen text (words: hold) | Visual | Motion intent | Transition in | VO (words, words/s) | Assets |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| S01 | 0:00.0–0:03.0 | 0–89 (90) | "Which client is blocked?" (4: 81f, in at f0) | Sample close spreadsheet mid-scroll, comment "is this reconciled??" | Scroll decelerates over 20f; comment pops in at f24 (crisp) | none (first frame is the hook, no fade) | "Which client is blocked?" (4, 1.3) | SheetMock, sample data |
| S02 | 0:03.0–0:09.0 | 90–269 (180) | "Close, in a spreadsheet" (4: 81f, in at f24) | Same sheet, five fill colors, second comment thread | Slow push 1.0 to 1.08 over the scene; one cell flips yellow to orange at f90 | hard cut | "Month-end close in a spreadsheet. Color codes, cell comments, and nobody sure what's reconciled." (14, 2.3) | SheetMock |
| S03 | 0:09.0–0:12.0 | 270–359 (90) | "A close board" (3: 72f, in at f18) | Empty close board on ledger paper; "Prototype. Sample data." label from here to 0:48 | Board rules draw left to right (move easing, 18f) | hard cut on the downbeat | "So we're building a close board." (6, 2.0) | CloseBoard |
| S04 | 0:12.0–0:20.0 | 360–599 (240) | "1 row per client. 1 column per step." (8: 117f, in at f18) | 6 sample clients x 6 steps; ticks draw row by row | Tick stroke draws in 9f each, 3f stagger, reading order | continuous | "Every client is a row. Every close step is a column. A tick means done, and who did it." (18, 2.3) | CloseBoard |
| S05 | 0:20.0–0:29.0 | 600–869 (270) | "Blocked: waiting on client" (4: 81f, in at f60) | Row C-04 stops at AP, note "Waiting on client: card statement" | Hold wide 30f, camera 1.0 to 1.8x on C-04 over 27f, rest of board dims to 40% | continuous | "This one is stuck at accounts payable. The reason is right there: waiting on the client's card statement." (18, 2.0) | CloseBoard, Camera |
| S06 | 0:29.0–0:37.0 | 870–1109 (240) | "See what's already reconciled" (4: 81f, in at f30) | Client checklist panel: reconciled accounts, initials and dates in mono | Panel enters from the right (forward side), 18f enter easing; rows stagger 3f | push from right | "Reviewers see what's already reconciled, so nobody redoes Tuesday's work." (10, 1.3) | ClientChecklist |
| S07 | 0:37.0–0:44.0 | 1110–1319 (210) | "5 ready. 1 blocked." (4: 81f, in at f36) | Pull back to full board; summary line "5 of 6 ready for review. 1 blocked." | Camera 1.8 to 1.0 over 27f; summary counts are static text, no tick-up counter | hard cut | "Partners see the whole month: five ready for review, one blocked." (11, 1.6) | CloseBoard, SummaryLine |
| S08 | 0:44.0–0:48.0 | 1320–1439 (120) | "Built by a former firm ops lead" (7: 108f, in at f12) | Paper card, Caslon headline, small mono line "2 firms piloting now" | Settle entrance 18f, no other motion | hard cut | "Two firms are piloting it now." (6, 1.5) | TextCard |
| S09 | 0:48.0–0:52.0 | 1440–1559 (120) | "Join the waitlist" (3: 72f, in at f12) + "ledgerline.app" | Blocked C-04 cell resolves to a tick, then wordmark and URL on paper | Tick draws with the pop spring (the one overshoot in the video); last 60f static | hard cut | "Join the waitlist at ledgerline dot app." (7, 1.8) | EndCard, `[NEED: wordmark SVG]` |

Totals: 1560 frames = 52.0s. VO 94 words, 1.8 words/s average, densest scene S02 and S04 at 2.3 (limit 2.7).

Revisions made while timing:
- S01 was 2.5s (75f). The hook card needs 81f, so it failed the reading rule; S01 grew to 90f and S02 gave back 0.5s. The hook text is on screen at frame 0 with no entrance: the first frame is also the thumbnail and the muted autoplay frame.
- S03 was 2.5s (75f). "A close board" needs 18f in + 72f hold = 90f; S03 grew to 3.0s, S04 shrank from 8.5s to 8.0s and still fits its 8-word card (18 + 117 = 135f of 240).
- S08 VO in the source script was "I ran ops at a bookkeeping firm for four years. Two firms are piloting Ledgerline now." (16 words in 4s = 4.0 words/s, over the 2.7 limit). The credential moved to the on-screen card and the VO kept the pilot line. `[NEED: founder approves the VO edit, or rerun video-script for the 52s cut]` and `[NEED: confirm the pilots have started on record day]`, since the file says they start next week.

## Motion design system

### Palette (from the website-design journal entry; contrast computed)
| Token | Hex | Role in video | Contrast |
| --- | --- | --- | --- |
| `paper` | `#F6F3EA` | Background of every scene | base |
| `ink` | `#1B2420` | Text, ticks, caption backing | 14.34:1 on paper |
| `pencil` | `#59625C` | Column headers, labels, dates | 5.69:1 on paper |
| `rule` | `#C5D3C2` | Ledger rules only, never text | 1.41:1 on paper (decoration) |
| `tick` | `#A3341F` | Blocked state, the end-card tick | 6.17:1 on paper |
| `reconciled` | `#2D5C4C` | Reconciled rows in S06 | 6.89:1 on paper |

Rejected: an ink-background end card with a red tick. Tick-red on ink is 2.32:1, under 3:1 even for a graphic, so the end card stays on paper.

### Type scale
| Token | 16:9 (1920x1080) | 9:16 (1080x1920) | 1:1 (1080x1080) | Face |
| --- | --- | --- | --- | --- |
| display | 112/118 | 112/118 | 104/110 | Libre Caslon Display 400 |
| headline | 80/88 | 84/92 | 80/88 | Libre Caslon Display 400 |
| title | 56/64 | 64/72 | 60/68 | IBM Plex Sans 600 |
| body | 40/52 | 48/60 | 44/56 | IBM Plex Sans 400 |
| caption | 44/56 | 56/68 | 48/60 | IBM Plex Sans 600 on ink at 88% |
| min (labels) | 32 | 40 | 36 | IBM Plex Mono 400 |

Computation: 16:9 base 40 x 1.414^n = 56.6, 80, 113; 9:16 base 48 x 1.333^n = 64, 85.3, 113.7; 1:1 base 44 x 1.333^n = 58.7, 78.2, 104.3; rounded to 4px.

### Motion tokens
| Token | Value | Used for |
| --- | --- | --- |
| `ease.move` | `cubic-bezier(0.65, 0, 0.35, 1)` | Camera zoom and pull back, board rules drawing |
| `ease.enter` | `cubic-bezier(0.16, 1, 0.3, 1)` | Panel and card entrances |
| `springs.crisp` | damping 26, stiffness 170, mass 1 | Comments, labels, checklist rows |
| `springs.settle` | damping 200, `durationInFrames` 18 | Text cards |
| `springs.pop` | damping 18, stiffness 180, mass 1 (~6% overshoot) | Only the S09 tick |
| `dur` | enter 18, tick 9, stagger 3, camera 27 | All scenes |
| Signature motion | A pencil-style tick drawn by SVG `strokeDashoffset`, never faded | Board cells, S09 end card |

## Build

- Project: `video/` in the repo `[ASSUMPTION: the founders want it next to the site code]`. Scaffold: `npx create-video@latest --yes --blank video`, then `npx remotion add @remotion/google-fonts @remotion/media`. Dependencies added: those two, version-matched to `remotion` by `npx remotion add`. `out/` added to `.gitignore`.
- Compositions: `Launch-16x9`, `Launch-1x1`, `Cut30-9x16` (S01, S03, S04, S05, S09 = 810 frames, 27.0s), `Hero-loop` (240 frames, silent).

| Scene | Component | Shared components |
| --- | --- | --- |
| S01, S02 | `scenes/Spreadsheet.tsx` | `SheetMock`, `TextCard`, `Camera` |
| S03–S05, S07 | `scenes/Board.tsx` (one component, props pick the beat) | `CloseBoard`, `Tick`, `Camera`, `PrototypeLabel`, `TextCard` |
| S06 | `scenes/Checklist.tsx` | `ClientChecklist`, `PrototypeLabel`, `TextCard` |
| S08 | `scenes/Proof.tsx` | `TextCard` |
| S09 | `scenes/EndCard.tsx` | `Tick`, wordmark `[NEED]` |
| All | `Launch.tsx` | `Captions` (burned into 1:1 and 9:16), VO and music `<Audio>` once files exist |

Key excerpts:

#### `src/tokens.ts`

```ts
import {Easing} from 'remotion';

export const FPS = 30;
export const sec = (s: number) => Math.round(s * FPS);
export const clamp = {extrapolateLeft: 'clamp', extrapolateRight: 'clamp'} as const;

export const color = {
  paper: '#F6F3EA',
  ink: '#1B2420',
  pencil: '#59625C',
  rule: '#C5D3C2',
  tick: '#A3341F',
  reconciled: '#2D5C4C',
} as const;

export const ease = {
  enter: Easing.bezier(0.16, 1, 0.3, 1),
  move: Easing.bezier(0.65, 0, 0.35, 1),
};

export const springs = {
  settle: {damping: 200},
  crisp: {damping: 26, stiffness: 170, mass: 1},
  pop: {damping: 18, stiffness: 180, mass: 1},
};

export const dur = {enter: 18, tick: 9, stagger: 3, camera: 27} as const;

export type Format = 'landscape' | 'vertical' | 'square';
export const formatOf = (w: number, h: number): Format => (h > w ? 'vertical' : w === h ? 'square' : 'landscape');

export const typeScale: Record<Format, {display: number; headline: number; title: number; body: number; caption: number; min: number}> = {
  landscape: {display: 112, headline: 80, title: 56, body: 40, caption: 44, min: 32},
  vertical: {display: 112, headline: 84, title: 64, body: 48, caption: 56, min: 40},
  square: {display: 104, headline: 80, title: 60, body: 44, caption: 48, min: 36},
};

export const safe: Record<Format, {top: number; right: number; bottom: number; left: number}> = {
  landscape: {top: 54, right: 96, bottom: 54, left: 96},
  vertical: {top: 250, right: 140, bottom: 350, left: 64},
  square: {top: 64, right: 64, bottom: 64, left: 64},
};
```

#### `src/fonts.ts`

```ts
import {loadFont as loadCaslon} from '@remotion/google-fonts/LibreCaslonDisplay';
import {loadFont as loadPlex} from '@remotion/google-fonts/IBMPlexSans';
import {loadFont as loadMono} from '@remotion/google-fonts/IBMPlexMono';

const caslon = loadCaslon('normal', {weights: ['400'], subsets: ['latin']});
const plex = loadPlex('normal', {weights: ['400', '600'], subsets: ['latin']});
const mono = loadMono('normal', {weights: ['400'], subsets: ['latin']});

export const fonts = {display: caslon.fontFamily, text: plex.fontFamily, mono: mono.fontFamily};
```

#### `src/timing.ts`

```ts
import {sec} from './tokens';

export type Scene = {id: string; frames: number; text: string | null; textIn: number};

// The storyboard table as data. textIn = local frame where the card is fully legible.
export const SCENES: Scene[] = [
  {id: 'S01-hook', frames: sec(3), text: 'Which client is blocked?', textIn: 0},
  {id: 'S02-problem', frames: sec(6), text: 'Close, in a spreadsheet', textIn: 24},
  {id: 'S03-turn', frames: sec(3), text: 'A close board', textIn: 18},
  {id: 'S04-board', frames: sec(8), text: '1 row per client. 1 column per step.', textIn: 18},
  {id: 'S05-blocked', frames: sec(9), text: 'Blocked: waiting on client', textIn: 60},
  {id: 'S06-reconciled', frames: sec(8), text: "See what's already reconciled", textIn: 30},
  {id: 'S07-summary', frames: sec(7), text: '5 ready. 1 blocked.', textIn: 36},
  {id: 'S08-proof', frames: sec(4), text: 'Built by a former firm ops lead', textIn: 12},
  {id: 'S09-cta', frames: sec(4), text: 'Join the waitlist', textIn: 12},
];

export const TOTAL_FRAMES = SCENES.reduce((n, s) => n + s.frames, 0); // 1560 = 52.0s

export const holdFrames = (text: string) => 45 + 9 * text.trim().split(/\s+/).length;

// Fails loudly in the Studio if a retime breaks the reading rule.
for (const s of SCENES) {
  if (s.text && s.textIn + holdFrames(s.text) > s.frames) {
    throw new Error(`${s.id}: "${s.text}" needs ${s.textIn + holdFrames(s.text)} frames, scene has ${s.frames}`);
  }
}

// Cuts on beats: beat n sits at round(n * 1800 / bpm) frames after the music's first downbeat.
export const beatFrame = (n: number, bpm: number) => Math.round((n * 1800) / bpm);
```

#### `src/components/Camera.tsx`

```tsx
import React from 'react';
import {AbsoluteFill, interpolate, useCurrentFrame} from 'remotion';
import {clamp, dur, ease} from '../tokens';

// One move per scene: from scale `from` to `to` starting at `start`, origin on the target's centre.
export const Camera: React.FC<{
  start: number;
  from: number;
  to: number;
  origin: string;
  dimOthers?: boolean;
  children: React.ReactNode;
}> = ({start, from, to, origin, dimOthers = false, children}) => {
  const frame = useCurrentFrame();
  const progress = interpolate(frame, [start, start + dur.camera], [0, 1], {...clamp, easing: ease.move});
  const scale = interpolate(progress, [0, 1], [from, to]);
  return (
    <AbsoluteFill style={{transform: `scale(${scale})`, transformOrigin: origin}}>
      {children}
      {dimOthers ? <AbsoluteFill style={{backgroundColor: 'rgba(246, 243, 234, 0.6)', opacity: progress, pointerEvents: 'none'}} /> : null}
    </AbsoluteFill>
  );
};
```

In `Board.tsx`, the focused row renders above the dim layer (a second copy of the row inside the `Camera`, after the overlay), so only C-04 stays at full contrast.

#### `src/components/Tick.tsx`

```tsx
import React from 'react';
import {interpolate, spring, useCurrentFrame, useVideoConfig} from 'remotion';
import {clamp, color, dur, springs} from '../tokens';

// The signature motion: a pencil tick that draws itself. Never fades in.
export const Tick: React.FC<{start: number; size: number; emphasis?: boolean}> = ({start, size, emphasis = false}) => {
  const frame = useCurrentFrame();
  const {fps} = useVideoConfig();
  const LENGTH = 40; // path length of the tick below, in viewBox units
  const draw = emphasis
    ? spring({frame, fps, delay: start, config: springs.pop})
    : interpolate(frame, [start, start + dur.tick], [0, 1], clamp);
  return (
    <svg width={size} height={size} viewBox="0 0 32 32" aria-hidden>
      <path
        d="M5 17 L13 25 L28 7"
        fill="none"
        stroke={emphasis ? color.tick : color.ink}
        strokeWidth={3.5}
        strokeLinecap="round"
        strokeLinejoin="round"
        strokeDasharray={LENGTH}
        strokeDashoffset={LENGTH * (1 - Math.min(draw, 1))}
      />
    </svg>
  );
};
```

The pop spring overshoots past 1; the `Math.min` keeps the stroke from over-drawing, and the overshoot shows instead as a 4% scale on the end-card tick's wrapper.

Excerpt from `src/Launch.tsx` (scene components not shown):

```tsx
<Series>
  {SCENES.map((s) => (
    <Series.Sequence key={s.id} durationInFrames={s.frames} name={s.id}>
      <SceneFor id={s.id} />
    </Series.Sequence>
  ))}
</Series>
{/* [NEED: VO recording] <Audio src={staticFile('audio/vo.wav')} /> */}
{/* [NEED: licensed music] <Audio src={staticFile('audio/music.mp3')} volume={music} /> */}
{burnCaptions ? <Captions cues={CUES} /> : null}
```

## Renders and deliverables

```powershell
npx remotion render src/index.ts Launch-16x9 out/ledgerline-launch-16x9-v1.mp4 --codec=h264 --crf=18 --color-space=bt709
npx remotion render src/index.ts Launch-1x1 out/ledgerline-launch-1x1-v1.mp4 --codec=h264 --crf=18 --color-space=bt709
npx remotion render src/index.ts Cut30-9x16 out/ledgerline-cut27-9x16-v1.mp4 --codec=h264 --crf=18 --color-space=bt709
npx remotion render src/index.ts Hero-loop out/hero-master.mp4 --codec=h264 --crf=16 --color-space=bt709 --muted
npx remotion still src/index.ts Hero-loop out/hero-poster.png --frame=150
ffmpeg -i out/hero-master.mp4 -an -vf "scale=1600:-2:flags=lanczos" -c:v libx264 -preset slow -crf 26 -maxrate 2.5M -bufsize 5M -pix_fmt yuv420p -movflags +faststart deliver/hero.mp4
ffmpeg -i out/hero-master.mp4 -an -vf "scale=1600:-2:flags=lanczos" -c:v libvpx-vp9 -crf 36 -b:v 0 -row-mt 1 deliver/hero.webm
ffmpeg -hide_banner -i out/ledgerline-launch-16x9-v1.mp4 -vn -af ebur128=peak=true -f null NUL
```

| File | Aspect | Resolution | Duration | Codec | Budget | Captions | Goes to |
| --- | --- | --- | --- | --- | --- | --- | --- |
| `ledgerline-launch-16x9-v1.mp4` | 16:9 | 1920x1080 | 52.0s | H.264 CRF 18, AAC | quality first | `.vtt` + `.srt` | Landing page `how-it-works`, YouTube |
| `ledgerline-launch-1x1-v1.mp4` | 1:1 | 1080x1080 | 52.0s | H.264 | quality first | burned in + `.srt` | LinkedIn feed |
| `ledgerline-cut27-9x16-v1.mp4` | 9:16 | 1080x1920 | 27.0s | H.264 | quality first | burned in, inside safe zones | Shorts, Reels |
| `hero.mp4` / `hero.webm` | 16:9 | 1600x900 | 8.0s loop | H.264 / VP9 | 3MB each | none (board reads without words); "Concept. Sample data." label | `website-design` hero |
| `hero-poster.jpg` | 16:9 | 1600x900 | still | JPEG | under 150KB | n/a | Poster and reduced-motion state |

Loudness target: -14 LUFS integrated, -1 dBTP true peak (common target, verify current). Not measurable until the VO and music exist.

## Self-check

Scored on the scratch-timed build (no VO or music yet).

| # | Criterion | Score | Evidence |
| --- | --- | --- | --- |
| 1 | Legibility | 2 | Nothing under 32px at 16:9 or 40px at 9:16; every text pair 5.69:1 or higher; captions on 88% ink backing |
| 2 | One message per scene | 2 | Each card states one idea; S05 dims the board so only C-04 competes for attention |
| 3 | Brand consistency | 1 | All values from tokens; wordmark is still type-set text until `[NEED: wordmark SVG]` arrives |
| 4 | Motion purpose | 2 | One camera move per scene, one overshoot (S09), no template tells; 3D logo request declined with a reason |
| 5 | Timing and readability | 2 | All 9 cards pass 45 + 9 x words (guard in `timing.ts`); densest VO 2.3 words/s |
| 6 | Audio sync | 1 | Cuts sit on 120 BPM beats, but VO and music are not recorded; text-to-VO offsets unverified |
| 7 | Accessibility | 2 | Captions on every cut, no flashing (max 1 state change per cell), hero loop has poster, reduced-motion and pause handling specified |
| 8 | File size and format | 2 | Specs table met; hero budget set at 3MB with the encode recipe; files probed for yuv420p and 30fps after render |
| 9 | Truthfulness | 2 | Sample data only, "Prototype. Sample data." on every board frame, pilot claim flagged for confirmation, no invented metrics or logos |
| 10 | Muted read | 2 | On-screen text alone carries problem, product, proof, and CTA |

Total 18/20. Gates: truthfulness 2 (pass), no 0 on legibility or accessibility (pass). Verdict: ready for founder review as a scratch cut; not publishable until criteria 3 and 6 reach 2.

## Open items
- [NEED: VO recording of the 94-word script, or approval to record a founder scratch on a phone]
- [NEED: licensed music track; 120 BPM keeps every cut on a beat, otherwise re-snap with `beatFrame()`]
- [NEED: wordmark SVG for S09]
- [NEED: founder approves the S08 VO edit; confirm the pilots have started on record day]
- [ASSUMPTION: only the 2 founders work on the Remotion project, so the Free License applies]
- [ASSUMPTION: the video lives on the landing page, LinkedIn, and YouTube]

## Next step
Founder answers the contractor question and records the VO by 2026-10-27. I then lock the timing to the real VO (scenes shift by at most a beat each), drop in music, render v2 of all four deliverables, and re-score criteria 3 and 6.

Logged to `.foundora/journal.md`:

```markdown
### 2026-10-20 — decision: Launch video built in Remotion, 52s, no 3D logo open
- 52s 16:9 master + 1:1 + 27s 9:16 cut + 8s hero loop; Remotion Free License assumed (2 founders, no contractors), confirm before render
- Declined the 3D logo spin: hook shows the close spreadsheet; signature motion is a drawn tick, end card on paper (tick-red on ink is 2.32:1)
- Board is a labelled prototype with sample data until pilot UI exists; self-check 18/20 on scratch timing
- Revisit 2026-10-27 when the VO is recorded: retime to VO, add music, re-score audio sync and brand
- Source: motion-video
```
