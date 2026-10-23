# Layout and components

Read this when building the grid, sequencing sections, choosing compositions, or building any component. Section IDs here are shared with `landing-page-copy` so copy drops into the layout without renaming.

## Shared section IDs

| ID | Job | Include when |
| --- | --- | --- |
| `hero` | Headline, subhead, primary CTA, one artifact that shows the product or outcome | Always |
| `proof` | Real evidence: logos with permission, a named quote, a sourced number, a true stage statement | Any real proof exists |
| `problem` | The situation the customer is in today, in their words | Usually |
| `how-it-works` | 3 to 4 steps or one annotated flow from first use to outcome | Always |
| `features` | Capabilities tied to outcomes, only those that matter for the decision | The product exists and has more than one capability worth explaining |
| `pricing` | Tiers, a single price, or "talk to us" with what happens next | Self-serve, or the founder wants prices public |
| `faq` | Objections answered plainly | Usually |
| `final-cta` | One repeat of the primary action with a reason to act now | Always |
| `footer` | Navigation, legal, contact | Always |

Order is a default. A pre-product waitlist might be `hero`, `problem`, `how-it-works`, `final-cta`. A dev tool might put `how-it-works` (a code sample) right after `hero`. The content inventory (SKILL.md step 3) decides which sections exist; an empty section is cut, not filled.

## The grid

| Viewport | Columns | Gutter | Outer margin | Content max |
| --- | --- | --- | --- | --- |
| Mobile, under 640px | 4 | 16px | 16px (20px from 390px) | 100% |
| Tablet, 640 to 1023px | 8 | 24px | 32px | 100% |
| Desktop, 1024px+ | 12 | 32px | 48px to auto | 1200px (1120 to 1280) |

- Column math at 1200px: (1200 − 11 × 32) ÷ 12 = 70.7px per column. Write the column spans in the wireframe (for example `cols 1-7 / 8-12`).
- **Baseline:** 4px. Every line-height is a multiple of 4 (see the type scale in `typography.md`) and every vertical space comes from the spacing scale, so text across columns lines up.
- **Alignment axis:** choose one primary left edge (often the start of column 1 or 2) and hold it down the page. Count distinct left edges per screen: 2 to 3 is clean; 4+ is noise.
- **Measure inside the grid:** body text spans at most 65ch (about 7 columns at 18px); never let a paragraph run the full 12 columns.
- Full-bleed only for the signature moment or real media.

## Spacing scale and rules

Scale (4px base): `4 8 12 16 24 32 48 64 96 128 160`. No other values in components.

| Relationship | Space |
| --- | --- |
| Label to its input; icon to its label | 4 to 8 |
| Heading to its paragraph | 12 to 16 (h3), 16 to 24 (h2, display) |
| Paragraph to paragraph | 16 (mobile) / 18 to 24 (desktop), about 1em |
| Paragraph or form to the CTA | 24 to 32 |
| Items in a list or grid | 24 to 48 |
| Section header block to section content | 48 to 64 |
| Section padding | tight 48 / 64, default 64 / 96, generous 96 / 160 (mobile / desktop) |

Proximity rule: space inside a group is at most half the space between groups. If a heading sits as close to the section above as to its own paragraph, the grouping is broken.

## Composition library

Pick a composition per section on purpose. Name it in the wireframe.

| Composition | Grid | Use for |
| --- | --- | --- |
| Asymmetric split | 7/5 or 8/4, text on the larger side unless the media is the point | Hero, feature rows |
| Hanging headline | h2 in cols 1-4, body and content in cols 5-11 | Problem, FAQ, editorial sections |
| Offset media | Text cols 1-6, image starts col 7 and bleeds past the right margin | Product screenshots |
| Index list | Narrow numeral column (cols 1-2) + text (cols 3-9), separated by 1px rules | Problem points, steps, objections |
| Single statement | One line at `h1` or `display` size, generous padding, nothing else | A turn in the argument, a real quote |
| Specimen | One large artifact (table, code, diagram) full width with margin callouts | Signature moment, how-it-works |
| Comparison table | You vs the current alternative, honest rows | Features, pricing context |
| Centred block | Only for under about 25 words | Final CTA, a single stat |

6/6 splits read as default. Use them only when two things truly have equal weight.

## Density and rhythm

Plan a density map before the wireframe: label each section Dense, Medium, or Airy.

