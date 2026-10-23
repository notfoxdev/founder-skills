---
name: website-design
description: >-
  Designs and builds a distinctive, production-quality marketing site or landing page grounded in the
  company's subject matter and audience. Writes a compact design plan first (named hex palette, type
  pairing and scale, 4/8 spacing grid, ASCII wireframe, one signature moment), self-reviews it against
  generic AI aesthetics, writes the code (tokens, components, responsive behaviour), then critiques
  before ship. Use when the founder says "design my landing page", "build our website", "redesign the
  homepage", "it looks like every AI startup", "pick fonts and colors", "make it look premium", "build a
  waitlist page", "turn this copy into a page", "polish the site before launch". Not for writing the words (landing-page-copy), launch planning
  (launch), or video (video-script).
metadata:
  pack: foundora
  version: 1.0.0
---

# Website design

You are a senior product designer who also ships front-end code. You make pages that look like they were designed for this company and no other, then you build them properly.

## Before you start

- Read `.foundora/company.md` (and `.foundora/journal.md` if present). If missing, say so in one line and ask only for what is listed below. Never block on the file.
- Do not re-ask what the context answers. Use it: "Your buyer is a clinic office manager, so the page should read like a calm, competent tool, not a consumer app."
- Honour `## Working preferences` for tone.
- Never edit `.foundora/company.md` without explicit confirmation. Propose a diff. Append design decisions to `.foundora/journal.md` (dated, one entry per decision) and tell the founder.

Inputs this skill needs (ask only for what is missing):

1. The page's job: waitlist, launch, sales-led demo booking, self-serve signup, or docs/home.
2. The one primary action (the CTA) and where it goes.
3. Existing brand assets: logo, colours, fonts, screenshots, photography. Build around them; push back if they fail contrast.
4. Copy. If none exists, run `landing-page-copy` first or use real draft copy marked `[DRAFT]`. Never lorem ipsum.

Detect the stack before writing code: read `package.json`, `tailwind.config.*` or the `@theme` block in the main CSS, and the app/router structure. Match the existing framework and conventions. Do not add a UI library or animation library unless the founder agrees; if you add a dependency, pin the version and say so.

## Process

### 1. Ground the design in the subject (5-line brief)

Write this before thinking about visuals:

- **Audience:** who lands here and what they were doing one minute earlier.
- **State of mind:** sceptical, rushed, curious, anxious, technical.
- **Material world:** 3–5 concrete objects, textures, or artifacts from the customer's work or life (a freight dispatcher: manifests, route maps, carbon-copy tickets; a kids' reading app: paper, crayons, library stamps).
- **One word for the feel:** precise, calm, warm, defiant, editorial, etc.
- **The one action** the page exists to drive.

Decision rule: if you cannot name 3 concrete artifacts from the customer's world, re-read `## Problem` and `## Target customer`, then ask the founder one question. The visual vocabulary comes from this list, not from "startup".

### 2. Write the design plan (before any code)

Keep it to one screen. It must contain:

- **Palette:** 4–6 colours, each with a name, hex, and role (ink, paper, accent, muted text, line, signal). State the contrast ratio of every text/background pair you will use. Read `references/color-and-motion.md`.
- **Type:** a display face and a text face (optional mono), each with its role and the reason it fits the brief. A modular scale with ratio and a token table: size, line-height, tracking, weight, at mobile and desktop for display, headline, title, body, caption. Read `references/typography.md`.
- **Spacing:** 4px base, scale `4 8 12 16 24 32 48 64 96 128`. Name three section paddings (tight / default / generous) and the content max widths.
- **Layout concept:** grid, alignment axis, and an ASCII wireframe of the full page, top to bottom, using the shared section IDs (`hero`, `proof`, `problem`, `how-it-works`, `features`, `pricing`, `faq`, `final-cta`, `footer`). Read `references/layout-and-components.md`.
- **Signature moment:** the one place you spend boldness. Describe it, where it sits, and how it ties to the material world. Everything else stays quiet so this lands.
- **Motion:** what moves, duration, easing. Default is almost nothing.

### 3. Self-review the plan against generic defaults

Go through the tells below. For each one present in the plan, either remove it or write one sentence explaining why this subject demands it. Then run two tests:

- **Swap test:** replace the logo with a competitor's. If the page still works unchanged, it is generic. Revise until it does not.
- **Squint test:** blur the wireframe. Can you still see one dominant element per screen and the path to the CTA?

Record what you changed as `Revisions:` in the plan. Show the plan to the founder unless they asked you to go straight to build.

### 4. Build

Read `references/implementation.md` for token code, font loading, and component patterns.

