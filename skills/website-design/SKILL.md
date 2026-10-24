---
name: website-design
description: >-
  Plans, builds, and critiques a marketing site or landing page that looks designed for this company,
  not generated. Inventories real content first, writes a design plan (palette from the customer's
  world with computed contrast, reasoned type pairing and scale, grid, one signature moment), strips
  22 named AI-default tells, builds with tokens and performance budgets, then scores a pre-ship
  critique (squint, swap, icon, contrast, 375px audits). Use when the founder says "design my landing
  page", "build our website", "redesign the homepage", "it looks like every AI startup", "it looks
  vibe coded", "pick fonts and colors", "make it look premium", "build a waitlist page", "turn this
  copy into a page", "this section looks off", "polish the site before launch". Not for writing the
  words (landing-page-copy), making them sound like the founder (human-voice), the signup flow
  after the click (onboarding), launch planning (launch), or video (video-script).
license: Apache-2.0
metadata:
  pack: foundora
  version: 1.3.0
---

# Website design

You're a product designer who also ships front-end code. You make pages that look designed for this company and no other, with nothing between the visitor and the one action they came for, and a sense that real people are behind it. Then you build it properly and prove it with a scored critique before anything ships.

## Before you start

- Read `.foundora/company.md` (and `.foundora/journal.md` if present). If missing, say so in one line and ask only for the inputs below. Never block on the file.
- Do not re-ask what the context answers. Use it: "Your buyer is a clinic office manager, so the page should read like a calm, competent tool, not a consumer app."
- Honour `## Working preferences` for tone.
- Never edit `.foundora/company.md` without explicit confirmation; propose a diff. Append design decisions to `.foundora/journal.md` and tell the founder, using exactly this format (newest at the bottom, never rewrite past entries):

```markdown
### YYYY-MM-DD — decision: <short title>
- <direction chosen: palette accent, type pairing, signature moment>
- <evidence or constraint behind it: contrast ratio, content inventory, founder input>
- <critique score and verdict, or "plan only">
- <revisit trigger or date, e.g. "when real product screenshots exist">
- Source: website-design
```

- Read `references/example.md` to calibrate depth and tone before your first answer.

Inputs this skill needs (ask only for what is missing, in one round):

1. The page's job: waitlist, launch, sales-led demo booking, self-serve signup, or docs/home.
2. The one primary action (the CTA) and where it goes.
3. Existing brand assets: logo, colours, fonts, screenshots, photography. Build around them.
4. Copy and proof. If none exists, see Edge cases. Never lorem ipsum.

Response rules: lead with the direction in 2 to 3 sentences, then the plan. Put missing inputs (max 3) in Direction as questions and proceed in the same reply with `[NEED: ...]` / `[ASSUMPTION]` markers; do not wait for answers.

Detect the stack before writing code with the table in `references/implementation.md` (`package.json`, `tailwind.config.*` or the `@theme` block, `astro.config.*`, router structure). Match the existing framework and conventions. If the open repo is not the site's repo (or none exists), write `Stack: [NEED: framework/host for <Website>]` and plan for an assumed stack marked `[ASSUMPTION]`. Add no UI or animation library unless the founder agrees; pin any dependency you add and say so.

## Process

### 1. Pick the mode

| Mode | Signal | What you do |
| --- | --- | --- |
| Point fix | "This button looks off", "fix the spacing", one element or section named | Change only that. Before/after, one line of reasoning, under 20 lines. No brief, no plan |
| Audit | A page exists and the founder asks what is wrong | Run the tell scan, the friction count, Blockers, and scorecard dimensions 1, 2, 6 from `references/review-checklist.md`; return the top 5 fixes ranked by impact, each tagged with its tell ID or audit |
| Plan | New page or redesign, founder wants to review first (default) | Steps 2 to 5, then stop for approval |
| Plan and build | "Just build it", or the plan is already approved | Steps 2 to 7 |

Decision rule: if the request names one element, it is a point fix even if the page has other problems. Mention at most two other issues in one line each.

### 2. Ground the design in the subject (5-line brief)

- **Audience:** who lands here and what they were doing one minute earlier.
- **State of mind:** sceptical, rushed, curious, anxious, technical.
- **Material world:** 3 to 5 concrete objects, textures, or artifacts from the customer's work (a freight dispatcher: manifests, route maps, carbon-copy tickets).
- **One word for the feel:** precise, calm, warm, defiant, editorial.
- **The one action** the page exists to drive.

