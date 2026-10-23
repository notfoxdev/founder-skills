# Typography

Read this when choosing fonts, building the type scale, or fixing a page that "looks off" without an obvious reason. Type does most of the work on a marketing page. Get it right and the page needs very little decoration.

## Pairing principles

1. **Contrast on one axis, harmony on the others.** Pair faces that differ clearly in one way (serif vs sans, condensed vs wide, geometric vs humanist) and agree on others (x-height, stroke contrast, overall proportion). Two similar-but-different sans serifs look like a mistake.
2. **One characterful face, one quiet face.** The display face carries personality. The text face disappears. If both shout, neither is heard.
3. **Two families maximum, plus an optional mono.** A superfamily (Source Serif 4 + Source Sans 3, IBM Plex Sans + Plex Mono) is a safe, coherent choice.
4. **One family can be enough.** A good variable sans with a strong display cut, using weight and size for hierarchy, often beats a forced pairing.
5. **Choose from the brief, not from habit.** Write one sentence: "Display face X because the customer's world is Y." If you cannot, you are picking by default.
6. **Spend the display face sparingly.** Use it for the h1, section headlines, and the signature moment. Do not set buttons, nav, or captions in it unless it is also the text face.
7. **Test at real sizes with real copy.** A face that looks great at 96px can be unreadable at 14px. Check the longest headline and a dense paragraph.
8. **Check the details before committing:** tabular and lining numerals (pricing, stats), italic quality, language/character support for the market, weights available, and licence for web use.

## Roles

| Role | Typical use | Face |
| --- | --- | --- |
| Display | h1, signature moment | Display face |
| Headline | Section h2 | Display face (or text face, heavy) |
| Title | h3, card and feature titles | Text face, medium/semibold |
| Body | Paragraphs, list items | Text face, regular |
| Body large | Hero subhead, lead paragraphs | Text face, regular |
| Caption / label | Metadata, form labels, footnotes | Text face, or mono for technical products |
| Mono | Code, CLI commands, data | Mono face |

## Modular scales

Pick the ratio from the page's character:

| Ratio | Name | Use |
| --- | --- | --- |
| 1.200 | Minor third | Dense product UI, docs, dashboards |
| 1.250 | Major third | Default for SaaS marketing pages |
| 1.333 | Perfect fourth | Editorial, brand-led, confident pages |
| 1.500+ | Perfect fifth and up | Posters, one-screen launches, big display moments |

Common practice: a tighter ratio on mobile (1.2) and a wider one on desktop (1.25–1.333), so display type does not overflow small screens.

### Computed steps (base 16px)

| Step | 1.200 | 1.250 | 1.333 |
| --- | --- | --- | --- |
| -1 | 13.3 | 12.8 | 12.0 |
| 0 | 16 | 16 | 16 |
| 1 | 19.2 | 20 | 21.3 |
| 2 | 23.0 | 25 | 28.4 |
| 3 | 27.6 | 31.3 | 37.9 |
| 4 | 33.2 | 39.1 | 50.5 |
| 5 | 39.8 | 48.8 | 67.3 |
| 6 | 47.8 | 61.0 | 89.8 |
| 7 | 57.3 | 76.3 | 119.7 |

Round to whole pixels (or to the nearest 2px at display sizes). For a marketing page, body at 17–18px on desktop reads better than 16px; recompute from that base if you use it.

### Default token table (major third, adapt to the brief)

| Token | Mobile size / LH | Desktop size / LH | Tracking | Weight |
| --- | --- | --- | --- | --- |
| `display` | 40 / 1.05 | 76 / 1.0 | -0.025em | 500–700 |
| `headline` | 31 / 1.12 | 49 / 1.08 | -0.02em | 500–700 |
| `title` | 20 / 1.3 | 25 / 1.25 | -0.01em | 600 |
| `body-lg` | 18 / 1.55 | 20 / 1.5 | 0 | 400 |
| `body` | 16 / 1.6 | 17–18 / 1.6 | 0 | 400 |
| `caption` | 13 / 1.45 | 13–14 / 1.45 | 0.01em | 400–500 |
| `label-caps` (if used) | 12 / 1.3 | 12–13 / 1.3 | 0.06–0.08em | 500–600 |

Fluid display size example: `font-size: clamp(2.5rem, 1.6rem + 4.5vw, 4.75rem);` gives about 42px at 375px wide and caps at 76px. Check both ends.

## Tracking and line-height rules

- **Display (40px+):** tighten, -0.02em to -0.035em. Large type set at default tracking looks loose and amateur. Heavier weights and wide faces need more tightening; condensed faces need less.
- **Headlines (24–40px):** -0.01em to -0.02em.
- **Body (14–20px):** 0. Do not tighten body text. Most text faces are spaced for this range.
- **Small text (under 14px):** 0 to +0.01em.
- **All caps and small caps:** always add +0.04em to +0.1em. Caps set tight are hard to read. Use caps for short labels only, never for sentences, and not above every heading.
- **Line-height falls as size rises:** display 1.0–1.1, headline 1.08–1.2, title 1.25–1.35, body 1.5–1.7, caption 1.4–1.5. Long measures need taller leading; short measures can go tighter.
- **Measure:** body 60–75ch, ideal about 65ch. Hero subheads 40–55ch. Captions can run shorter.
- **Paragraph spacing:** about 0.75–1em between paragraphs; do not indent and space at once.

