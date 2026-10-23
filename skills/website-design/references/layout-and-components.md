# Layout and components

Read this when choosing the hero, sequencing sections, or building any component. Section IDs here are shared with `landing-page-copy` so copy drops into the layout without renaming.

## Shared section IDs

| ID | Job | Required |
| --- | --- | --- |
| `hero` | Headline, subhead, primary CTA, one artifact that shows the product or outcome | Yes |
| `proof` | Real evidence: logos with permission, a named quote, a sourced number, a design-partner count | If any proof exists |
| `problem` | The situation the customer is in today, in their words | Usually |
| `how-it-works` | 3–4 steps or one annotated flow from first use to outcome | Yes |
| `features` | Capabilities tied to outcomes, only those that matter for the decision | Optional |
| `pricing` | Tiers or a single price, or "talk to us" with what happens next | If self-serve |
| `faq` | Objections answered plainly | Usually |
| `final-cta` | One repeat of the primary action with a reason to act now | Yes |
| `footer` | Navigation, legal, contact | Yes |

Order is a default. A pre-product waitlist might be `hero`, `problem`, `how-it-works`, `final-cta`. A dev tool might put `how-it-works` (a code sample) right after `hero`.

## Grid and alignment

- 12-column grid on desktop, 4 on mobile, 8 on tablet. Gutter 16px mobile, 24px tablet, 32px desktop.
- Content max width 1120–1280px. Text column max 65ch. Full-bleed only for the signature moment or media.
- Choose one alignment axis (usually a left edge) and hold it. Count the distinct left edges on a screen: aim for 2–3. Every extra edge looks like noise.
- Centre only short, symmetric content (a final CTA, a single stat). Centred paragraphs over 2 lines are hard to read.
- Asymmetry is a tool: a 7/5 or 8/4 split reads as designed; 6/6 reads as default.

## Section rhythm

- Three section paddings, used deliberately: tight (48–64px), default (96px desktop / 64px mobile), generous (128–160px desktop / 96px mobile). Generous goes before and after the signature moment.
- Vary density. Follow a dense section (features table) with an airy one (a single quote, large).
- Vary composition. If two adjacent sections are both "heading on top, three things below", change one.
- At most one inverted (dark) band per page, and only if it marks something: the signature moment or the final CTA.
- Dividers: either whitespace or a 1px line in the `line` colour. Not both. Not wavy SVG separators.

## Hero patterns by product type

Choose by what the visitor needs to believe in the first 5 seconds.

| Product type | Pattern | The artifact | Avoid |
| --- | --- | --- | --- |
| Developer tool / API | Headline left, code or terminal right; or headline plus a copyable install command | A real snippet that runs, with real output | Fake code, glowing terminals |
| B2B SaaS with a UI | Headline and CTA above, real product screenshot below, cropped to the moment of value, optionally annotated | Screenshot with realistic but clearly sample data | Full-dashboard screenshots at unreadable scale, tilted 3D mockups |
| Consumer app | Headline with device frame showing 1–2 real screens, or the product in use | Real screens, app store badges | Floating phones over blobs |
| Marketplace | The action is the hero: search field or category picker above the fold | Working input | A headline that explains the marketplace instead of letting people use it |
| AI agent / automation | Before/after of the actual work: input on one side, finished output on the other | A real run, timestamped or step-labelled | Sparkle icons, abstract "neural" art |
| Service / done-for-you | Outcome headline, who it is for, a calendar or contact CTA, one case result | A named result (with permission) | Stock team photos |
| Hardware / physical | Large photography of the product, spec strip below | Real photos | Renders passed off as photos |
| Pre-product waitlist | Headline, one-field form, one honest artifact: sketch, prototype clip, manifesto paragraph | Something real that shows intent | Fake screenshots of a product that does not exist |
| Content / community | Editorial layout, latest or best piece front and centre | Real content | Generic "join our community" with avatars |

Hero rules: one `h1`, headline under about 10 words where possible, subhead 1–2 sentences under 55ch, one primary CTA plus at most one secondary (text link). The hero should fit in the first viewport on a 1280x800 laptop without the CTA falling below the fold.

## Navigation

- Logo left, at most 5 links, primary CTA right. Login as a quiet text link.
- Height 56–64px desktop, 56px mobile. Sticky only if the page is longer than about 3 screens; no shrink-and-grow animation.
- Mobile: a `button` with `aria-expanded` and `aria-controls`, opening a full-height panel. Trap focus while open, close on Escape and on link click, return focus to the button.
- A visible skip link ("Skip to content") as the first focusable element.
- Current page marked with `aria-current="page"` and a visual indicator that is not colour alone.

## Buttons

| Spec | Value |
| --- | --- |
| Height | 44px (default), 48–52px (hero), 36px (dense UI only, with 44px hit area) |
| Padding | 16–24px horizontal |
| Radius | From the system: pick one of 0, 4, 8, or full. Same everywhere |
| Label | Specific verb phrase, sentence case, 2–5 words |
| Hierarchy | One primary per view. Secondary is outline or text. Never two filled buttons side by side with equal weight |