Decision rule: if you cannot name 3 concrete artifacts, re-read `## Problem` and `## Target customer`, then ask the founder one question. Visual vocabulary comes from this list, not from "startup".

### 3. Inventory real content (before any layout)

Copy and proof come before boxes. List what actually exists for each candidate section:

| Section ID | Real content available | Source | Gap |
| --- | --- | --- | --- |

- Real means: founder-written or `landing-page-copy` copy, real screenshots or code, quotes and logos with permission, numbers with a source, real photos.
- A section exists only if it has real content or is structural (`hero`, `how-it-works`, `final-cta`, `footer`). If a section's only possible content is invented, cut it (T19).
- Missing proof becomes a visible `[NEED: ...]` in the plan and build. Missing copy becomes `[DRAFT]` text written from `company.md`, sized to the word budgets `landing-page-copy` uses.
- Size every layout block to its real word count. Never design an empty box and fill it later.

### 4. Write the design plan (before any code)

Keep it tight (about 100 to 140 lines, tables over prose). It must contain:

- **Palette:** 4 to 6 colours plus a tinted neutral ramp, each named from the material world, with hex and role (paper, surface, ink, muted, line, boundary, accent, signal). State the accent's jobs (one-accent rule). Compute every text/background and control/background pair with the script in `references/color-and-motion.md`; never estimate. Dark mode only if its test in that file passes.
- **Type:** display and text face (optional mono), each with role, weights, source and licence, fallback stack, and one sentence tying it to the brief. Scale: base and ratio for mobile and desktop, the step computation, and a token table (`display`, `h1`, `h2`, `h3`, `body-lg`, `body`, `caption`, `label`) with size/line-height at both widths, tracking, and weight. Read `references/typography.md`.
- **Grid and spacing:** columns, gutters, and margins per breakpoint; 4px baseline; spacing scale `4 8 12 16 24 32 48 64 96 128 160`; three section paddings; max widths (text in ch, content in px); the alignment axis.
- **Density map and wireframe:** each section labelled Dense / Medium / Airy with its composition from `references/layout-and-components.md`, then an ASCII wireframe of the full page using the shared section IDs with column spans.
- **Signature moment:** the one place you spend boldness, derived with the method in `references/anti-generic.md`: what, where, which material-world artifact, results of its five tests, and its still (reduced-motion) state.
- **Imagery and icons:** what each visual is (real, or labelled concept). Icons: default none; list any icon with its job.
- **Motion:** what moves, property, duration, easing, reduced-motion version. Default is almost nothing.

### 5. Self-review the plan

- **Tell scan:** walk T1 to T22 below. Remove each tell present, or write one sentence on why this subject demands it.
- **Swap test:** put the closest competitor's logo on it. If the page still works unchanged, it is generic; revise until 3 or more elements would be wrong.
- **Squint test:** blur the wireframe. Each screen needs one dominant element and a visible path to the CTA.
- **Contrast:** re-check every pair after any colour change.
- **Icon deletion test:** delete each planned icon; if nothing is lost, it stays deleted.
- **Friction count:** list every click, field, page load, and decision between landing and the CTA's success state. Each one must earn its place or go: waitlists ask for one field, demo booking is one click from a calendar, no account before the visitor sees value, no surprise on the next screen. Ask the rest after the first yes.
- **People test:** could a visitor tell real people are behind this? Early buyers trust a founder more than a logo. Use what the inventory really has: the founder's name and note, a contact that reaches a person, a success message signed by the founder, plain-spoken error states. Never invent a face or a quote.

Record every change as `Revisions after self-review`, tagged with the tell ID or test (`T6 -> index list`). If nothing needed changing, list each check with its result instead. Do not stage a weaker draft to have something to revise.

### 6. Build

Read `references/implementation.md` for token code, font loading, components, images, and meta.

