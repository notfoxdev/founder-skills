# Remotion guide

Read this when the tool decision in SKILL.md step 4 lands on Remotion, or when Remotion does not fit and you need the license-free path at the end. Facts marked "verify current" change between releases; check the linked docs before relying on them.

## Facts checked at the time of writing (verify current)

| Fact | Value | Source |
| --- | --- | --- |
| Current major version | 4.x (npm `remotion` 4.0.538). 5.0 is announced but not released | npm registry; remotion.dev/docs/5-0-migration |
| Free License | Individuals; for-profit organisations with up to 3 employees; non-profits; evaluation before commercial use | github.com/remotion-dev/remotion/blob/main/LICENSE.md |
| Company License | Required for companies of 4+ people. "Remotion for Creators" is priced per seat, "Remotion for Automators" per render | remotion.dev/docs/license/pricing |
| 5.0 license change | Contractors also count towards team size; an agency's and its client's headcount aggregate if both operate the same project | remotion.dev/docs/5-0-migration, remotion.dev/docs/license/faq |
| Scaffold | `npx create-video@latest` (wizard) or `npx create-video@latest --yes --blank my-video` | remotion.dev/docs |
| Studio | `npx remotion studio` (templates alias it as `npm run dev`) | remotion.dev/docs |
| Render | `npx remotion render <entry> <composition-id> <output>` | remotion.dev/docs/cli/render |
| Still | `npx remotion still <entry> <composition-id> <output> --frame=<n>` | remotion.dev/docs/cli/still |
| Bundled ffmpeg | `npx remotion ffmpeg ...` (H.264, H.265, VP8, VP9, ProRes only) | remotion.dev/docs/cli/ffmpeg |
| Audio/video components | `<Audio>` / `<Video>` from `@remotion/media` are now recommended; `<Html5Audio>` (formerly `<Audio>`) and `<OffthreadVideo>` remain in `remotion` | remotion.dev/docs/media/audio, remotion.dev/docs/offthreadvideo |

## License check (do this before scaffolding)

Ask one question if `company.md` does not answer it: "How many people, including contractors, will work on or run this video project, and is it for a for-profit company?"

| Situation | Outcome |
| --- | --- |
| Solo founder, or a for-profit company of 3 or fewer people (count contractors to be safe; 5.0 does) | Free License. Note it in the brief and the journal |
| 4+ people, founder willing to pay | Company License. Founder buys it at remotion.pro; never buy or sign up on their behalf |
| 4+ people, founder will not pay | Use the license-free path below |
| The founder wants videos generated inside their own product for users | Not this skill's default job. Flag "Remotion for Automators" pricing and stop for a decision |
| Unsure (agency, client project, contractor-heavy) | Point to remotion.dev/docs/license/faq and let the founder decide. Do not interpret the license for them |

This is a summary of public terms, not legal advice. The founder confirms fit.

## Setup

```powershell
npx create-video@latest --yes --blank launch-video
cd launch-video
npx remotion add @remotion/google-fonts @remotion/media @remotion/transitions
npx remotion studio
```

`npx remotion add` installs packages at the same version as the installed `remotion`, which avoids version mismatch errors. Remotion also publishes its own agent skills (`npx remotion skills add`); they help with API detail, while this skill owns design, timing, and delivery.

Add `out/` and any raw recordings to `.gitignore` before the first render.

## Project structure

```
launch-video/
  public/
    brand/        logo.svg, wordmark.svg (from the founder, never redrawn)
    ui/           real screenshots at 2x, screen recordings
    audio/        vo.wav, music.mp3 (licensed), sfx/
  src/
    index.ts      registerRoot
    Root.tsx      one <Composition> per aspect ratio
    tokens.ts     palette, type scale, spacing, easing, springs, durations, safe zones
    fonts.ts      font loading (render waits for fonts)
    timing.ts     the storyboard as data: one entry per scene, frames at 30fps
    captions.ts   caption cues in ms (or parsed from .srt)
    components/   Captions, TextCard, Camera, Cursor, PrototypeLabel, EndCard
    scenes/       one file per scene, S01Hook.tsx, S02Problem.tsx ...
    Launch.tsx    the master: <Series> of scenes + audio + captions
  remotion.config.ts
```

