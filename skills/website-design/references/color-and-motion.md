# Colour and motion

Read this when building the palette, checking contrast, deciding on dark mode, or deciding what moves. All ratios in this file were computed with the script below.

## Building the palette from the subject

1. **Start from the material world in the brief.** Pull colour from the customer's environment: the manila of a case file, the safety orange of a warehouse, the green-grey of a clinic corridor, the ink blue of a ledger. Write the source next to each colour. A colour with a reason is never generic.
2. **Neutrals first.** Most of the page is paper and ink. Pick them before the accent.
   - Paper: rarely pure `#FFFFFF`. A slightly warm or cool off-white sets the mood.
   - Ink: rarely pure `#000000`. A near-black tinted toward the accent hue or the material.
   - Tint every neutral toward one hue. Mathematically neutral grey looks dead next to a coloured accent.
3. **One accent.** See the one-accent rule below.
4. **Support colours only with a job:** `muted` (secondary text), `line` (decorative rules), `boundary` (input borders and control outlines), `signal` (success, error, warning in UI states only).
5. **Proportion:** roughly 70 to 80% paper, 15 to 25% ink and muted, under 10% accent.
6. **Name every colour** by what it is in the brief, not by hue number: `ledger`, `manila`, `signal-red`. Names keep the system coherent when someone adds a colour later.

## Neutral ramps

Build an 11-step ramp in OKLCH: fix the hue, keep chroma low (about 0.005 to 0.012), and step lightness. Convert to hex for the tokens, then compute contrast. Two ready ramps, tinted warm (hue 75) and cool (hue 250):

| Step | Warm hex | vs warm 50 | vs `#FFFFFF` | Cool hex | vs cool 50 | vs `#FFFFFF` | Typical role |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 50 | `#F9F6F3` | 1.00 | 1.08 | `#F3F7FC` | 1.00 | 1.08 | Paper |
| 100 | `#F2F0EC` | 1.06 | 1.14 | `#EDF1F5` | 1.06 | 1.14 | Surface (cards, table rows) |
| 200 | `#E6E2DC` | 1.20 | 1.29 | `#DDE4EB` | 1.19 | 1.28 | Line (decorative dividers) |
| 300 | `#D6D2CC` | 1.40 | 1.51 | `#CDD3DA` | 1.40 | 1.51 | Line, stronger |
| 400 | `#ABA7A2` | 2.22 | 2.39 | `#A2A8AF` | 2.23 | 2.40 | Disabled fills only, never text |
| 500 | `#898580` | 3.40 | 3.66 | `#81878D` | 3.38 | 3.63 | Boundary (input borders, 3:1+), large text only |
| 600 | `#6F6B66` | 4.91 | 5.29 | `#676C73` | 4.92 | 5.29 | Muted text (lightest step allowed for body-size text) |
| 700 | `#585550` | 6.89 | 7.42 | `#50565C` | 6.91 | 7.43 | Secondary text, safe on surface too |
| 800 | `#433F3B` | 9.69 | 10.43 | `#3B4046` | 9.72 | 10.46 | Body text on tinted bands |
| 900 | `#2C2824` | 13.58 | 14.62 | `#25292F` | 13.59 | 14.61 | Body text |
| 950 | `#1B1814` | 16.43 | 17.69 | `#14191E` | 16.44 | 17.68 | Ink, headlines, focus ring |

Muted 600 on surface 100 is 4.65:1 (warm) and 4.66:1 (cool): it passes, with little margin. On any darker surface, move muted to 700. Retune the hue to the brief (a green-black ledger ink, a blue-grey clinic) and recompute; never reuse these hex values without checking.

## The one-accent rule

- One accent hue per page. It marks, in this order: the primary CTA, the signature moment, and optionally links and the focus ring if they pass contrast. Nothing else.
- Under 10% of the surface at any viewport. If it appears in every section, it marks nothing.
- The accent may have states (hover, pressed) and a text-safe shade. Those are tokens of the same hue, not new colours.
- `signal` colours (error red, success green) are not accents. They appear only in UI states and never as decoration. If the accent is red, make the error colour visibly different or rely on icon and text.
- A second accent needs a written reason (for example, a two-sided marketplace where each side has a colour). Default answer: no.

Deriving the accent:

1. Pick the hue from the material world.
2. Decide its jobs: CTA fill, text/link, large display only.
3. For a CTA fill, compute the label colour on it. Paper or white text needs 4.5:1; if the hue is light (yellow, lime, orange), use ink for the label instead.
4. For text or links on paper, it needs 4.5:1. If the brand hue fails, derive a darker text-safe shade of the same hue and keep the original for fills and large type only.
5. Record every ratio in the plan.

Illustrative palettes (computed; adapt, never copy as-is):