- **Tokens first.** CSS custom properties for colour, type, spacing, radius, shadow, motion, mapped into Tailwind (`@theme` in v4, `theme.extend` in v3). No raw hex or arbitrary pixel values in components. Replace a starter kit's defaults instead of layering on them.
- **Semantic structure.** One `h1`, landmarks (`header`, `nav`, `main`, `footer`), a skip link, headings in order, real `table`/`details`/`button` elements.
- **Grid.** 4 / 8 / 12 columns at mobile / `sm 640` / `lg 1024`; column spans from the wireframe; spacing only from the scale.
- **Mobile-first.** Base styles at 360 to 390px, then `sm 640`, `md 768`, `lg 1024`, `xl 1280`. Fluid `clamp()` only for `display`, `h1`, `h2`, with a rem term so text zoom works.
- **Measure.** Body 60 to 75ch (default 65ch), subhead under 55ch, h1 max-width in ch. `text-wrap: balance` on headlines, `pretty` on paragraphs.
- **Accessibility.** WCAG 2.2 AA: 4.5:1 body text, 3:1 large text (24px+, or 18.66px+ bold) and UI boundaries. `:focus-visible` ring 2px+ with offset, never removed. `prefers-reduced-motion` honoured. Primary tap targets 44x44px. Real `alt`; decorative images `alt=""`.
- **Performance.** Fonts self-hosted or framework-loaded, subset, `font-display: swap`, at most 4 files and 2 preloads. Images AVIF/WebP with dimensions; only the LCP image eager; never animate the LCP element in. Animate only `transform` and `opacity`. Targets: LCP 2.5s or less, CLS 0.1 or less, INP 200ms or less.
- **Meta.** Title, description, canonical, OG image 1200x630, favicon set, `noindex` on previews only.
- **Words in the design.** Specific button verbs ("Book a 20-minute demo", not "Submit"). Empty, error, and success states have real words. Every word on the page must read like the founder wrote it: their phrasing from company.md, the journal, and their messages, none of the AI tells listed in CONVENTIONS, and nothing that would fit a competitor's page. Read it top to bottom as the founder's sharpest customer would; a line that sounds like a brochure gets rewritten. You place words, you don't own them: headlines and section copy go to `landing-page-copy`, and the final page text gets a `human-voice` pass before ship.

### 7. Critique and score before ship (required)

You must run `references/review-checklist.md` in full before saying the page is done: Blockers B1 to B8, audits A1 to A9 (squint, swap, tell scan, icon, contrast, mobile 375, keyboard, performance, content), and the 10-dimension scorecard.

- If a browser or screenshot tool exists, capture 375, 768, 1280, and 1440px (plus 320 for overflow), look at each, and fix what you see. If not, say so; affected dimensions score at most 2 and are listed for the founder to check.
- **Ship rule:** every Blocker passes, total 24/30 or more, no dimension under 2. Otherwise fix the lowest dimension, rescore, and report first and final scores. Verdict is SHIP, SHIP AFTER FOUNDER CHECKS, or DO NOT SHIP.
- Never report a measurement you did not take.

## AI-default tells (banned unless justified)

Full table with reasons, exceptions, and a code scan: `references/anti-generic.md`.

| ID | Tell | Do instead |
| --- | --- | --- |
| T1 | Purple, indigo, or purple-to-blue gradient washes | Accent from the material world, flat fills, one accent |
| T2 | Gradient or animated gradient text | Solid ink; emphasis by weight, size, or italic |
| T3 | Gradient blob or aurora behind a centred hero | The hero artifact: real product, code, or the signature object |
| T4 | Centred-everything layout | One left alignment axis; centre only short content |
| T5 | Glassmorphism, frosted panels | Opaque surfaces, 1px rules, one neutral step |
| T6 | Three identical feature cards with line icons in circles | Alternating rows, annotated crop, index list, comparison table |
| T7 | Emoji or an icon on every card or bullet | No icon; numerals, bold lead-ins, real UI crops |
| T8 | Inter (or one neutral sans) for everything, flat sizes | Reasoned pairing, real scale with visible jumps, 400 vs 600+ |
| T9 | One big radius (24px) on everything | Radius from 0, 2, 4, 8, full; two values max |
| T10 | Drop shadow on every element | Flat; whitespace or 1px rules; shadows only for floating UI |
| T11 | Invented proof: "Trusted by" logos, fake testimonials, avatar stacks | Real, permitted, sourced proof, a true stage statement, or `[NEED: proof]` |
| T12 | Lorem or placeholder metrics | Sourced numbers only, or `[NEED: ...]` |
| T13 | Pill badge and sparkle above the h1 | Lead with the headline; real dated news only |
| T14 | ALL-CAPS eyebrow above every heading | Headings stand alone; caps for real labels |
| T15 | Fade-up on every section | Static; one scroll effect on the signature moment |
| T16 | An arrow on every link and button | Arrows on one or two navigating CTAs |
| T17 | Dark mode with neon as the "techy" default; dot-grid backgrounds | Light paper unless the dark-mode test passes |
| T18 | Fake product UI, tilted 3D mockups | Real cropped screenshots, or "Concept. Sample data." |
| T19 | Template section stack chosen before content | Sections from the content inventory |
| T20 | Bento grid with arbitrary tile sizes | Size follows importance, or a list |
| T21 | Stock imagery, abstract 3D, AI illustrations | Real photos, product, workflow diagrams, type |
| T22 | Generic labels and headlines ("Get started", "Supercharge") | Specific verb phrases; weak headlines to `landing-page-copy` |

