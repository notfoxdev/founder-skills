# Colour and motion

Read this when building the palette, checking contrast, or deciding what moves.

## Building the palette

1. **Start from the material world in the brief.** Pull colour from the customer's environment: the manila of a case file, the safety orange of a warehouse, the green-grey of a hospital corridor, the ink blue of a ledger. A colour with a reason is never generic.
2. **Neutrals first.** Most of the page is paper and ink. Pick them before the accent.
   - Paper: rarely pure `#FFFFFF`. A slightly warm or cool off-white sets the mood (`#FAF8F4` warm, `#F6F8F9` cool).
   - Ink: rarely pure `#000000`. A near-black tinted toward the accent hue (`#16130F`, `#0E1621`).
   - Tint neutrals toward one hue. Grey that is mathematically neutral looks dead next to a coloured accent.
3. **One accent.** It marks the primary action and the signature moment. If it appears everywhere, it marks nothing.
4. **Support colours only with a job:** `muted` (secondary text), `line` (borders, dividers), `signal` (success/error/warning, used in UI states only).
5. **Proportion:** roughly 70–80% paper, 15–25% ink and muted, under 10% accent.
6. **Name every colour** by what it is in the brief, not by hue number: `ledger`, `manila`, `signal-red`. Names keep the system coherent when someone adds a colour later.

## Palette skeleton (4–6 colours)

| Name | Role | Rule |
| --- | --- | --- |
| `paper` | Page background | Off-white or deliberate dark |
| `ink` | Headlines and body | 4.5:1 or more on `paper`, ideally 12:1+ |
| `muted` | Secondary text, captions | 4.5:1 on `paper`. Many "muted greys" fail; check |
| `line` | Borders, dividers | 1.3–1.6:1 for decoration; 3:1 if it is the only cue for a control |
| `accent` | Primary CTA fill, signature moment, links if dark enough | Button text on accent at 4.5:1 |
| `signal` (optional) | Errors, success | Never the only indicator; pair with icon or text |

Illustrative starting points (adapt; do not copy as-is):

| Brief | paper | ink | muted | line | accent |
| --- | --- | --- | --- | --- | --- |
| Logistics ops tool | `#F4F2EC` | `#1B1A17` | `#5C5A52` | `#D9D5C9` | `#E2541B` (safety orange) |
| Clinical scheduling | `#F5F8F7` | `#10201D` | `#4E5F5B` | `#D3DEDB` | `#1F6F5C` (surgical green) |
| Developer CLI | `#0F1113` | `#ECEEF0` | `#9AA1A8` | `#2A2F34` | `#C6F432` (terminal highlight) |
| Children's reading | `#FFF8EE` | `#2A1E16` | `#6B5A4C` | `#EBDCC7` | `#D9432B` (crayon red) |

## Contrast

WCAG 2.x AA thresholds:

- Body text (under 24px regular or 18.66px bold): **4.5:1**.
- Large text (24px+ regular, or 18.66px+ bold): **3:1**.
- UI components and meaningful graphics (input borders, focus rings, icons that convey meaning): **3:1** against adjacent colours.
- Placeholder text, disabled states: aim for 4.5:1 anyway if the text carries information.

Compute, do not guess. Drop this into a scratch script or the browser console:

```js
// Returns WCAG contrast ratio between two hex colours, e.g. contrast('#5C5A52', '#F4F2EC')
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

Record every text/background pair and its ratio in the design plan. If the brand accent fails 4.5:1 with white text, try ink text on the accent, darken the accent for text uses (keep a lighter tint for fills), or reserve it for large type.

## Gradients, texture, and imagery

- Gradients are allowed when they come from the subject (dawn sky for a sleep app, heat map for an energy tool) and stay subtle (two adjacent hues, small lightness shift). Purple-to-blue washes, mesh-gradient blobs, and gradient text are banned by default.
- Grain/noise overlays: at most 3–5% opacity, on one surface, and check they do not band or slow rendering.
- Photography: one consistent treatment (colour grade, crop style). Real over stock. Duotone or monochrome can unify mixed-quality images.
- Illustration: one style, one stroke weight, from one source. Mixing illustration packs is a tell.

## Dark mode

- Not required for a marketing page. Do it only if the audience expects it (developers) or the brand is dark-first.
- Not an inversion. Background around `#0E0F11`–`#16181B`, not `#000`. Raise elevated surfaces by lightness, not shadow.
- Desaturate and lighten the accent slightly so it does not vibrate.
- Re-check every contrast pair; muted text usually fails first.
- If supporting both, drive with `prefers-color-scheme` plus tokens; never hard-code colours in components.

## Motion

Motion is for feedback, orientation, and one moment of emphasis. Not for decoration.

| Purpose | Example | Duration | Easing |
| --- | --- | --- | --- |
| Feedback | Button hover/press, toggle | 100–150ms | `ease-out` |
| UI change | Menu open, accordion, tab switch | 180–250ms | `cubic-bezier(0.2, 0, 0, 1)` |
| Entrance (rare) | Signature element on first view | 400–700ms | `cubic-bezier(0.16, 1, 0.3, 1)` |
| Exit | Closing panels | 70–80% of the entrance time | `cubic-bezier(0.4, 0, 1, 1)` |

Rules:

- Animate only `transform` and `opacity` (and `clip-path` sparingly). Never animate layout properties (`width`, `height`, `top`) on scroll.
- One scroll-triggered effect per page at most, on the signature moment. No fade-up on every section.
- No scroll-jacking, no parallax on body content, no autoplaying carousels.
- Looping media (hero demo clips): muted, under 12s, with a visible pause control if it runs longer than 5 seconds (WCAG 2.2.2).
- Nothing flashes more than 3 times per second (WCAG 2.3.1).
- Movement distances small: 8–24px for entrances. Large travel reads as gimmick.

Reduced motion is required:

```css
:root {
  --ease-standard: cubic-bezier(0.2, 0, 0, 1);
  --ease-emphasized: cubic-bezier(0.16, 1, 0.3, 1);
  --dur-fast: 120ms;
  --dur-base: 220ms;
  --dur-slow: 560ms;
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

For the signature moment, design the reduced-motion version on purpose (final state shown immediately, or a cross-fade under 200ms) rather than relying only on the global override. Pause or replace autoplaying video with its poster image under reduced motion.