Rule: scenes never hard-code a hex value, font size, or duration. Everything comes from `tokens.ts` and `timing.ts`, so a 9:16 cut or a retime is a data change.

## Minimal complete example (3 scenes, 16:9 and 9:16)

Placeholder brand values; replace with the brand's tokens from SKILL.md step 6.

### `src/index.ts`

```ts
import {registerRoot} from 'remotion';
import {RemotionRoot} from './Root';

registerRoot(RemotionRoot);
```

### `src/tokens.ts`

```ts
import {Easing} from 'remotion';

export const FPS = 30;
export const sec = (s: number) => Math.round(s * FPS);
export const clamp = {extrapolateLeft: 'clamp', extrapolateRight: 'clamp'} as const;

// Palette: placeholders. Use the brand's named hex values; check text contrast >= 4.5:1.
export const color = {
  paper: '#F4F2EC',
  ink: '#1B1A17',
  muted: '#5C5A52',
  line: '#D9D5C9',
  accent: '#B8430F',
} as const;

export const ease = {
  standard: Easing.bezier(0.2, 0, 0, 1), // UI changes, small moves
  enter: Easing.bezier(0.16, 1, 0.3, 1), // entrances: fast out, long settle
  exit: Easing.bezier(0.4, 0, 1, 1), // exits: accelerate away
  move: Easing.bezier(0.65, 0, 0.35, 1), // on-screen to on-screen, camera moves
};

// Damping ratio = damping / (2 * sqrt(stiffness * mass)). See motion-principles.md.
export const springs = {
  settle: {damping: 200}, // overdamped, no overshoot; always pass durationInFrames
  crisp: {damping: 26, stiffness: 170, mass: 1}, // ~critically damped, no visible overshoot
  pop: {damping: 18, stiffness: 180, mass: 1}, // ~6% overshoot; one element per video
};

// Durations in frames at 30fps
export const dur = {micro: 6, enter: 18, exit: 12, transition: 12, camera: 27, stagger: 3} as const;

export type Format = 'landscape' | 'vertical' | 'square';
export const formatOf = (width: number, height: number): Format =>
  height > width ? 'vertical' : width === height ? 'square' : 'landscape';

// px at 1920x1080 / 1080x1920 / 1080x1080. Nothing renders below `min`.
export const typeScale: Record<Format, {display: number; headline: number; title: number; body: number; caption: number; min: number}> = {
  landscape: {display: 112, headline: 80, title: 56, body: 40, caption: 44, min: 32},
  vertical: {display: 112, headline: 84, title: 64, body: 48, caption: 56, min: 40},
  square: {display: 104, headline: 80, title: 60, body: 44, caption: 48, min: 36},
};

export const space = (n: number) => n * 8; // 8px grid

// Text-safe insets. Vertical values keep text clear of platform UI (approximate; verify current overlays).
export const safe: Record<Format, {top: number; right: number; bottom: number; left: number}> = {
  landscape: {top: 54, right: 96, bottom: 54, left: 96},
  vertical: {top: 250, right: 140, bottom: 350, left: 64},
  square: {top: 64, right: 64, bottom: 64, left: 64},
};
```

### `src/fonts.ts`

```ts
import {loadFont as loadText} from '@remotion/google-fonts/IBMPlexSans';
import {loadFont as loadMono} from '@remotion/google-fonts/IBMPlexMono';

// Always pass weights and subsets: fewer requests, no render timeouts, and required from 5.0.
const text = loadText('normal', {weights: ['400', '600'], subsets: ['latin']});
const mono = loadMono('normal', {weights: ['400'], subsets: ['latin']});

export const fonts = {text: text.fontFamily, mono: mono.fontFamily};
```

For brand fonts that are not on Google Fonts, put the licensed file in `public/fonts/` and use `loadFont({family, url: staticFile('fonts/Brand.woff2')})` from `@remotion/fonts`.

### `src/timing.ts`

```ts
import {sec} from './tokens';

// The storyboard as data. Change timings here, never inside scenes.
export const SCENES = {
  hook: {id: 'S01-hook', frames: sec(3)}, // 90
  product: {id: 'S02-product', frames: sec(6)}, // 180
  cta: {id: 'S03-cta', frames: sec(3)}, // 90
} as const;

export const TOTAL_FRAMES = Object.values(SCENES).reduce((sum, s) => sum + s.frames, 0); // 360

// Reading rule: text needs 1.5s + 0.3s per word on screen = 45 + 9 * words frames.
export const holdFrames = (text: string) => 45 + 9 * text.trim().split(/\s+/).length;
```