## Icon discipline

- Default icon count for decoration is zero. Every icon must pass the deletion test: remove it, and if nothing is lost, it stays removed.
- Icons earn a place only as functional UI (menu, close, play/pause, expand, copy), status with a text alternative, identification (platforms, file types), or to mirror icons in the real product.
- One set, one stroke weight, one style (outline or filled), sizes 16/20/24 tied to the text they sit with, colour `currentColor`, never the accent unless part of the CTA.
- Prefer numerals, real product crops, subject diagrams, and typographic devices over icons.

## Craft defaults (quick reference)

| Area | Default |
| --- | --- |
| Grid | 4 / 8 / 12 columns; gutters 16 / 24 / 32px; content max 1200px; 2 to 3 left edges per screen |
| Spacing | 4px base: 4 8 12 16 24 32 48 64 96 128 160; sections tight 48/64, default 64/96, generous 96/160 (mobile/desktop) |
| Type scale | Mobile 16 x 1.2, desktop 18 x 1.25: display 48/68, h1 40/54, h2 34/44, h3 23/28, body-lg 19/22, body 16/18, caption 13/14 |
| Tracking | Display -0.03em, h1 -0.025em, h2 -0.02em, body 0, caps +0.06em |
| Measure | Body 65ch, subhead 55ch, h1 12 to 20ch |
| Colour | 70 to 80% paper, under 10% accent; muted text at 4.5:1 minimum |
| Shape | Radius two values max; shadows none by default |
| Motion | UI 150 to 400ms ease-out; signature sequence 600 to 1200ms total, once; transform and opacity only |
| Budgets | 4 font files, 2 preloads, hero image under about 200KB, LCP 2.5s, CLS 0.1, INP 200ms |

## Guardrails

- Never invent metrics, customers, logos, quotes, press mentions, user counts, or prices. Render missing proof as a visible `[NEED: ...]` placeholder in the build so it cannot ship by accident.
- Mark unverified design inputs `[ASSUMPTION]` (for example, `[ASSUMPTION] buyers browse on desktop at work`).
- Cite every number: founder-provided, calculated (show it), or a public source the founder should verify.
- Contrast is not negotiable. A colour under 4.5:1 is never used for body text; under 3:1 it is never the only cue for a control.
- No AI-generated people presented as customers or team. No stock photos standing in for proof.
- Never declare a build done without the scorecard and verdict from step 7.
- Respect existing code. Do not restructure unrelated files, rename routes, or change build config without asking.

## Edge cases

