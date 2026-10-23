# Typography

Read this when choosing fonts, building the type scale, or fixing a page that "looks off" without an obvious reason. Type does most of the work on a marketing page. Get it right and the page needs very little decoration.

## Pairing principles

1. **Contrast on one axis, harmony on the others.** Pair faces that differ clearly in one way (serif vs sans, condensed vs wide, geometric vs humanist) and agree on others (x-height, stroke contrast, overall proportion). Two similar-but-different sans serifs look like a mistake.
2. **One characterful face, one quiet face.** The display face carries personality. The text face disappears. If both shout, neither is heard.
3. **Two families maximum, plus an optional mono.** A superfamily (Source Serif 4 + Source Sans 3, IBM Plex Sans + Plex Mono) is a safe, coherent choice.
4. **One family can be enough.** A good variable sans with a strong display cut, using weight and size for hierarchy, often beats a forced pairing.
5. **Choose from the brief, not from habit.** Write one sentence: "Display face X because the customer's world is Y." If you cannot, you are picking by default (T8 in `anti-generic.md`).
6. **Spend the display face sparingly.** Use it for the h1, section headlines, and the signature moment. Do not set buttons, nav, or captions in it unless it is also the text face.
7. **Test at real sizes with real copy.** A face that looks great at 96px can be unreadable at 14px. Check the longest headline at 375px and a dense paragraph at desktop.
8. **Check the details before committing:** tabular and lining numerals (pricing, stats), italic quality, character support for the market's languages, weights available, and licence for web use.

## Roles

| Role | Token | Typical use | Face |
| --- | --- | --- | --- |
| Display | `display` | Hero h1 on a marketing page, the signature moment | Display face |
| Page title | `h1` | h1 on interior pages (pricing, about, docs home) | Display face |
| Section headline | `h2` | Section h2 | Display face, or text face heavy |
| Title | `h3` | Card, step, FAQ question, feature titles | Text face, 600 |
| Lead | `body-lg` | Hero subhead, lead paragraphs | Text face, 400 |
| Body | `body` | Paragraphs, list items | Text face, 400 |
| Caption | `caption` | Metadata, form help, footnotes, image captions | Text face (or mono for technical products) |
| Label | `label` | Table headers, stamps, short caps labels | Text face or mono, caps, tracked |
| Mono | `mono` | Code, CLI commands, data cells | Mono face, tabular |

## Modular scales

Pick the ratio from the page's character:

| Ratio | Name | Use |
| --- | --- | --- |
| 1.200 | Minor third | Mobile default; dense product UI, docs |
| 1.250 | Major third | Desktop default for SaaS marketing pages |
| 1.333 | Perfect fourth | Editorial, brand-led, confident pages |
| 1.500+ | Perfect fifth and up | Posters, one-screen launches, big display moments |

Use a tighter ratio on mobile (1.2) and a wider one on desktop (1.25 to 1.333) so display type does not overflow small screens.

### Computed steps

Size at step n = base × ratio^n. Round to whole px; at 32px and above round to the nearest even px.

| Step | 16 × 1.2 (mobile) | 18 × 1.25 (desktop) | 16 × 1.25 | 17 × 1.333 |
| --- | --- | --- | --- | --- |
| -1 | 13.3 | 14.4 | 12.8 | 12.8 |
| 0 | 16 | 18 | 16 | 17 |
| 1 | 19.2 | 22.5 | 20 | 22.7 |
| 2 | 23.0 | 28.1 | 25 | 30.2 |
| 3 | 27.6 | 35.2 | 31.3 | 40.3 |
| 4 | 33.2 | 43.9 | 39.1 | 53.7 |
| 5 | 39.8 | 54.9 | 48.8 | 71.6 |
| 6 | 47.8 | 68.7 | 61.0 | 95.4 |
| 7 | 57.3 | 85.8 | 76.3 | 127.1 |

### Default type scale (adapt to the brief, then show your own computation)

Mobile: base 16, ratio 1.2. Desktop: base 18, ratio 1.25. Line-heights snap to the 4px baseline grid.

| Token | Step | Mobile size / LH | Desktop size / LH | Tracking | Weight |
| --- | --- | --- | --- | --- | --- |
| `display` | 6 | 48 / 52 | 68 / 72 | -0.03em | 500 to 700 (400 for high-contrast serifs) |
| `h1` | 5 | 40 / 44 | 54 / 60 | -0.025em | 500 to 700 |
| `h2` | 4 | 34 / 40 | 44 / 48 | -0.02em | 500 to 700 |
| `h3` | 2 | 23 / 28 | 28 / 36 | -0.01em | 600 |
| `body-lg` | 1 | 19 / 28 | 22 / 32 | 0 | 400 |
| `body` | 0 | 16 / 24 | 18 / 28 | 0 | 400 |
| `caption` | -1 | 13 / 20 | 14 / 20 | +0.01em | 400 to 500 |
| `label` (caps) | fixed | 12 / 16 | 13 / 16 | +0.06em | 500 to 600 |

Notes:

- Body on desktop at 17 to 18px reads better than 16px on a marketing page. Never under 16px on mobile (and inputs at 16px+, which prevents iOS zoom on focus).
- If the longest word of the h1 does not fit 343px (375px viewport minus 16px margins) at mobile `display`, drop one step for that page. Do not shrink the whole scale.
- Visible jump between levels: adjacent heading levels should differ by at least one scale step. `h3` sitting 2px above `body` is a flat hierarchy (T8).

### Fluid sizes

Make `display`, `h1`, and `h2` fluid between 375px and 1280px; step `h3` and body at the `md` breakpoint instead. Formula:

```
slope     = (maxPx - minPx) / (1280 - 375)
intercept = minPx - slope * 375          (convert to rem: / 16)
font-size: clamp(minRem, interceptRem + slope*100 vw, maxRem)
```

Computed for the default scale:

```css
--text-display: clamp(3rem, 2.482rem + 2.21vw, 4.25rem);     /* 48px @375 -> 68px @1280 */
--text-h1:      clamp(2.5rem, 2.137rem + 1.547vw, 3.375rem);  /* 40px -> 54px */
--text-h2:      clamp(2.125rem, 1.866rem + 1.105vw, 2.75rem); /* 34px -> 44px */
```

Keep a `rem` term in the middle value so browser text zoom still scales the size (WCAG 1.4.4 Resize Text). A pure `vw` value does not respond to text zoom. As a rule of thumb, keep max under 2.5 times min so 200% zoom still enlarges the text.

## Tracking and line-height rules

| Size | Tracking | Line-height |
| --- | --- | --- |
| Display (48px+) | -0.025em to -0.035em. Heavier weights and wide faces need more; condensed faces less | 1.0 to 1.1 |
| Headlines (24 to 47px) | -0.01em to -0.025em | 1.08 to 1.2 |
| Titles (20 to 28px) | 0 to -0.01em | 1.2 to 1.3 |
| Body (15 to 22px) | 0. Never tighten body text | 1.45 to 1.65 |
| Small (under 15px) | 0 to +0.01em | 1.4 to 1.55 |
| All caps, small caps | +0.04em to +0.1em, always | 1.2 to 1.35 |

- Large type at default tracking looks loose and amateur. Check display tracking with the real headline; optical spacing differs by face.
- Caps only for short labels, never sentences, and not above every heading (T14).
- **Measure:** body 60 to 75ch (default 65ch). Hero subhead 40 to 55ch. Headlines 12 to 20ch per line (set `max-width` in `ch` on the h1 so it breaks into 2 or 3 deliberate lines).
- **Paragraph spacing:** 0.75 to 1em between paragraphs; do not indent and space at once.

## Numbers and data

- `font-variant-numeric: tabular-nums lining-nums` on prices, tables, counters, dates, and anything that updates or aligns in columns.
- Right-align numeric columns; align decimals.
- Use the mono or a face with good tabular figures for data-heavy signature moments.
- Old-style figures (`oldstyle-nums`) only in editorial running text, never in tables.
- Use the real minus sign (−) and multiplication sign (×) in displayed math and specs.

## Details that separate polished from generic

- `text-wrap: balance` on headlines, `text-wrap: pretty` on paragraphs to avoid widows. Both are progressive enhancements.
- Real quotes and apostrophes (’ “ ”), en dashes for ranges (9–5).
- Hanging punctuation on large pull quotes (`hanging-punctuation: first` where supported, or a negative text-indent).
- Optical sizing on variable fonts that have an `opsz` axis (`font-optical-sizing: auto`), for example Fraunces, Newsreader, Literata, Bricolage Grotesque.
- Weight steps that are visibly different (400 vs 600, not 400 vs 500) when weight alone signals hierarchy.
- Underlines on body links with `text-underline-offset: 0.2em` and `text-decoration-thickness: 1px` (or `from-font`).
- Italic from the real italic file, never synthesised (`font-synthesis: none` if no italic is loaded).

## Font sources and licensing

| Source | Licence | How to use |
| --- | --- | --- |
| Google Fonts (fonts.google.com) | Mostly SIL Open Font License 1.1 (OFL), some Apache 2.0. Free for commercial use, embedding, and self-hosting; you may not sell the fonts on their own | Self-host via `next/font/google`, Fontsource, or downloaded `.woff2`. Self-hosting avoids a third-party connection (EU privacy: a 2022 Munich court ruling found hot-linking Google Fonts without consent breached GDPR) |
| Fontsource (fontsource.org) | Repackages open fonts under their original licences | npm packages for self-hosting; pin the version |
| Fontshare (fontshare.com, Indian Type Foundry) | ITF Free Font License: free for personal and commercial use | Download and self-host. Read the licence file shipped with each family |
| Velvetyne, Collletttivo, The League of Moveable Type | Mostly OFL; check each family | Open display faces with character |
| Commercial foundries (Klim, Grilli Type, Commercial Type, Pangram Pangram, Displaay, and others) | Paid web licences, often by domain or pageviews | Often the most distinctive. Trial or personal-use files are not licensed for production websites. Never ship a trial font; tell the founder the cost |
| System fonts | No licence needed | `system-ui`, `ui-serif`, `ui-monospace`. Zero download; the right choice for plain-HTML pages with a strict performance budget |