### `src/components/Captions.tsx`

```tsx
import React from 'react';
import {AbsoluteFill, useCurrentFrame, useVideoConfig} from 'remotion';
import {color, formatOf, safe, typeScale} from '../tokens';
import {fonts} from '../fonts';

// Same shape as the Caption type from @remotion/captions, so parseSrt() output works too.
export type Cue = {text: string; startMs: number; endMs: number};

export const Captions: React.FC<{cues: Cue[]}> = ({cues}) => {
  const frame = useCurrentFrame();
  const {fps, width, height} = useVideoConfig();
  const ms = (frame / fps) * 1000;
  const cue = cues.find((c) => ms >= c.startMs && ms < c.endMs);
  if (!cue) return null;

  const f = formatOf(width, height);
  const inset = safe[f];
  return (
    <AbsoluteFill
      style={{
        justifyContent: 'flex-end',
        alignItems: 'center',
        paddingBottom: inset.bottom + 16,
        paddingLeft: inset.left,
        paddingRight: inset.right,
      }}
    >
      <div
        style={{
          maxWidth: f === 'vertical' ? 860 : 1400, // keeps lines near 32-42 characters
          padding: '10px 20px',
          borderRadius: 6,
          backgroundColor: 'rgba(27, 26, 23, 0.86)', // ink backing: text contrast holds on any frame
          color: color.paper,
          fontFamily: fonts.text,
          fontWeight: 600,
          fontSize: typeScale[f].caption,
          lineHeight: 1.25,
          textAlign: 'center',
        }}
      >
        {cue.text}
      </div>
    </AbsoluteFill>
  );
};
```

### `src/scenes/Hook.tsx`

```tsx
import React from 'react';
import {AbsoluteFill, interpolate, spring, useCurrentFrame, useVideoConfig} from 'remotion';
import {color, dur, formatOf, safe, springs, typeScale} from '../tokens';
import {fonts} from '../fonts';

export const Hook: React.FC<{line: string}> = ({line}) => {
  const frame = useCurrentFrame(); // local to this Series.Sequence: starts at 0
  const {fps, width, height} = useVideoConfig();
  const f = formatOf(width, height);
  const inset = safe[f];

  const enter = spring({frame, fps, config: springs.crisp, durationInFrames: dur.enter});
  const y = interpolate(enter, [0, 1], [40, 0]);

  return (
    <AbsoluteFill
      style={{
        backgroundColor: color.paper,
        justifyContent: 'center',
        padding: `${inset.top}px ${inset.right}px ${inset.bottom}px ${inset.left}px`,
      }}
    >
      <h1
        style={{
          margin: 0,
          maxWidth: '14ch',
          fontFamily: fonts.text,
          fontWeight: 600,
          fontSize: typeScale[f].display,
          lineHeight: 1.05,
          letterSpacing: '-0.02em',
          color: color.ink,
          opacity: enter,
          transform: `translateY(${y}px)`,
        }}
      >
        {line}
      </h1>
    </AbsoluteFill>
  );
};
```

### `src/scenes/Product.tsx`

Recreated UI with sample data, a staggered fill, then one camera move to the detail that matters.