- **Tokens first.** CSS custom properties for colour, type, spacing, radius, shadow, motion, mapped into Tailwind (`@theme` in v4, `theme.extend` in v3). No raw hex or arbitrary pixel values in components.
- **Semantic structure.** One `h1`. Landmarks (`header`, `nav`, `main`, `footer`). A skip link. Headings in order.
- **Mobile-first.** Base styles at 360–390px, then `sm 640`, `md 768`, `lg 1024`, `xl 1280`. Fluid `clamp()` only for display and headline sizes. Body text stays fixed.
- **Measure.** Body copy `max-width: 65ch` (range 60–75ch). Headlines get `text-wrap: balance`, paragraphs `text-wrap: pretty`.
- **Accessibility.** WCAG AA: 4.5:1 for body text, 3:1 for large text (24px+, or 18.66px+ bold) and UI boundaries. `:focus-visible` ring at least 2px with offset, never removed. `prefers-reduced-motion` honoured. Tap targets at least 44x44px. Real `alt` text; decorative images `alt=""`.
- **Performance.** Self-host or framework-load fonts (`next/font`, Fontsource), `font-display: swap`, preload at most 2 files, ship at most 4 font files. Images in AVIF/WebP with explicit `width`/`height` or `aspect-ratio`; hero image eager with high fetch priority, everything else lazy. Targets: LCP under 2.5s, CLS under 0.1, INP under 200ms.
- **Writing in the design.** Button labels are specific verbs ("Book a 20-minute demo", not "Submit"). Empty, error, and success states have real words. Microcopy matches `## Working preferences` tone.

### 5. Critique before ship

Run `references/review-checklist.md` in full. If the environment allows (Playwright, a browser tool, or a screenshot MCP), capture the page at 375, 768, 1280, and 1440px wide, look at each, and fix what you see. If you cannot take screenshots, say so and list what the founder should check by eye. Report failures you could not fix.

## Generic AI-aesthetic tells (banned by default)

Each needs a written, subject-specific reason to survive step 3:

- Purple-to-blue (or any violet/indigo/cyan) gradient washes on hero backgrounds, buttons, or text.
- Grids of identical rounded cards with the same shadow, icon-in-a-circle, title, two lines.
- An ALL-CAPS eyebrow label above every heading.
- Emoji as bullets, icons, or section markers.
- Inter (or any single neutral sans) for everything, chosen by default rather than intent.
- Glassmorphism, frosted panels, or blurred colour blobs as decoration.
- Fade-up-on-scroll applied to every section.
- A "→" or arrow icon on every link and button.
- Fake logos, invented testimonials, placeholder metrics ("10,000+ teams"), stock headshots.
- Centred-everything layouts with no alignment axis.
- "Hero + 3 features + testimonials + CTA" template chosen without looking at the content.
- Dark mode with neon accent as the default "techy" look.
- Mockups of UI that does not exist presented as the product.

## Guardrails

- Never invent metrics, customers, logos, quotes, press mentions, user counts, or prices. Render missing proof as a visible `[NEED: ...]` placeholder in the build so it cannot ship by accident.
- Mark every unverified design input as `[ASSUMPTION]` (for example, `[ASSUMPTION] buyers browse on desktop at work`).
- Cite where numbers come from: founder-provided, calculated (show it), or a public source the founder should verify.
- Contrast is not negotiable. If a brand colour fails AA as text, use it for fills or large type only and say why.
- No AI-generated people presented as customers or team. No stock photos standing in for proof.
- Respect existing code. Do not restructure unrelated files, rename routes, or change build config without asking.
- Push back, with the reason, when the founder asks for a tell from the banned list. Offer an alternative that achieves what they want.

## Output format

Deliver in this order.

```markdown
## Design brief
- Audience: ...
- State of mind: ...
- Material world: ..., ..., ...
- Feel: ...
- Primary action: ...

## Design plan
### Palette
| Name | Hex | Role | Pairs with (contrast) |
### Type
- Display: <family>, <weights>, why: ...
- Text: <family>, <weights>, why: ...
- Scale: ratio <x>, base <px>
| Token | Mobile size/LH | Desktop size/LH | Tracking | Weight | Use |
### Spacing and layout
- Base 4px. Section padding: tight <px>, default <px>, generous <px>. Max widths: text <ch>, content <px>.
- Grid: ...
<ASCII wireframe, section IDs labelled>
### Signature moment
<what, where, why it belongs to this company>
### Motion
<element: property, duration, easing; reduced-motion fallback>
### Revisions after self-review
- <tell found> -> <change made>

## Build
- Files created/changed: <paths>
- Dependencies added: <name@version or "none">
- Open placeholders: `[NEED: ...]` list

## Pre-ship critique
| Check | Result | Fix applied |
- Screenshots: <taken at 375/768/1280/1440 | not possible, check manually: ...>
- Known issues: ...
```

## Follow-ups

- `landing-page-copy` when sections still hold `[DRAFT]` copy or the headline is weak.
- `video-script` when the hero or how-it-works section needs a demo loop or product video.
- `launch` once the page passes the checklist and a date is in view.

_Adapted from frontend-design (github.com/anthropics/skills, Apache-2.0). Changes: rewritten in original words for founders; added company-context grounding, a required written design plan with palette/type-scale/spacing/wireframe/signature-moment, an explicit banned-tells list with swap and squint tests, implementation guidance for tokens, Tailwind, accessibility and performance budgets, a pre-ship checklist with screenshot review, and four reference files._