## Pairings by personality

Starting points, not rules. Verify the family still exists at its source and check the licence before naming it in a plan. Overused defaults (Inter, Roboto, Poppins, Montserrat, DM Sans, Plus Jakarta Sans, Space Grotesk) are allowed only with a stated reason. GF = Google Fonts (OFL unless noted), FS = Fontshare (ITF FFL).

| Personality | Fits | Display + Text (+ Mono) | Source | Fallback stack (display / text) | Watch out |
| --- | --- | --- | --- | --- | --- |
| Editorial, considered | Research, legal, finance, media, B2B with a point of view | Newsreader + Public Sans (+ IBM Plex Mono) | GF | `"Iowan Old Style", Charter, Georgia, serif` / `system-ui, "Segoe UI", sans-serif` | Turn on optical sizing for Newsreader |
| Editorial, warmer | Publishing, education, considered consumer | Fraunces + Instrument Sans | GF | `Georgia, serif` / `system-ui, sans-serif` | Keep Fraunces' SOFT and WONK axes low for serious subjects |
| Archival, accountable | Accounting, records, compliance, insurance | Libre Caslon Display + IBM Plex Sans (+ IBM Plex Mono) | GF | `Georgia, "Times New Roman", serif` / `system-ui, sans-serif` | Caslon Display has one weight and thin hairlines: 28px and up only |
| Precise, technical | Dev tools, infra, data, security | IBM Plex Sans + IBM Plex Mono, or Geist + Geist Mono | GF (Geist also on npm as `geist`) | `system-ui, sans-serif` / `ui-monospace, "SF Mono", Menlo, Consolas, monospace` | Geist is now common on dev-tool sites; earn distinctiveness from layout and the artifact |
| Industrial, operational | Logistics, manufacturing, field ops | Archivo (condensed widths for display) + Archivo (+ Martian Mono) | GF | `"Arial Narrow", system-ui, sans-serif` / `system-ui, sans-serif` | Use the width axis for display only; body at normal width |
| Warm, human | Health, care, community, consumer services | Bricolage Grotesque + Figtree, or Young Serif + Onest | GF | `Georgia, serif` (Young Serif) or `system-ui` / `system-ui, sans-serif` | Bricolage gets quirky at large optical sizes; test the headline |
| Confident, loud | Consumer brands, creator tools, events | Clash Display + Satoshi | FS | `"Arial Black", system-ui, sans-serif` / `system-ui, sans-serif` | Very common in templates; it must pass the swap test on composition |
| Refined, premium | Hospitality, architecture, high-ticket services | Instrument Serif + Switzer, or Cormorant Garamond + Manrope | GF / FS | `Didot, "Bodoni 72", Georgia, serif` / `system-ui, sans-serif` | Instrument Serif has one weight; Cormorant is thin under 32px |
| Playful, light | Kids, games, hobby, social | Chillax + General Sans, or Fredoka + Nunito Sans | FS / GF | `"Trebuchet MS", system-ui, sans-serif` / `system-ui, sans-serif` | Playful display only; body stays calm |
| Accessibility-first | Public sector, older or low-vision audiences | Atkinson Hyperlegible (display and text), Lexend as an alternative text face | GF (the Braille Institute's newer "Next" and "Mono" versions: check availability) | `Verdana, system-ui, sans-serif` | Hierarchy from size and weight, not face contrast |
| Zero budget | Plain HTML, strict performance | `ui-serif` display + `system-ui` text + `ui-monospace` | System | n/a | Renders differently per OS; check Windows and macOS screenshots |

Example reasoning (write one like this in the plan):

- **Newsreader + Public Sans:** a compliance product for community banks. Newsreader's newspaper heritage signals seriousness; Public Sans was designed for US government interfaces and stays neutral at small sizes.
- **IBM Plex Sans + Plex Mono:** a CLI-first developer tool. One superfamily; the mono carries real commands in the hero, so no decorative face is needed.
- **Clash Display + Satoshi:** a consumer fitness app with a loud brand. Clash's tight grotesque carries the hero; Satoshi's geometric calm handles body text.

## Font budget and loading

- At most 4 font files total (for example display 600, text 400, text 600, mono 400). A variable font file counts as one.
- Subset to the scripts you ship (`latin` usually). `next/font` and Fontsource subset for you; for downloaded fonts use `pyftsubset` (fonttools) with a `unicode-range` that matches. See `implementation.md`.
- `font-display: swap` for text; `optional` is acceptable for a display face if you prefer no swap flash over showing the brand face on slow connections.
- Preload only the 1 or 2 files used above the fold (display weight and body regular).
- Fallback metrics: match the fallback's size and vertical metrics to the web font (`size-adjust`, `ascent-override`, `descent-override`, `line-gap-override`) so the swap does not shift layout. `next/font` does this automatically; otherwise compute values with a tool such as Fontaine or Capsize.