```tsx
import React from 'react';
import {AbsoluteFill, interpolate, spring, useCurrentFrame, useVideoConfig} from 'remotion';
import {clamp, color, dur, ease, formatOf, springs, typeScale} from '../tokens';
import {fonts} from '../fonts';

const ROWS = ['Item A', 'Item B', 'Item C', 'Item D'];
const COLS = ['Step 1', 'Step 2', 'Step 3'];
const FOCUS = {row: 2, col: 1}; // the one cell this scene is about
const FILL_START = 8;
const CAMERA_START = 90;

export const Product: React.FC = () => {
  const frame = useCurrentFrame();
  const {fps, width, height} = useVideoConfig();
  const t = typeScale[formatOf(width, height)];

  // One camera move: hold wide (readable), then push to 1.6x on the focus cell.
  const zoom = interpolate(frame, [CAMERA_START, CAMERA_START + dur.camera], [1, 1.6], {...clamp, easing: ease.move});

  return (
    <AbsoluteFill style={{backgroundColor: color.paper, justifyContent: 'center', alignItems: 'center'}}>
      <div style={{transform: `scale(${zoom})`, transformOrigin: '62% 66%' /* set to the focus cell's centre, checked in Studio */}}>
        <div style={{display: 'grid', gridTemplateColumns: `260px repeat(${COLS.length}, 200px)`, fontFamily: fonts.text, fontSize: t.body, color: color.ink}}>
          <div />
          {COLS.map((c) => (
            <div key={c} style={{fontFamily: fonts.mono, fontSize: t.min, color: color.muted, padding: 12}}>{c}</div>
          ))}
          {ROWS.map((r, ri) => (
            <React.Fragment key={r}>
              <div style={{padding: 12, borderTop: `2px solid ${color.line}`}}>{r}</div>
              {COLS.map((c, ci) => {
                const isFocus = ri === FOCUS.row && ci === FOCUS.col;
                const start = FILL_START + (ri * COLS.length + ci) * dur.stagger;
                const s = spring({frame, fps, delay: start, config: isFocus ? springs.pop : springs.crisp});
                return (
                  <div key={c} style={{padding: 12, borderTop: `2px solid ${color.line}`}}>
                    <span
                      style={{
                        display: 'inline-block',
                        opacity: s,
                        transform: `scale(${interpolate(s, [0, 1], [0.6, 1])})`,
                        color: isFocus ? color.accent : color.ink,
                        fontWeight: isFocus ? 600 : 400,
                      }}
                    >
                      {isFocus ? 'Blocked' : '✓'}
                    </span>
                  </div>
                );
              })}
            </React.Fragment>
          ))}
        </div>
      </div>
    </AbsoluteFill>
  );
};
```

### `src/scenes/Cta.tsx`

```tsx
import React from 'react';
import {AbsoluteFill, interpolate, spring, useCurrentFrame, useVideoConfig} from 'remotion';
import {color, dur, formatOf, springs, typeScale} from '../tokens';
import {fonts} from '../fonts';

export const Cta: React.FC<{action: string; url: string}> = ({action, url}) => {
  const frame = useCurrentFrame();
  const {fps, width, height} = useVideoConfig();
  const t = typeScale[formatOf(width, height)];
  const a = spring({frame, fps, config: springs.settle, durationInFrames: dur.enter});
  const b = spring({frame, fps, delay: 6, config: springs.settle, durationInFrames: dur.enter}); // 6-frame follow

  return (
    <AbsoluteFill style={{backgroundColor: color.ink, justifyContent: 'center', alignItems: 'center', gap: 24}}>
      <div style={{fontFamily: fonts.text, fontWeight: 600, fontSize: t.headline, color: color.paper, opacity: a, transform: `translateY(${interpolate(a, [0, 1], [24, 0])}px)`}}>
        {action}
      </div>
      <div style={{fontFamily: fonts.mono, fontSize: t.title, color: color.paper, opacity: b}}>{url}</div>
    </AbsoluteFill>
  );
};
```

### `src/Launch.tsx`

```tsx
import React from 'react';
import {AbsoluteFill, Series, interpolate, staticFile, useCurrentFrame} from 'remotion';
import {Audio} from '@remotion/media';
import {clamp, color} from './tokens';
import {SCENES, TOTAL_FRAMES} from './timing';
import {Hook} from './scenes/Hook';
import {Product} from './scenes/Product';
import {Cta} from './scenes/Cta';
import {Captions, type Cue} from './components/Captions';

const CUES: Cue[] = [
  {text: 'Which item is stuck?', startMs: 200, endMs: 2800},
  {text: 'Every step, one board.', startMs: 3200, endMs: 6000},
  {text: 'The blocked one shows itself.', startMs: 6200, endMs: 8800},
  {text: 'Join the waitlist.', startMs: 9300, endMs: 11800},
];

export const Launch: React.FC = () => {
  const frame = useCurrentFrame();
  // Music: fade in, sit low under VO, fade out over the last 30 frames. Set by ear: music ~15-20 dB under VO.
  const music = interpolate(frame, [0, 15, TOTAL_FRAMES - 30, TOTAL_FRAMES], [0, 0.25, 0.25, 0], clamp);

  return (
    <AbsoluteFill style={{backgroundColor: color.paper}}>
      <Series>
        <Series.Sequence durationInFrames={SCENES.hook.frames} name={SCENES.hook.id}>
          <Hook line="Which item is stuck?" />
        </Series.Sequence>
        <Series.Sequence durationInFrames={SCENES.product.frames} name={SCENES.product.id}>
          <Product />
        </Series.Sequence>
        <Series.Sequence durationInFrames={SCENES.cta.frames} name={SCENES.cta.id}>
          <Cta action="Join the waitlist" url="example.com" />
        </Series.Sequence>
      </Series>
      <Audio src={staticFile('audio/vo.wav')} />
      <Audio src={staticFile('audio/music.mp3')} volume={music} />
      <Captions cues={CUES} />
    </AbsoluteFill>
  );
};
```