- No more than two adjacent sections with the same density, and no two adjacent sections with the same composition.
- At least one Airy section between the hero and the final CTA.
- Generous padding before and after the signature moment.
- At most one inverted (dark) band per page, and only if it marks something: the signature moment or the final CTA.
- Dividers: whitespace or a 1px `line` rule. Not both. No wavy SVG separators.

## Hero patterns by product type

Choose by what the visitor needs to believe in the first 5 seconds.

| Product type | Pattern | The artifact | Avoid |
| --- | --- | --- | --- |
| Developer tool / API | Headline left, code or terminal right; or headline plus a copyable install command | A real snippet that runs, with real output | Fake code, glowing terminals |
| B2B SaaS with a UI | Headline and CTA above, real product screenshot below, cropped to the moment of value, optionally annotated | Screenshot with realistic sample data, labelled | Full-dashboard screenshots at unreadable scale, tilted 3D mockups (T18) |
| Consumer app | Headline with a device frame showing 1 to 2 real screens, or the product in use | Real screens, store badges | Floating phones over blobs (T3) |
| Marketplace | The action is the hero: search field or category picker above the fold | Working input | A headline explaining the marketplace instead of letting people use it |
| AI agent / automation | Before/after of the actual work: input on one side, finished output on the other | A real run, step-labelled | Sparkle icons, abstract "neural" art (T13, T21) |
| Service / done-for-you | Outcome headline, who it is for, a calendar or contact CTA, one case result | A named result with permission | Stock team photos |
| Hardware / physical | Large photography of the product, spec strip below | Real photos | Renders passed off as photos |
| Pre-product waitlist | Headline, one-field form, one honest artifact: sketch, prototype clip, founder note | Something real that shows intent | Screenshots of a product that does not exist |
| Content / community | Editorial layout, latest or best piece front and centre | Real content | "Join our community" with avatar stacks (T11) |

## Component quality bar

### Hero

| Do | Don't |
| --- | --- |
| One `h1`, under about 10 words, max-width 12 to 20ch so it breaks deliberately | A headline that wraps into 5 lines at 375px |
| Subhead 1 to 2 sentences under 55ch | A paragraph of features |
| One primary CTA plus at most one text-link secondary | Two filled buttons of equal weight |
| The artifact from the table above, on the alignment axis | Gradient blob, pill badge, avatar stack (T3, T11, T13) |
| CTA visible in the first viewport at 1280x800 and 375x667 | CTA pushed below the fold by a tall image |

### Navigation

| Do | Don't |
| --- | --- |
| Logo left, at most 5 links, primary CTA right (or a quiet text link if the hero holds the CTA). Login as a text link | Mega-menus on a 5-page site |
| Height 56 to 64px desktop, 56px mobile. Sticky only if the page is longer than about 3 screens | Shrink-and-grow animations on scroll |
| Mobile: a `button` with `aria-expanded` and `aria-controls`, full-height panel, focus trapped while open, Escape and link click close it, focus returns to the button | A hover-only menu, a `div` with `onClick` |
| Skip link as the first focusable element; `aria-current="page"` plus a non-colour indicator | Current page marked by colour alone |

### Proof

| Do | Don't |
| --- | --- |
| Logos only of real customers or partners, with permission. Monochrome, matched by optical size, 5 to 8 max | "Trusted by" strips of invented or unpermitted logos (T11) |
| Quotes under 40 words, with name, role, company; photo only with permission. Specific outcome over praise | Unattributed praise, AI or stock headshots |
| Numbers with source and date ("41 clinics live, March 2025, internal data") | Round numbers with no source (T12) |
| No proof yet: a true stage statement ("2 firms piloting from October") or a visible `[NEED: proof]` | Filling the gap with anything invented |

### How it works

| Do | Don't |
| --- | --- |
| 3 to 4 steps from first use to outcome, as an index list or one annotated artifact | Three identical icon cards (T6) |
| Each step names the customer's action and what they get | Steps that describe your architecture |
| Real UI crops, code, or the signature diagram as the visual | An icon per step |

### Features

| Do | Don't |
| --- | --- |
| Alternating text/media rows for 3 to 4 major capabilities | A grid of 6 to 9 equal cards |
| One annotated screenshot with 3 to 5 numbered callouts | Callouts on a mockup of UI that does not exist |
| A comparison table vs the current alternative, honest rows | Rows rigged so you win every line |
| Bento only when items differ in importance (T20) | Bento for equal items |

If you use cards: vary them by content, one border style, at most one shadow level, no icon-in-a-circle.

### Pricing