| Brief | paper | ink | muted (on paper) | line | accent | Accent check |
| --- | --- | --- | --- | --- | --- | --- |
| Logistics ops tool | `#F4F2EC` | `#1B1A17` (15.55) | `#5C5A52` (6.17) | `#D9D5C9` (1.31) | `#E2541B` safety orange | Paper text on it 3.40, fails; ink label on it 4.57, passes. As text on paper 3.40: large type only, or use `#B23A1F` (5.33) for links |
| Clinical scheduling | `#F5F8F7` | `#10201D` (15.77) | `#4E5F5B` (6.32) | `#D3DEDB` (1.29) | `#1F6F5C` surgical green | White label 6.02; as text on paper 5.64. Passes both |
| Developer CLI (dark) | `#0F1113` | `#ECEEF0` (16.27) | `#9AA1A8` (7.24) | `#2A2F34` (1.40) | `#C6F432` terminal highlight | Dark label (`#0F1113`) on it 14.76; light text on it 1.10, never |
| Children's reading | `#FFF8EE` | `#2A1E16` (15.37) | `#6B5A4C` (6.24) | `#EBDCC7` (1.28) | `#D9432B` crayon red | As text on paper 4.16, fails; white label 4.39, fails. Ink label on it 3.70, also fails. Use the shade `#B5371F` for links (5.64 on paper) and for CTA fills (white label 5.95); keep crayon red for large illustration only |

## Contrast

WCAG 2.2 Level AA thresholds:

| What | Ratio | Criterion |
| --- | --- | --- |
| Body text (under 24px regular, under 18.66px bold) | 4.5:1 | 1.4.3 Contrast (Minimum) |
| Large text (24px+ regular, or 18.66px+ bold; 18pt / 14pt bold) | 3:1 | 1.4.3 |
| UI component boundaries and states, meaningful graphics (input borders, focus indicators, chart lines, icons that carry meaning) | 3:1 against adjacent colours | 1.4.11 Non-text Contrast |
| Enhanced (optional) | 7:1 body, 4.5:1 large | 1.4.6 (AAA) |

- Logos and purely decorative elements are exempt. Disabled controls are exempt, but information text is not; aim for 4.5:1 on placeholder text that carries meaning.
- Do not round up: 4.47:1 fails 4.5:1, and so does 4.497:1 displayed as "4.50".
- Colour alone never conveys information (1.4.1 Use of Color): pair errors, required fields, and highlights with text or shape.

The math: relative luminance L = 0.2126 R + 0.7152 G + 0.0722 B on linearised sRGB channels (c ≤ 0.04045 ? c / 12.92 : ((c + 0.055) / 1.055)^2.4). Ratio = (L_lighter + 0.05) / (L_darker + 0.05). Older WCAG text uses 0.03928 as the threshold; for 8-bit hex colours both give identical results.

Compute, do not guess. Run in a scratch script or the browser console:

```js
// WCAG 2.x contrast ratio between two hex colours.
// contrast('#6F6B66', '#F9F6F3').toFixed(2) -> "4.91"; passes(…, 4.5) compares the unrounded value.
function contrast(a, b) {
  const lum = (hex) => {
    const [r, g, bl] = hex.replace('#', '').match(/.{2}/g).map((h) => {
      const c = parseInt(h, 16) / 255;
      return c <= 0.04045 ? c / 12.92 : ((c + 0.055) / 1.055) ** 2.4;
    });
    return 0.2126 * r + 0.7152 * g + 0.0722 * bl;
  };
  const [hi, lo] = [lum(a), lum(b)].sort((x, y) => y - x);
  return (hi + 0.05) / (lo + 0.05);
}
const passes = (fg, bg, threshold) => contrast(fg, bg) >= threshold;
```

Ratios in this skill are shown rounded to two decimals; pass or fail is always decided on the unrounded value.

Contrast audit procedure: list every text/background pair actually used (including text on accent, text on tinted bands, placeholder text, captions on images, focus ring against both paper and accent), compute each, and record it in the plan's palette table. Any pair below its threshold is a Blocker.

## Gradients, texture, and imagery

- Gradients only when they come from the subject (dawn sky for a sleep app, heat map for an energy tool) and stay subtle: two adjacent hues, a small lightness shift. Purple-to-blue washes, mesh blobs, and gradient text are T1 to T3 in `anti-generic.md`.
- Hard-stop patterns drawn from the material (ledger rules, graph paper, a route grid) are texture, not gradient washes. Keep them under the content's contrast and on one or two surfaces.
- Grain or noise: at most 3 to 5% opacity on one surface; check it does not band or slow rendering.
- Photography: one consistent treatment (colour grade, crop style). Real over stock. Duotone or monochrome can unify mixed-quality images.
- Illustration: one style, one stroke weight, from one source.

## Dark mode: only if justified

Ship light only unless one of these is true; write which one in the plan:

1. The audience works in dark environments or dark tools all day (developers, security operators, video editors).
2. The product UI is dark, and light-page screenshots would glare.
3. The brand is dark-first (existing assets confirm it).

If justified:

- Not an inversion. Background around `#0E0F11` to `#16181B`, not `#000`. Raise elevated surfaces by lightness, not shadow.
- Desaturate and lighten the accent slightly so it does not vibrate on dark.
- Recompute every pair; muted text usually fails first.
- Supporting both: drive with `prefers-color-scheme` and tokens, set `color-scheme: light dark`, never hard-code colours in components.

## Motion

Motion is for feedback, orientation, and one moment of emphasis. Not decoration. Default to almost nothing.

| Purpose | Example | Duration | Easing |
| --- | --- | --- | --- |
| Feedback | Button hover and press, link underline, toggle | 150ms | `cubic-bezier(0.25, 1, 0.5, 1)` (ease-out quart) |
| Small UI change | Tooltip, focus ring, tab underline | 150 to 200ms | `cubic-bezier(0.2, 0, 0, 1)` |
| Disclosure | Accordion, mobile menu, dropdown | 200 to 300ms | `cubic-bezier(0.2, 0, 0, 1)` |
| Large UI change | Drawer, dialog, panel | 300 to 400ms | `cubic-bezier(0.22, 1, 0.36, 1)` (ease-out quint) |
| Exit | Closing anything | About 70% of the enter time | `cubic-bezier(0.5, 0, 0.75, 0)` (ease-in quart) |
| Hero or signature sequence | The one choreographed moment | 600 to 1200ms total; each element 240 to 600ms; stagger 60 to 120ms | `cubic-bezier(0.16, 1, 0.3, 1)` (ease-out expo) |

Rules:

- Ease-out for anything entering or responding to the user; ease-in only for exits; linear only for progress bars and continuous loops. No bounce or elastic easing on B2B pages.
- UI responses never exceed 400ms. Only the signature sequence runs longer, and it runs once.
- Travel distances small: 8 to 24px for entrances. Scale from 0.96 to 1, not from 0.
- One scroll-triggered effect per page at most, on the signature moment, triggered once at 25 to 40% visibility. No fade-up on every section (T15).
- Never fade or slide in the hero h1 or the LCP image. Elements at `opacity: 0` are not counted for LCP until they appear, so entrance animations on the hero delay LCP.
- Content must be visible without JavaScript: render the final state in HTML and CSS, then enhance. Do not set `opacity: 0` in CSS and rely on a script to reveal it.
- No scroll-jacking, no parallax on body content, no autoplaying carousels.
- Moving or looping media that starts automatically and lasts more than 5 seconds needs a pause control (WCAG 2.2.2 Pause, Stop, Hide). Hero loops: muted, under 12 seconds.
- Nothing flashes more than 3 times per second (WCAG 2.3.1).

### Scroll-driven reveals

Use `IntersectionObserver` (or CSS scroll-driven animations as progressive enhancement behind `@supports (animation-timeline: view())`, since browser support is still incomplete). Never a `scroll` event listener that reads layout on every frame.

```js
// Runs the signature sequence once, when 35% of it is visible. Final state is the default CSS.
const el = document.querySelector('[data-signature]');
if (el && !matchMedia('(prefers-reduced-motion: reduce)').matches) {
  el.classList.add('is-armed'); // moves elements to their start state only when JS and motion are available
  new IntersectionObserver(([entry], obs) => {
    if (entry.isIntersecting) { el.classList.add('is-playing'); obs.disconnect(); }
  }, { threshold: 0.35 }).observe(el);
}
```

### Performance budget for motion

- Animate only `transform` and `opacity`. These can run on the compositor without layout or paint. Do not animate `width`, `height`, `top`, `left`, `margin`, `padding`, or `font-size`; do not animate `box-shadow` or `filter: blur()` on large areas. `clip-path` sparingly, on small elements.
- `will-change` only on the element about to animate, removed after; never on `*`.
- No layout reads (`offsetHeight`, `getBoundingClientRect`) inside animation frames.
- Effects code: no animation library unless the founder agrees. Pack budget: under about 10KB of JavaScript for all page effects, or none.
- Page targets (Core Web Vitals "good", measured at the 75th percentile of real visits): LCP at or under 2.5s, INP at or under 200ms, CLS at or under 0.1. Lab tools (Lighthouse) only estimate these; say which you measured.

### Tokens and reduced motion

```css
:root {
  --ease-out: cubic-bezier(0.25, 1, 0.5, 1);
  --ease-standard: cubic-bezier(0.2, 0, 0, 1);
  --ease-emphasized: cubic-bezier(0.16, 1, 0.3, 1);
  --ease-in: cubic-bezier(0.5, 0, 0.75, 0);
  --dur-fast: 150ms;
  --dur-base: 240ms;
  --dur-slow: 400ms;
  --dur-hero: 900ms; /* total budget for the signature sequence */
}

@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
```

Design the signature moment's reduced-motion version on purpose (final state shown immediately, or a cross-fade under 200ms) rather than relying only on the global override. Replace autoplaying video with its poster image under reduced motion.