Remove the two `<Audio>` lines until the files exist in `public/audio/`; a missing file fails a video render, even with `--muted` (a still renders with a 404 warning).

### `src/Root.tsx`

```tsx
import React from 'react';
import {Composition} from 'remotion';
import {Launch} from './Launch';
import {FPS} from './tokens';
import {TOTAL_FRAMES} from './timing';

export const RemotionRoot: React.FC = () => (
  <>
    <Composition id="Launch-16x9" component={Launch} durationInFrames={TOTAL_FRAMES} fps={FPS} width={1920} height={1080} />
    <Composition id="Launch-9x16" component={Launch} durationInFrames={TOTAL_FRAMES} fps={FPS} width={1080} height={1920} />
    <Composition id="Launch-1x1" component={Launch} durationInFrames={TOTAL_FRAMES} fps={FPS} width={1080} height={1080} />
  </>
);
```

Each scene reads `formatOf(width, height)` and re-lays itself out. A 9:16 version is a re-layout, never a crop or letterbox of the 16:9 frame.

## Render commands

```powershell
# Preview
npx remotion studio

# Masters (H.264, CRF 18 is visually near-lossless; platforms re-encode anyway).
# --color-space=bt709 gives limited-range yuv420p tagged BT.709; without it 4.0.538 wrote full-range yuvj420p.
npx remotion render src/index.ts Launch-16x9 out/launch-16x9.mp4 --codec=h264 --crf=18 --color-space=bt709
npx remotion render src/index.ts Launch-9x16 out/launch-9x16.mp4 --codec=h264 --crf=18 --color-space=bt709
npx remotion render src/index.ts Launch-1x1 out/launch-1x1.mp4 --codec=h264 --crf=18 --color-space=bt709

# One scene only, for review (frames are inclusive)
npx remotion render src/index.ts Launch-16x9 out/s02.mp4 --frames=90-269

# Contact sheet: one PNG per scene midpoint
npx remotion render src/index.ts Launch-16x9 out/check --frames=45,180,315 --image-format=png

# Poster frame
npx remotion still src/index.ts Launch-16x9 out/poster.png --frame=150

# Silent master for a hero loop or for muted social
npx remotion render src/index.ts Launch-16x9 out/launch-silent.mp4 --muted --color-space=bt709
```

On Windows, inline `--props='{...}'` JSON breaks because the shell strips quotes; pass a file path instead (`--props=props.json`). Encoding the deliverables from these masters is in `references/delivery.md`.

## Transitions

Default to hard cuts on a beat. When a scene needs a crossfade or a push, use `<TransitionSeries>` from `@remotion/transitions`:

```tsx
import {TransitionSeries, linearTiming} from '@remotion/transitions';
import {fade} from '@remotion/transitions/fade';

<TransitionSeries>
  <TransitionSeries.Sequence durationInFrames={90}><Hook line="..." /></TransitionSeries.Sequence>
  <TransitionSeries.Transition presentation={fade()} timing={linearTiming({durationInFrames: 12})} />
  <TransitionSeries.Sequence durationInFrames={180}><Product /></TransitionSeries.Sequence>
</TransitionSeries>
```

A transition overlaps the two scenes, so the total is the sum of scenes minus each transition (90 + 180 - 12 = 258). Recompute the storyboard frames when you add one.

## Common pitfalls