| Do | Don't |
| --- | --- |
| 1 to 3 tiers early; recommended tier marked by position, border, and a label, not colour alone | 4+ tiers at launch, or highlight by colour only |
| Price in tabular figures with currency and period ("$49 per seat / month, billed annually") | "$49" with no period |
| Monthly/annual toggle as a real button group with `aria-pressed`; savings stated exactly | A toggle that is a styled `div` |
| Feature rows with accessible text ("Included", "Not included") behind any check icons | Bare check icons |
| One CTA per tier, labelled for that tier. Prices from the founder or `[NEED: pricing]` | Placeholder prices |

### FAQ

| Do | Don't |
| --- | --- |
| Native `details`/`summary`, or a disclosure button with `aria-expanded` | Click-only divs |
| 4 to 8 questions from real objections (calls, support, `## Alternatives` in company.md) | Questions written to sound good ("Why is it so fast?") |
| Questions in the customer's words; answers start with the direct answer | Answers that start with "Great question" |

### Final CTA

| Do | Don't |
| --- | --- |
| Repeat the primary action with one reason to act now that is true | Fake urgency, countdown timers |
| The same label as the hero CTA, or a more specific one | A new, different action |
| Short and centred is fine here (under about 25 words) | Another full section of features |

### Footer

| Do | Don't |
| --- | --- |
| Product, company, resources, legal: only links that exist | A sitemap of every page |
| Contact method, legal name, location if relevant | A newsletter form with no newsletter |
| Caption token, muted colour still at 4.5:1 | Pale grey legal text under 4.5:1 |

### Buttons

| Spec | Value |
| --- | --- |
| Height | 44px default, 48 to 52px hero, 36px dense UI only with a 44px hit area |
| Padding | 16 to 24px horizontal |
| Radius | From the system: one of 0, 2, 4, 8, or full. Same everywhere (T9) |
| Label | Specific verb phrase, sentence case, 2 to 5 words (T22) |
| Hierarchy | One primary per view. Secondary is outline or text |

All states are required: default (label at 4.5:1 on the fill), hover (darken fill 6 to 10%, no grow or bounce), active (darker again or a 1px translate down), focus-visible (2px ring at 3:1 against the background, 2px offset), disabled (prefer not disabling; show a validation message instead), loading (keep the width, `aria-busy="true"`, block double submit). Arrows only on one or two navigating CTAs (T16).

### Forms

- Visible label above every input. Placeholder is an example, never the label.
- Input height 44 to 48px, font-size 16px or more (prevents iOS zoom on focus), border in the `boundary` colour (3:1).
- Correct `type`, `autocomplete`, and `inputmode` (`type="email" autocomplete="email"`).
- Errors inline below the field, in words that say how to fix it; linked with `aria-describedby`; `aria-invalid="true"`; not red alone.
- Validate on blur or submit, not on every keystroke.
- Success replaces the form with the next step, announced with `role="status"`.
- Waitlist forms ask for one field. Ask the rest after.
- A privacy line next to the field ("No spam. Unsubscribe in one click.") only if true.

## Component specs

| Element | Spec |
| --- | --- |
| Radius scale | 0, 2, 4, 8, 16, full. At most two values on one page |
| Borders | 1px. `line` for decoration (any ratio), `boundary` (3:1+) where the border is the only cue for a control |
| Shadows | Default none. At most two levels, ink-tinted at low opacity, only for elements that float (T10) |
| Icons | See Icon discipline in `anti-generic.md` |
| Images | Fixed aspect ratios (16:10, 4:3, 1:1), `object-fit: cover`, corners from the radius scale |
| Screenshots | Captured at 2x, cropped to the relevant area, sample data labelled |
| Links in body | Underlined. Colour change alone is not enough |
| Hit areas | 44x44px for primary controls and icon buttons (WCAG 2.5.5 AAA level; the AA minimum in 2.5.8 is 24x24px) |

## Responsive behaviour

- Mobile first. Design the 375px view before desktop.
- Breakpoints: `sm 640`, `md 768`, `lg 1024`, `xl 1280`. Splits stack below `md`. Media goes below its text unless the media is the point.
- Reduce section padding by about a third on mobile, not by half.
- Do not hide decision-relevant content on mobile; reorder or condense.
- Tables on mobile: horizontal scroll inside a focusable, labelled region (`role="region"`, `aria-labelledby`, `tabindex="0"`) with the first column sticky, or convert rows to stacked definition lists.
- Test at 320px for overflow. No horizontal page scroll at any width (WCAG 1.4.10 Reflow: content works at 320 CSS px wide).
