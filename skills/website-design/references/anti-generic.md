# Anti-generic system

Read this when writing the design plan (step 4), self-reviewing it (step 5), auditing an existing page, or when the founder says "it looks like every AI startup". It holds the full catalogue of AI-default tells, the icon rules, how to derive a signature moment, and how to translate vague taste words into decisions.

Every tell has an ID (T1 to T22). Use the IDs in `Revisions after self-review` and in the critique so the founder can see exactly what was removed and why.

## Why pages look "vibe coded"

Generated pages converge on the same output because every choice is left at its default: default font, default palette of the UI kit, default radius, default shadow, default section order, an icon because the card had an empty slot. No single default is wrong. The sum reads as "nobody decided anything". The cure is not decoration. It is making each of those choices on purpose, from the brief, and writing down why.

Rule: for every visual property in the plan (font, colour, radius, shadow, icon, motion, section order) you must be able to name the brief item it came from. "Looks modern" is not a reason.

## The tells

| ID | Tell | Why it reads as default | Do instead | Survives only if |
| --- | --- | --- | --- | --- |
| T1 | Purple, violet, indigo, or purple-to-blue gradient washes on backgrounds, buttons, borders | The most common default palette of generated UI and dark SaaS templates | Take the accent from the material world (manila, safety orange, ledger green). Flat fills. One accent | The brand already owns the colour (existing logo, founder-confirmed) |
| T2 | Gradient or animated gradient text (`bg-clip-text text-transparent`, shimmer) | Decoration standing in for hierarchy; often fails contrast at one end | Solid ink headline. Emphasis by weight, size, italic, or one word in the accent with 3:1+ contrast at that size | Never on body text; on display text only if both gradient ends pass contrast and it ties to the subject |
| T3 | Gradient blob, aurora, mesh, or glowing orb behind a centred hero | Fills empty space with nothing; says "tech" about every subject | Put the hero artifact there: real product crop, code that runs, the signature object | Never as the main hero visual |
| T4 | Centred-everything: centred headline, centred paragraphs, centred cards | No alignment axis, so nothing anchors the eye; long centred text is hard to read | One left axis held down the page. Centre only short symmetric content (final CTA, one stat) | A one-screen page with under 25 words of text |
| T5 | Glassmorphism: frosted `backdrop-blur` panels, translucent cards on colour | Trend default; low contrast over busy backgrounds; costs paint time | Opaque surfaces, 1px `line` borders, or a shift of one neutral step | The product UI itself uses it and you are showing that UI |
| T6 | A row of three identical feature cards, each with a line icon in a tinted circle, a title, two lines | The single most recognisable template block | Alternating text/media rows, one annotated product crop, a numbered list with large numerals, or a comparison table (see `layout-and-components.md`) | Never with icon-in-circle; three cards only if the content genuinely has three parallel items of equal weight |
| T7 | Emoji or an icon on every card, bullet, or list item | Icons used as filler; every item gets one so none means anything | No icon by default. Use numerals, short bold lead-ins, or real UI crops. See Icon discipline below | The icon carries information the text does not (status, platform, file type) |
| T8 | Inter, Roboto, Poppins, or one neutral sans for everything, with sizes close together and weights 400/500 only | No typographic voice and no hierarchy | A pairing chosen from the brief, a real scale with a visible jump between levels (ratio 1.2 to 1.333), weights 400 vs 600+ | A stated reason (existing brand, product UI uses it) and the hierarchy still comes from a real scale |
| T9 | One large radius on everything (`rounded-2xl`, `rounded-3xl`, 24px) | Kit default; makes buttons, inputs, images, and cards feel like the same soft blob | Pick from 0, 2, 4, 8, full. At most two values per page. Sharp corners often suit serious B2B subjects | The material world is soft (children, care) and the radius is still a named token |
| T10 | A drop shadow on every element, or `shadow-xl` cards floating on white | Depth with no meaning; muddy on off-white paper | Flat by default. Separate with whitespace or a 1px rule. At most two shadow levels, ink-tinted, for things that really float (menus, popovers) | The element truly sits above the page |
| T11 | Invented social proof: "Trusted by" logo strips, testimonials from unnamed or AI-generated people, avatar stacks ("Join 2,000+ founders") | Dishonest, and visitors recognise the pattern | Real proof with permission and a source, a true stage statement ("2 firms piloting from October"), or a visible `[NEED: proof]` | It is real, permitted, and sourced |
| T12 | Lorem or placeholder metrics ("10x faster", "99.9% uptime", "500+ teams", "4.9 stars") | Numbers with no source teach visitors to distrust the page | Only founder-provided or calculated numbers with source and date; otherwise `[NEED: ...]` | Never invented |
| T13 | A pill badge above the h1 ("New: AI-powered ...") with a sparkle icon | Template opener; sparkle has come to mean "generated" | Lead with the headline. Put real news in the nav or a dated line under the CTA | There is real, dated news and it is the visitor's reason to care |
| T14 | An ALL-CAPS eyebrow label above every heading | Repeated on every section it stops labelling anything | Let headings stand alone. Use caps only for real labels (table headers, stamps, metadata) | Used once or twice where it labels a category the visitor needs |
| T15 | Fade-up on scroll for every section; staggered everything | Motion as decoration; delays reading; can delay LCP | Static by default. One scroll-triggered effect at most, on the signature moment | It is the signature moment |
| T16 | An arrow on every link and button | Arrows stop meaning "goes somewhere" | Arrows on at most two key CTAs that navigate | Navigation CTAs only |
| T17 | Dark mode with neon accent as the "techy" default; dot or grid background with a radial fade | Borrowed dev-tool look on subjects that are not dev tools | Light paper unless the dark-mode test in `color-and-motion.md` passes; texture only from the material world | The dark-mode test passes |
| T18 | Fake product UI: tilted 3D dashboard mockups, browser chrome around invented screens, UI for a product that does not exist | Misleading, and visitors who try the product notice | Real screenshots cropped to the moment of value, or a concept visual labelled "Concept. Sample data." | Real UI, or labelled concept |
| T19 | The template stack "hero, logos, 3 features, testimonials, pricing, CTA" picked before looking at the content | Structure chosen by habit, so empty sections get filled with invented content | Build the section list from the content inventory (SKILL.md step 3); cut sections with nothing real in them | The content really fills every section |
| T20 | Bento grid where tiles differ in size for no reason | Varied sizes imply varied importance; when the content is equal, it is noise | Tile size follows importance, or use a list or table | Items genuinely differ in importance |
| T21 | Stock imagery, abstract 3D shapes, AI illustrations of "teams" or "growth" | Interchangeable between any two companies | Real photos, real product, diagrams of the actual workflow, typographic compositions | A real photo of the real thing |
| T22 | Generic action labels and headlines shown in the design ("Get started", "Learn more", "Supercharge your workflow") | Copy is part of the design; generic words make any layout generic | Specific verb phrases ("Book a 20-minute demo", "Join the waitlist"). Hand weak headlines to `landing-page-copy` | Never |