States, all required:

- **Default:** accent fill, ink or paper text at 4.5:1.
- **Hover:** small, legible change: darken fill 6–10% or shift background. No grow or bounce.
- **Active:** slightly darker again, or a 1px translate down.
- **Focus-visible:** 2px ring in a colour with 3:1 against the background, 2px offset. Do not rely on hover styles for focus.
- **Disabled:** reduced contrast plus `cursor: not-allowed`; prefer not disabling at all and showing a validation message instead.
- **Loading:** keep the width (no jump), show a spinner or progress text, set `aria-busy="true"`, prevent double submit.

Arrows on buttons: only where they mean "goes somewhere" and only on one or two key CTAs, not on every link.

## Forms

- Visible label above every input. Placeholder is an example, never the label.
- Input height 44–48px, font-size at least 16px (prevents iOS zoom on focus).
- Correct `type`, `autocomplete`, and `inputmode` (`type="email" autocomplete="email"`).
- Errors inline, below the field, in words that say how to fix it; link with `aria-describedby`; mark `aria-invalid="true"`. Errors use an icon or text in addition to red.
- Validate on blur or submit, not on every keystroke.
- Success replaces the form with a clear next step ("Check your inbox. We sent a link to name@company.com."), announced via `role="status"`.
- Waitlist forms ask for one field. Every extra field costs signups; ask the rest after.
- State privacy next to the field in one line if you collect email ("No spam. Unsubscribe in one click.") only if true.

## Features

Alternatives to the identical card grid:

- **Alternating rows:** text on one side, real media on the other, switching sides. Good for 3–4 major capabilities.
- **One annotated screenshot:** a single large image with 3–5 numbered callouts.
- **Numbered list with large numerals** in the display face, for sequential value.
- **Comparison table:** you vs the current alternative (spreadsheets, an agency, doing nothing). Honest rows only.
- **Bento layout** only when items genuinely differ in importance, so tiles differ in size for a reason.

If you use cards: vary them by content, not decoration. One border style, at most one shadow level, no icon-in-a-circle by default.

## Proof

- Logos: only real customers or partners with permission. Monochrome, matched by optical size (not identical pixel width), 5–8 maximum.
- Quotes: name, role, company, and photo only with permission. Short (under 40 words). Specific outcome over praise.
- Numbers: with source and date ("41 clinics live, March 2025, internal data").
- No proof yet: say what is true ("In private beta with 6 design partners") or leave `[NEED: proof]`. Never fill the gap.

## Pricing

- 1–3 tiers for early stage; 4 only with a clear enterprise tier.
- Mark the recommended tier with structure (position, border, label) not colour alone.
- Price in the display or a tabular face, currency and billing period stated ("$49 per seat / month, billed annually").
- Monthly/annual toggle: a real `button` group or switch with `aria-pressed`, savings stated in currency or exact percent.
- Feature rows: check icons have accessible text ("Included" / "Not included").
- One CTA per tier, labelled for that tier ("Start Team trial").
- Prices come from the founder. If unknown: `[NEED: pricing]`.

## FAQ

- Native `details`/`summary` or a disclosure button pattern with `aria-expanded`.
- 5–8 questions drawn from real objections (sales calls, support, the alternatives in `company.md`).
- Questions in the customer's words; answers start with the direct answer.

## Footer

- Columns: product, company, resources, legal. Only links that exist.
- Contact method, company legal name, and location if relevant for trust.
- Small type (caption token), muted colour still at 4.5:1.
- Not a second sitemap of every page. Not a newsletter form unless there is a newsletter.

## Component quality specs

| Element | Spec |
| --- | --- |
| Radius scale | 0, 4, 8, 16, full. Use at most two values on one page |
| Borders | 1px in the `line` colour. 3:1 contrast if the border is the only cue for an interactive element |
| Shadows | At most two levels. Tint with the ink colour at low opacity rather than pure black. Many pages need none |
| Icons | One set, one stroke weight (1.5px or 2px), 20 or 24px, aligned to text baseline or cap height |
| Images | Fixed aspect ratios (16:10, 4:3, 1:1). `object-fit: cover`. Rounded corners match the radius scale |
| Screenshots | Captured at 2x, cropped to the relevant area, sample data plausible and labelled if invented |
| Links in body | Underlined. Colour change alone is not enough |
| Hit areas | 44x44px minimum, including icon buttons |

## Responsive behaviour

- Mobile first. Design the 375px view before desktop.
- Stack splits below `md` (768px). Media goes below its text unless the media is the point.
- Reduce section padding by about a third on mobile, not by half.
- Do not hide content on mobile that matters for the decision; reorder or condense instead.
- Tables on mobile: horizontal scroll inside a labelled region, or convert rows to stacked definition lists.
- Test at 320px for overflow. No horizontal page scroll at any width.