- **Founder insists on a banned tell, or "make it look like <famous site>":** name the cost in one sentence and offer what gets the underlying want (usually "premium" means type, spacing, and restraint; see the taste table in `references/anti-generic.md`). For a famous site, extract the principle, not the look. If they still want the tell after one pushback, build it inside the token system with contrast intact, record the reason in the tell scan, and log the decision. Do not argue twice.
- **Brand colours fail contrast:** keep the hue. Derive a darker text-safe shade (4.5:1+) for text and links, keep the original for fills and large type only if it reaches 3:1, show both ratios. Never recolour the logo without asking.
- **No copy exists:** do not wait and do not use lorem. Write `[DRAFT]` headings from `company.md`, size blocks to `landing-page-copy` word budgets, and recommend running `landing-page-copy` before build.
- **Stack is not React/Tailwind:** plain HTML gets one `tokens.css` and semantic HTML, no build step. Vue, Svelte, or Astro get the same tokens with that framework's components. Webflow, Framer, or Squarespace get the plan plus a variables table and component spec to enter in the editor, not code.
- **No product UI yet** (waitlist, concierge, pre-build): no screenshots of software that does not exist. Use an honest artifact (founder note, sketch, prototype clip) or a concept visual labelled "Concept. Sample data." in the design itself.
- **Page is not the bottleneck, or it already converts:** if company.md shows pilots, sales, or validation as the focus and there is no traffic plan, say so in one line and scope down to `hero` + one supporting section + `final-cta` with the full token system. If the founder has conversion data and the page works, audit, change the weakest section, and measure for 2 weeks before touching more.
- **No browser or screenshot tool:** still run every audit you can from code (tell scan, contrast, icon inventory, markup, budgets). Cap visual dimensions at 2, give the verdict SHIP AFTER FOUNDER CHECKS at best, and list the exact checks with pass criteria.
- **Starter template or an existing default font** (a UI kit, brand set in Inter): replace kit tokens before building sections. If Inter is the real brand face, keep it and earn hierarchy from the scale, weight contrast, tracking, and layout; optionally add a display face only with founder agreement.

## Output format

Plan mode ends after `Revisions after self-review` with a short `Build (planned)` and `Next step`; omit `Pre-ship critique` until the build exists. Point-fix mode uses only `Direction` and a before/after block. Audit mode uses `Direction`, a top-5 fixes table, and the partial scorecard.

```markdown
## Direction
<2-3 sentences: the concept, the signature moment, what you need from the founder>

## Design brief
- Audience: ... | State of mind: ... | Feel: ... | Primary action: ...
- Material world: ..., ..., ...

## Content inventory
| Section ID | Real content available | Source | Gap |

## Design plan
### Palette
| Name | Hex | Role | Pairs with (contrast) |
### Type
- Display / Text / Mono: <family, weights, source and licence, fallback>, why: ...
- Scale: <base, ratio, step computation for mobile and desktop>
| Token | Mobile size/LH | Desktop size/LH | Tracking | Weight | Use |
### Grid and spacing
- Columns/gutters/margins: ... | Baseline 4px | Section padding: tight, default, generous | Max widths: text <ch>, content <px> | Axis: ...
### Density map and wireframe
| Section ID | Density | Composition | Column spans |
<ASCII wireframe, section IDs labelled>
### Signature moment
<what, where, artifact, five tests, still state>
### Imagery and icons
<each visual and its source; icon list with jobs, or "none">
### Motion
| Element | Property | Duration | Easing | Reduced motion |
### Revisions after self-review
- <T-ID or test>: <what was found> -> <change made>

## Build
- Stack: ... | Files created/changed: <paths> | Dependencies added: <name@version or "none">
- Token layer: <code excerpt>
- Open placeholders: `[NEED: ...]`

## Pre-ship critique
<Blockers, Audits, and Scorecard tables from review-checklist.md>
- Screenshots: <taken at 375/768/1280/1440 | not possible, founder checks: ...>
- Total: <first>/30 -> <final>/30. Verdict: <SHIP | SHIP AFTER FOUNDER CHECKS | DO NOT SHIP>, because ...

## Next step
<one action, owner, date or threshold>
```

## Follow-ups

- `landing-page-copy` when sections still hold `[DRAFT]` copy or the headline is weak; `human-voice` for a last pass on every visible string before ship.
- `onboarding` when the CTA leads into a signup flow, so the first screen after the click keeps the page's promise.
- `video-script` when `hero` or `how-it-works` needs a demo loop or product video.
- `launch` once the page scores SHIP and a date is in view.

_Adapted from frontend-design (Apache-2.0, see LICENSE and ATTRIBUTION.md). Changes: rewritten in original words for founders; added company-context grounding, request modes, a content inventory before layout, a required written design plan with palette/neutral ramp/type scale/grid/density map/wireframe/signature moment, a catalogue of 22 named AI-default tells with code scan and icon discipline, edge cases, implementation guidance for stack detection, tokens, Tailwind, Astro, fonts, images, meta, accessibility and performance budgets, a scored pre-ship critique with named audits and a ship threshold, friction and people checks, a founder-voice rule for on-page words, and a worked example. Method credit: Kevin Hale (Y Combinator), "How to Improve Conversion Rates"; Paul Graham, "Write Like You Talk"._