- **Animating with CSS transitions, CSS keyframes, `setTimeout`, or `Math.random()`.** Renders are frame-by-frame in parallel; anything not derived from `useCurrentFrame()` flickers or drifts. Use `interpolate`, `spring`, and `random('seed')` from `remotion`.
- **Unclamped `interpolate`.** It extrapolates past the input range by default: an opacity of 1.4 or a scale running away. Pass `extrapolateLeft/Right: 'clamp'` unless you want that.
- **Frame offsets.** `useCurrentFrame()` inside a `<Sequence>` or `<Series.Sequence>` is local (starts at 0). Do not subtract the scene start again.
- **Non-integer durations.** `durationInFrames` must be an integer. Convert seconds with `Math.round(s * fps)` once, in `timing.ts`.
- **Plain `<img>` or CSS `background-image`.** The renderer may capture a frame before the image loads. Use `<Img src={staticFile(...)}>` from `remotion`, which delays the frame until loaded.
- **Fonts not loaded.** Load through `@remotion/google-fonts` or `@remotion/fonts`, which block the render until ready. A system-font fallback in one frame is a visible flash.
- **Video sources.** Use `<Video>` from `@remotion/media` (or `<OffthreadVideo>`) for screen recordings; record at constant frame rate; re-encode variable frame rate recordings first (see delivery.md).
- **Zooming a screenshot past its resolution.** A 1x screenshot zoomed 1.6x is soft. Capture at 2x and never zoom past the capture scale.
- **Composition ids.** Letters, numbers, and hyphens only. `defaultProps` must be JSON-serializable; type props with `type`, not `interface`.
- **Slow renders.** See SKILL.md Edge cases. Biggest wins: fewer `filter: blur()` and large `box-shadow` layers, pre-sized images, `--concurrency`, and rendering only changed scenes with `--frames`.
- **Upgrading to 5.0 later (verify current).** Planned: a license key in render APIs and config (`"free-license"` for Free License users), `loadFont()` requiring weights and subsets, a 2-second default premount in the Player, and contractors counting towards headcount. Read the migration guide before upgrading a live project.

## When Remotion does not fit: license-free path

Use plain HTML/CSS/SVG animated with CSS keyframes or the Web Animations API, captured frame by frame with Playwright (Apache-2.0), then encoded with ffmpeg. It suits hero loops, teasers, and kinetic-type clips up to about 30s. Audio is mixed in ffmpeg afterwards.

Setup (pin versions; tell the founder what you installed):

```powershell
npm i -D playwright@1.64.1
npx playwright install chromium
```

Author the animation in `loop/index.html` with every animation starting at page load (use `animation-delay` for sequencing) and fonts loaded via `@font-face`. Then capture deterministically: pause every animation and seek it to the exact frame time, so no frame depends on how fast the machine is.

```js
// capture.mjs  ->  node capture.mjs
import {chromium} from 'playwright';
import {mkdir} from 'node:fs/promises';
import {pathToFileURL} from 'node:url';

const FPS = 30;
const SECONDS = 8;
const [W, H] = [1920, 1080];

await mkdir('frames', {recursive: true});
const browser = await chromium.launch();
const page = await browser.newPage({viewport: {width: W, height: H}, deviceScaleFactor: 1});
await page.goto(pathToFileURL('loop/index.html').href);
await page.evaluate(() => document.fonts.ready);

for (let f = 0; f < FPS * SECONDS; f++) {
  const ms = (f * 1000) / FPS;
  await page.evaluate((t) => {
    for (const a of document.getAnimations()) {
      a.pause();
      a.currentTime = t; // includes animation-delay, so sequenced keyframes line up
    }
    window.renderFrame?.(t); // optional hook if any motion is JS-driven
  }, ms);
  await page.screenshot({path: `frames/f_${String(f).padStart(5, '0')}.png`});
}
await browser.close();
```

```powershell
ffmpeg -framerate 30 -i frames/f_%05d.png -c:v libx264 -crf 18 -preset slow -pix_fmt yuv420p -movflags +faststart out/loop-master.mp4
```

Do not use Playwright's built-in video recording for deliverables: it records in real time, so frame timing depends on machine load.

Other option: Motion Canvas (MIT, TypeScript generators with an editor, good for vector explainers synced to VO). Its last npm release at the time of writing was 3.17.2 in December 2024; verify current maintenance before choosing it for a project that must ship.