## Scanning code for tells

Run these over the built page (or the founder's existing repo in Audit mode). A hit is not automatically a fail; each hit needs a reason or a fix. Use `rg` if available; the PowerShell lines are equivalent.

```bash
rg -n "from-(purple|violet|indigo|fuchsia)|via-(purple|violet|indigo)|bg-(linear|gradient)-to" src app components   # T1
rg -n "bg-clip-text|text-transparent" src app components                                                       # T2
rg -n "backdrop-blur|backdrop-filter" src app components                                                      # T5
rg -n "rounded-(2xl|3xl)" src app components | wc -l                                                          # T9 count
rg -n "shadow-(md|lg|xl|2xl)" src app components | wc -l                                                      # T10 count
rg -n "from ['\"](lucide-react|@heroicons|react-icons|@tabler|@phosphor-icons)" src app components             # icon audit
rg -n "animate-(pulse|bounce|ping)|whileInView|data-aos" src app components                                   # T15
```

```powershell
Get-ChildItem -Recurse -Include *.tsx,*.jsx,*.astro,*.html,*.css src,app,components -ErrorAction SilentlyContinue |
  Select-String -Pattern 'from-(purple|violet|indigo)|bg-clip-text|backdrop-blur|rounded-(2xl|3xl)|shadow-(lg|xl|2xl)|lucide-react|whileInView'
```

Adjust folder names to the repo. Also scan rendered copy for emoji (T7) and for numbers with no source (T12).

## Icon discipline

Icons are the fastest way to make a page look generated. Default to none, and add each one only if it passes the deletion test.

**Deletion test (per icon):** delete it. If no information is lost, it stays deleted.

Icons help when they:

- Are functional UI the visitor operates: menu, close, play/pause, expand/collapse chevron, external-link, copy-to-clipboard.
- Carry status that text alone makes slow to scan: included/not included in a pricing table, pass/fail in a comparison, with a text alternative.
- Identify a known thing faster than words: platform or integration marks (with permission), file types, payment methods.
- Match icons the visitor will see in the product, so the page teaches the UI.

Icons hurt when they:

- Decorate every feature, bullet, or card (T6, T7).
- Sit in a tinted circle or rounded square as a "badge".
- Replace a heading or stand for an abstract idea (a rocket for "fast", a shield for "secure", a sparkle for "AI").
- Come from mixed sets, mixed stroke weights, or mix outline and filled styles.

When you do use icons:

- One set for the whole site (for example Lucide, Phosphor, Heroicons, Tabler, or a custom set). Check its licence; most of these are MIT or similar.
- One stroke weight. Lucide and Tabler default to a 2px stroke on a 24px grid and Heroicons outline uses 1.5px; set the weight once and do not mix. Scale the stroke with the size so it looks optically equal (for example 1.5px at 20 to 24px, 1.25px at 16px if the set supports it).
- One style: all outline or all filled. Filled only for active or selected states.
- Sizes from a scale tied to text: 16px with caption, 20px with body, 24px with titles. Align the icon centre to the first line's x-height or cap height, not the text box.
- Colour `currentColor` (ink or muted). Never the accent unless the icon is part of the primary CTA.
- Decorative icons `aria-hidden="true"`. Icon-only buttons get an `aria-label` and a 44x44px hit area. Status icons pair with text ("Included", "Blocked").
- Budget: on a typical marketing page, the decorative icon count is 0 and the total icon count stays low enough that each one is noticed. In the icon audit, list every icon and its job; any icon without a job fails.

Prefer, in this order: a number or numeral, a real product crop, a diagram drawn from the subject, a typographic device (large numerals, rules, index labels, tabular figures), a real photo. An icon comes last.

## Deriving the signature moment

The signature moment is the one place the page spends boldness. It is derived from the product's subject, never added as decoration.

1. **Pick the object.** From the brief's material world, choose the artifact that shows the problem turning into the outcome. A dispatcher's manifest that reconciles itself. A clinic week grid where double-bookings resolve. A terminal session with real output. A redlined contract where the risky clause gets flagged.
2. **Make it real.** Build it in HTML, SVG, and CSS from the product's actual data shape (a real `<table>`, a timeline, a map, a receipt), with sample data labelled as sample. Not a picture of a dashboard.
3. **Place it once.** Usually `hero` or `how-it-works`. It gets generous padding, and it is the only full-bleed element and the only scroll-triggered motion.
4. **Design its still state first.** The reduced-motion version shows the final state and must tell the whole story on its own.

Pass all five before it goes in the plan:

| Test | Question | Fail means |
| --- | --- | --- |
| Recognition | Would someone in this industry name the object with the copy hidden? | It is decoration; pick a real artifact |
| Explanation | After seeing it, can a visitor say what the product does? | It shows mood, not the product |
| Removal | If you remove it, does the page lose meaning, not just colour? | It is ornament |
| Still state | Does the reduced-motion final state tell the story? | The meaning lives in the animation; redesign |
| Swap | Would it look wrong on a competitor's page? | It is generic; make it more specific |

Not signature moments: particle fields, spinning globes, gradient orbs, 3D shapes, cursor trails, typing-effect headlines, counters that tick up to invented numbers.

## Translating taste words

Founders describe the feel in vague words. Translate them into decisions, then confirm.

| Founder says | Usually means | Decisions |
| --- | --- | --- |
| "Premium", "high-end" | Restraint and confidence | Bigger type contrast (display at step 6 or 7), fewer elements per screen, generous section padding, one material, real photography, no shadows, tight display tracking |
| "Modern" | Not dated, not cluttered | Clean grid, current type (not Inter by default), flat fills, crisp 1px rules, little motion |
| "Clean" | Less noise | Fewer left edges, fewer colours, no icons, more whitespace between groups than within |
| "Bold" | Visible point of view | One oversized element per screen, a confident display face, a saturated accent used sparingly, asymmetric splits |
| "Trustworthy" | Calm and specific | Serif or humanist display, real names and numbers with sources, plain layout, no motion gimmicks |
| "Fun", "friendly" | Warmth without childishness | Warm paper, a characterful display face, illustration in one consistent hand, slightly softer radius, still one accent |
| "Like Stripe / Linear / Apple" | The principle, not the look | Extract it: type scale discipline, density, precise motion. Apply it to this subject. Copying fails the swap test |

## Stripping a starter template

If the repo started from a UI kit or template, the defaults are the tells. Before building sections:

- Replace the kit's colour tokens, radius token, font tokens, and shadow tokens with the plan's tokens.
- Delete unused demo sections rather than filling them.
- Remove kit-wide effects (global gradients, glows, blur utilities) from the base styles.
- Keep the kit's accessible primitives (dialog, menu, disclosure) and restyle them.