## Details that separate polished from generic

- `text-wrap: balance` on headlines, `text-wrap: pretty` on paragraphs to avoid widows.
- `font-variant-numeric: tabular-nums` on prices, tables, counters, and anything that updates.
- Real quotes and apostrophes (’ “ ”), real multiplication sign (×), en dashes for ranges (9–5).
- Hanging punctuation on large pull quotes (`hanging-punctuation: first` where supported, or a negative text-indent).
- Optical sizing on variable fonts that support it (`font-optical-sizing: auto`), e.g. Fraunces, Newsreader, Literata.
- Weight steps that are visibly different (400 vs 600, not 400 vs 500) when weight alone signals hierarchy.
- Underlines on body links with `text-underline-offset: 0.2em` and `text-decoration-thickness: 1px` (or `from-font`).

## Font sources

- **Google Fonts** (fonts.google.com): open licences (mostly SIL OFL). Self-host via `next/font/google` or Fontsource for performance and privacy rather than hot-linking.
- **Fontshare** (fontshare.com, by Indian Type Foundry): free for personal and commercial use under the ITF Free Font License. Download and self-host. Confirm the licence for the specific family.
- **Fontsource** (fontsource.org): npm packages of open fonts for self-hosting, pin the version.
- **Velvetyne, Collletttivo, The League of Moveable Type:** open-source display faces with character. Check each licence.
- **Paid/commercial foundries** (Klim, Grilli Type, Commercial Type, Pangram Pangram, Displaay, etc.): often the most distinctive. Some offer free trial or personal-use files that are not licensed for production websites. Never ship a trial font. Tell the founder the cost.

## Curated shortlist by personality

Starting points, not rules. Verify availability and licence before use. Overused defaults (Inter, Roboto, Poppins, Montserrat, DM Sans, Plus Jakarta Sans, Space Grotesk) are allowed only with a stated reason. Libraries change; confirm each family still exists at its source before naming it in a plan.

| Personality | Fits | Display | Text | Mono |
| --- | --- | --- | --- | --- |
| Editorial, considered | Research, legal, finance, media, B2B with a point of view | Newsreader, Fraunces, Source Serif 4, Instrument Serif (GF); Gambetta, Erode, Zodiak (FS) | Public Sans, Instrument Sans, Source Sans 3 (GF); Switzer (FS) | IBM Plex Mono |
| Precise, technical | Dev tools, infra, data, security | Geist, Schibsted Grotesk, IBM Plex Sans, Archivo (GF); Supreme (FS) | Geist, IBM Plex Sans, Hanken Grotesk (GF) | Geist Mono, JetBrains Mono, Martian Mono, Fragment Mono |
| Warm, human | Health, education, care, community, consumer services | Young Serif, Bricolage Grotesque, Literata (GF); Erode, Sentient (FS) | Figtree, Instrument Sans, Onest (GF); Satoshi, General Sans (FS) | Spline Sans Mono |
| Confident, loud | Consumer brands, creator tools, events, fintech for young users | Bricolage Grotesque (wide, heavy), Unbounded, Big Shoulders Display, Anton (GF); Clash Display, Cabinet Grotesk, Tanker (FS) | Manrope, Hanken Grotesk (GF); Satoshi, General Sans (FS) | JetBrains Mono |
| Refined, premium | Luxury, hospitality, high-ticket services, architecture | Instrument Serif, Cormorant Garamond, Bodoni Moda (GF); Boska, Zodiak (FS) | Inter Tight, Manrope (GF); Switzer, General Sans (FS) | none |
| Playful, light | Kids, games, hobby, social | Chillax, Pally (FS); Syne, Fredoka (GF) | Nunito Sans, Figtree (GF) | Recursive Mono |
| Accessibility-first | Public sector, older or low-vision audiences, health | Atkinson Hyperlegible (GF) | Atkinson Hyperlegible, Lexend (GF) | Atkinson Hyperlegible Mono (GF, if available) |

GF = Google Fonts, FS = Fontshare.

Example pairings with reasoning (write one like this in the plan):

- **Newsreader + Public Sans:** a compliance product for community banks. Newsreader's newspaper heritage signals seriousness; Public Sans was designed for government interfaces and stays neutral at small sizes.
- **Geist + Geist Mono:** a CLI-first developer tool. One system, the mono carries commands in the hero, no decorative face needed.
- **Clash Display + Satoshi:** a consumer fitness app with a loud brand. Clash's tight, high-contrast grotesque carries the hero; Satoshi's geometric calm handles body text.
- **Fraunces (soft, high optical size) + Instrument Sans:** a children's learning product aimed at parents. Fraunces' soft serifs read warm without going cartoonish.

## File budget

- At most 4 font files total (for example display 600, text 400, text 600, mono 400). Variable fonts count as one file per axis set.
- Subset to the languages you ship (`latin` usually).
- Preload only the files used above the fold (usually display weight and body regular).
- Use `size-adjust` / `ascent-override` fallbacks (`next/font` does this automatically) to prevent layout shift when the web font swaps in.
