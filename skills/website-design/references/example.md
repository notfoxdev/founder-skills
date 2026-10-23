# Worked example: website-design

> Illustrative and fictional (Ledgerline fixture). Calibrates depth and format only; never reuse its content, palette, or fonts in a real answer.

Two turns: the plan (Plan mode), then build notes and the scored critique after the founder approves (Plan and build mode). Hard parts shown: no product UI exists (concept label), no proof (stage statement plus `[NEED]`), the first accent failed contrast, a section cut for having no real content, a pushback on showing a goal as a price, tells that crept in during the build and were caught by the scan, and a verdict of DO NOT SHIP despite a high design score because two Blockers depend on founder inputs.

---

## Turn 1

**Request:** "Design our waitlist landing page."

**Context used:** `evals/fixture-company.md` as `.foundora/company.md`. Validation stage, waitlist page only, 62 signups (9 in the target size band), 2 free concierge pilots start next week, no revenue, no product UI. Buyer is the managing partner; ops leads and bookkeepers use it daily. Alternatives: Google Sheets checklists, Karbon and TaxDome templates, doing nothing. Tone: direct, tables over paragraphs, US spelling. No brand assets, no copy, no repo, so: Plan mode, copy marked `[DRAFT]`, stack `[ASSUMPTION]` Next.js + Tailwind v4.

## Direction
Make the page look like a well-kept close binder, not a SaaS site: cream columnar paper, green ledger rules, red pencil ticks, and one close board where ticks land row by row and a blocked client gets stamped. The board is the only bold moment and is labelled "Concept" because the pilots run concierge and no UI exists; a dashboard mockup would be the first thing a skeptical partner tests, so there is none. Before build I need `[NEED: final hero copy from landing-page-copy]` and `[NEED: OK to describe the 2 pilot firms by size, unnamed]`. Scope: the pilots are your bottleneck this month, not the page, so this is one short scroll with no features or pricing sections; its job is to catch partners arriving from your LinkedIn posts and pilot referrals.

## Design brief
- Audience: managing partner or ops lead at a 3 to 15 person bookkeeping firm, arriving from the founder's LinkedIn post. One minute earlier: in the close spreadsheet, chasing a client for a statement. | State of mind: skeptical, numerate, short on time. | Feel: accountable. | Primary action: join the waitlist with a work email.
- Material world: green columnar ledger paper, red pencil tick marks beside reconciled lines, reviewer initials and rubber stamps (RECONCILED, REVIEWED), the month-end close calendar, client binder tabs.

## Content inventory
| Section ID | Real content available | Source | Gap |
| --- | --- | --- | --- |
| `hero` | `[DRAFT]` h1 and subhead; founder background (ran ops at a 9-person firm for 4 years) | company.md `## Problem`, `## Team` | `[NEED: final hero copy from landing-page-copy]` |
| `problem` | Three problems in the founder's own words | company.md `## Problem` | None |
| `how-it-works` | No UI. Close steps are standard domain knowledge; clients shown are sample data, labelled | Domain, labelled sample | Real screenshot after pilot day 30 |
| `proof` | 2 firms agreed to a 30-day concierge pilot; 62 signups, 9 in band | company.md `## Traction` | `[NEED: pilot start date]`, `[NEED: permission to describe firms by size]` |
| `features` | Nothing built | None | Cut (T19) |
| `pricing` | $150/month appears only as the 90-day goal | company.md `## 90-day goal` | Cut. A goal is not a price; showing it would anchor pilots before they convert. Run `pricing-strategy` first |
| `faq` | The core objection ("we already pay for Karbon or TaxDome") and the alternatives | company.md `## Biggest risk`, `## Alternatives` | `[NEED: your answer to "we already pay for Karbon"]` |
| `final-cta` | The waitlist action | Brief | None |
| `footer` | Domain ledgerline.app | company.md | `[NEED: privacy policy URL]` |

## Design plan
### Palette
| Name | Hex | Role | Pairs with (contrast) |
| --- | --- | --- | --- |
| `ledger-paper` | `#F6F3EA` | Page background, cream columnar paper | Base for pairs below |
| `binder` | `#EFEBDF` | Surface: index card, board body | ink 13.35, pencil 5.30, tick-red 5.74, reconciled 6.41 |
| `rule` | `#C5D3C2` | Ledger rules, dividers; decoration only | On paper 1.41, on binder 1.31; never the only cue for a control |
| `pencil` | `#59625C` | Muted text, captions, input borders (boundary) | On paper 5.69 (passes text and 3:1 boundary) |
| `ink` | `#1B2420` | Headlines, body, focus ring; green-black ledger ink | On paper 14.34 |
| `tick-red` | `#A3341F` | The one accent: CTA fill, ticks, stamps, margin rule | Paper text on it 6.17; as text on paper 6.17 |
| `reconciled` | `#2D5C4C` | Signal: "Reconciled" state in the board, success message | On paper 6.89; UI states only |

Accent states (same hue, not new colours): `tick-press` `#8E2D1B` for hover/active (paper text 7.45); `blocked-tint` `#F2E2D8`, a pale tint of tick-red behind the blocked board row (tick-red on it 5.43, pencil 5.00, ink 12.61). Neutral ramp is the five steps paper, binder, rule, pencil, ink, all tinted toward the green-black ink. Accent jobs: CTA, the board's ticks and stamps, the margin rule. Links use ink with underline, not red. Proportion: about 80% paper, 15% ink and pencil, under 5% red. Dark mode: test fails (partners work in light spreadsheets and the brand is not dark-first), so light only. Ratios computed with the script in `color-and-motion.md`.

### Type
- Display: Libre Caslon Display 400 (Google Fonts, OFL), fallback `Georgia, "Times New Roman", serif`. Why: Caslon was the everyday face of 18th-century English and American printing; at 40 to 72px it reads as printed records, not software. One weight, thin hairlines, so 28px and up only.
- Text: IBM Plex Sans 400/600 (Google Fonts, OFL), fallback `system-ui, sans-serif`. Why: drawn for a business-machines company, plain at 16 to 17px, tabular figures for dates and counts.
- Mono: IBM Plex Mono 400 (Google Fonts, OFL), fallback `ui-monospace, Menlo, Consolas, monospace`. Board figures, client codes, stamps; reads like adding-machine tape.
- Files: 4 (Caslon 400, Plex Sans 400 and 600, Plex Mono 400), latin subset via `next/font`. Preload Caslon 400 and Plex Sans 400.
- Scale (adapted from the default, because Caslon wants a wider ratio): desktop base 17, ratio 1.333: 17 × 1.333^n = 22.7, 30.2, 40.3, 53.7, 71.6 for n = 1 to 5. Mobile base 16, ratio 1.2: 19.2, 23.0, 27.6, 33.2, 39.8. `h3` n=1, `h2` n=3, `display` n=5. `body-lg` is a half step (17 × 1.333^0.5 = 19.6; 16 × 1.2^0.5 = 17.5). Line-heights snap to 4px; desktop body leading 28px is also the ledger rule spacing. `h1` token unused (single page; the hero h1 uses `display`).

| Token | Mobile size/LH | Desktop size/LH | Tracking | Weight | Use |
| --- | --- | --- | --- | --- | --- |
| `display` | 40/44 | 72/76 | -0.02em | 400 | Hero `h1` only (Caslon; high-contrast serif, so lighter tracking than the default) |
| `h2` | 28/32 | 40/44 | -0.015em | 400 | Section `h2` (Caslon) |
| `h3` | 19/24 | 23/28 | -0.005em | 600 | FAQ questions, step titles (Plex Sans) |
| `body-lg` | 18/28 | 20/28 | 0 | 400 | Hero subhead, 52ch max |
| `body` | 16/24 | 17/28 | 0 | 400 | Paragraphs, 62ch max |
| `caption` | 13/20 | 13/20 | 0.01em | 400 | Form help, board caption |
| `figure` | 13/20 | 14/20 | 0 | 400 | Board cells, dates (Plex Mono, tabular) |
| `label` | 12/16 | 13/16 | 0.08em | 400 | Stamps and board headers only, caps (Plex Mono) |

### Grid and spacing
- Columns: 4 / 8 / 12; gutters 16 / 24 / 32px; outer margins 16 / 32 / 48px. Content max 1200px. Baseline 4px. Spacing scale 4 to 160.
- Section padding: tight 48px, default 64px mobile / 96px desktop, generous 96px / 128px (before and after the board).
- Max widths: body 62ch, subhead 52ch, h1 16ch.
- Axis: a double `tick-red` margin rule (1px lines, 3px apart) at the left of column 2 on desktop, like the money-column rules on ledger paper. Every heading and paragraph starts on it. Two left edges per screen at most.

### Density map and wireframe
| Section ID | Density | Composition | Column spans (desktop) |
| --- | --- | --- | --- |
| `hero` | Medium | Asymmetric split 7/5 | Text 2-8, index card 9-12 |
| `problem` | Medium | Index list | Numerals 2, text 3-8 |
| `how-it-works` | Dense | Specimen, the only full-bleed | Board full width, callouts 10-12 |
| `proof` | Airy | Single statement | 2-9 |
| `faq` | Medium | Hanging headline | h2 2-4, details 5-11 |
| `final-cta` | Airy | Centred block (under 25 words) | 4-9 |

```
1280px                                                       section ID
+------------------------------------------------------------+
| Ledgerline (wordmark, Caslon)     Join the waitlist (link) | header
+------------------------------------------------------------+
|    ||  h1 See which clients are blocked   +--------------+ | hero
|    ||     before close day.               | Index card:  | | cols 2-8 /
|    ||  subhead, 2 lines, 52ch             | founder note | | 9-12; rules
|    ||  Work email [______________]        | 4 yrs ops at | | every 28px
|    ||  [Join the waitlist]                | a 9-person   | | behind text
|    ||  caption [NEED: what we email]      | firm, - init | |
|    ||                                     +--------------+ |
+------------------------------------------------------------+
|    ||  h2 Close runs on a spreadsheet nobody trusts        | problem
|    ||  01  Partners can't see which clients are blocked    | index list,
|    ||  02  Deadlines slip                                  | mono numerals
|    ||  03  Reviewers redo work already reconciled          |
+------------------------------------------------------------+
| CLOSE BOARD - OCTOBER   CONCEPT. SAMPLE DATA.              | how-it-works
| Client   Bank  Cards  AP   AR   Payroll  Review    | 1 ... | full-bleed
| C-01      v     v     v    v     v       [REVIEWED]| 2 ... | specimen,
| C-04      v     v    [BLOCKED: waiting on client stmt]     | callouts
| ...6 rows                                          | 3 ... | cols 10-12
+------------------------------------------------------------+
|    ||  Pilots with 2 bookkeeping firms start [NEED: date]  | proof
|    ||  [NEED: pilot result, with permission, after day 30] | airy
+------------------------------------------------------------+
|    ||  h2 Questions     | 4 details rows                   | faq
|    ||  partners ask     |                                  | hanging
+------------------------------------------------------------+
|         Your next close, on one page. [Join the waitlist]  | final-cta
+------------------------------------------------------------+
| Privacy [NEED: URL]   Contact   (c) Ledgerline             | footer
+------------------------------------------------------------+
```
All wireframe copy is `[DRAFT]`. Mobile (375px): margin rule becomes a single 1px rule at 16px; index card stacks below the form; board scrolls horizontally inside a labelled region with the Client column sticky.

### Signature moment
The close board in `how-it-works`. A real `<table>` set on ruled paper: 6 sample clients by 6 close steps. When 40% of it is visible, red ticks draw across each row, row C-04 stops at AP and takes a tilted BLOCKED stamp ("Waiting on client: card statement"), then a REVIEWED stamp lands by the reviewer initials on C-01. Header line: "5 of 6 clients ready for review. 1 blocked." Cells carry visually hidden text ("Done", "Blocked", "Not started"); ticks are `aria-hidden`. Caption: "Concept. Sample data. Not a product screen yet."

| Test | Result |
| --- | --- |
| Recognition | A bookkeeper names it as a close checklist with copy hidden: pass |
| Explanation | It shows the product's core claim (see who is blocked) in one picture: pass |
| Removal | Without it the page has no product at all: pass |
| Still state | Final state shows all ticks, both stamps, and the header line: pass |
| Swap | On Karbon's or TaxDome's page it would read as a feature, not the product: pass |

### Imagery and icons
- Raster images: none. Index card and board are HTML and CSS; the stamps are text in Plex Mono with a CSS border, rotated 4 degrees.
- Icons: none decorative. Ticks are status content with text alternatives. One functional marker: the FAQ plus/minus, drawn in CSS, `aria-hidden` (the native `summary` announces state).

### Motion
| Element | Property | Duration | Easing | Reduced motion |
| --- | --- | --- | --- | --- |
| Board ticks, per row | `transform: scaleX(0)` to `scaleX(1)`, origin left | 240ms, rows staggered 90ms | `cubic-bezier(0.2, 0, 0, 1)` | Final state shown |
| Stamps | opacity 0 to 1, scale 1.08 to 1 | 220ms, starting at 760ms and 900ms | `cubic-bezier(0.16, 1, 0.3, 1)` | Static, visible |
| CTA | background-color | 150ms | `cubic-bezier(0.25, 1, 0.5, 1)` | Unchanged |

Board sequence: last tick row starts at 5 × 90 = 450ms and ends at 690ms; the second stamp ends at 900 + 220 = 1120ms. Inside the 600 to 1200ms signature budget, runs once. Nothing else moves; the hero h1 is never animated (LCP).

### Revisions after self-review
- Contrast: accent `#D9483B` (brighter pencil red) gave paper text 3.83, failing 4.5:1 for a 17px label -> darkened to `#A3341F` (6.17); the bright red is dropped, not kept for fills.
- Contrast: input border used `rule` (1.41, fails 3:1 for a control) -> inputs use `pencil` (5.69).
- T18: hero draft had a tilted dashboard mockup -> removed; founder note card in the hero, board moved to `how-it-works` with the Concept label.
- Squint: header CTA was a second filled button in the first viewport -> quiet text link to the hero form.
- T14: stamp-style caps spread into eyebrows over each `h2` -> caps live only in stamps and board headers.
- T6 and T7: `problem` drafted as 3 icon cards -> index list with mono numerals.
- T12 / honesty: `proof` draft showed "62 on the waitlist" -> cut; only 9 are in-band firms and a partner reads 62 as small. The pilot statement carries more weight.
- Material overuse: ledger rules covered the whole page -> hero and board only, so they read as material, not wallpaper.
- Swap test with Karbon's logo: 5 elements would be wrong (Caslon records type, ledger margin axis, tick-red from pencil ticks, the blocked-client board, close-day vocabulary): pass. Squint: hero reads as h1 plus form, board reads as the stamped row: pass.

## Build (planned)
- Stack: `[ASSUMPTION]` Next.js + Tailwind v4; the open repo is not ledgerline.app's, so `[NEED: framework/host for ledgerline.app]`.
- Files to create on approval: `app/fonts.ts`, `app/globals.css`, `components/Section.tsx`, `components/WaitlistForm.tsx`, `components/CloseBoard.tsx`, `components/IndexCard.tsx`, `app/page.tsx`. Dependencies added: none (`next/font`, native IntersectionObserver).
- Token layer (`app/globals.css`, first file written):

```css
@import "tailwindcss";

@theme {
  --color-paper: #F6F3EA;       /* ledger-paper */
  --color-binder: #EFEBDF;      /* surface */
  --color-rule: #C5D3C2;        /* 1.41:1; decoration only */
  --color-pencil: #59625C;      /* 5.69:1; muted text and input borders */
  --color-ink: #1B2420;         /* 14.34:1 on paper */
  --color-tick: #A3341F;        /* paper text on it 6.17:1 */
  --color-tick-press: #8E2D1B;  /* hover/active, 7.45:1 */
  --color-blocked-tint: #F2E2D8;/* tick-red on it 5.43:1 */
  --color-reconciled: #2D5C4C;  /* 6.89:1 on paper; UI states only */
  --radius-sm: 2px;
  --container-content: 1200px;
  --container-measure: 62ch;
}
@theme inline {
  --font-display: var(--font-caslon), Georgia, serif;
  --font-text: var(--font-plex-sans), ui-sans-serif, system-ui, sans-serif;
  --font-mono: var(--font-plex-mono), ui-monospace, monospace;
}
:root {
  --text-display: clamp(2.5rem, 1.671rem + 3.536vw, 4.5rem);   /* 40px @375 -> 72px @1280 */
  --text-h2: clamp(1.75rem, 1.439rem + 1.326vw, 2.5rem);       /* 28px -> 40px */
  --text-body: 1rem;  --leading-body: 1.5;  --rule-gap: 24px;
  --section-default: 64px;  --section-generous: 96px;
  --ease-standard: cubic-bezier(0.2, 0, 0, 1);
  --ease-emphasized: cubic-bezier(0.16, 1, 0.3, 1);
}
@media (min-width: 768px) {
  :root { --text-body: 1.0625rem; --leading-body: 1.647; --rule-gap: 28px;
          --section-default: 96px; --section-generous: 128px; }
}
.ledger-rules { /* hard-stop 1px rules at the body leading; texture, not a gradient wash */
  background-image: repeating-linear-gradient(to bottom, transparent 0 calc(var(--rule-gap) - 1px),
    var(--color-rule) calc(var(--rule-gap) - 1px) var(--rule-gap));
}
```
- Open placeholders: `[NEED: hero copy]`, `[NEED: pilot start date]`, `[NEED: permission to describe pilot firms]`, `[NEED: answer to "we already pay for Karbon"]`, `[NEED: privacy policy URL]`.

Pre-ship critique runs after the build; plan-level checks are in Revisions above.

## Next step
Approve or change this plan by 2026-10-22, and run `landing-page-copy` for the hero the same day. I build on approval so the page is live before the pilot kickoff emails link to it `[ASSUMPTION: pilots start 2026-10-26]`. Logged to `.foundora/journal.md`:

```markdown
### 2026-10-20 — decision: Waitlist page visual direction
- Ledger-paper direction: Libre Caslon Display + IBM Plex Sans/Mono, accent tick-red #A3341F (6.17:1 with paper text)
- Signature moment: close board in how-it-works, labelled Concept until pilot UI exists; features and pricing sections cut
- Plan only; critique pending build
- Revisit: replace the concept board with a real screenshot after pilot day 30
- Source: website-design
```

---

## Turn 2

**Request:** "Approved. Repo is ledgerline-site, hero copy from landing-page-copy is in content/hero.md. Build it."

## Direction
Built to the approved plan with the new hero copy. The design scores 18/30 on the first pass and 28/30 after fixes, but the verdict is DO NOT SHIP: the waitlist form has nowhere to send emails yet and three `[NEED]` markers are still visible. Both are your inputs, listed under Next step.

## Build
- Stack detected: `next` in `package.json` with an `app/` directory (App Router); `@import "tailwindcss"` in `app/globals.css` (Tailwind v4). `lucide-react` is in `package.json` from the starter; the new page does not import it.
- Files created/changed: `app/fonts.ts`, `app/globals.css` (starter tokens replaced), `app/layout.tsx` (fonts, metadata), `app/page.tsx`, `components/Section.tsx`, `components/WaitlistForm.tsx`, `components/CloseBoard.tsx`, `components/IndexCard.tsx`, `app/opengraph-image.tsx` (Caslon headline on ledger paper via `next/og`). Dependencies added: none.
- Board: `<table>` with `<caption>`, `th scope="col"` for the six steps, `th scope="row"` for client codes, sr-only status text in every cell, ticks and stamps `aria-hidden`. Final state is the default CSS; the script adds `is-armed` only when JavaScript runs and reduced motion is off:

```css
.board.is-armed .tick { transform: scaleX(0); transform-origin: left; }
.board.is-playing .tick {
  transform: scaleX(1);
  transition: transform 240ms var(--ease-standard);
  transition-delay: calc(var(--row) * 90ms);
}
.board.is-armed .stamp { opacity: 0; transform: rotate(-4deg) scale(1.08); }
.board.is-playing .stamp {
  opacity: 1; transform: rotate(-4deg) scale(1);
  transition: opacity 220ms var(--ease-emphasized), transform 220ms var(--ease-emphasized);
  transition-delay: var(--stamp-delay); /* 760ms, 900ms */
}
```

- Form: a server action validates the email server-side and forwards it to `[NEED: current waitlist provider and endpoint]`, so the 62 existing signups stay in one list. Rate limit `[ASSUMPTION: 5 requests per minute per IP]`.
- Metadata: title "Ledgerline: month-end close tracking for bookkeeping firms" (58 characters), description from `content/hero.md`, canonical `/`, `noindex` on the preview only.
- Open placeholders still visible: `[NEED: pilot start date]`, `[NEED: answer to "we already pay for Karbon"]`, `[NEED: privacy policy URL]`.

## Pre-ship critique
Screenshots taken with the browser tool on the local dev server at 320, 375, 768, 1280, and 1440px. No deployed preview yet, so Lighthouse was not run.

### Blockers
| ID | Result | Evidence |
| --- | --- | --- |
| B1 No invented proof | Pass | Only the founder-provided pilot statement; sample board labelled "Concept. Sample data." |
| B2 Contrast | Pass after fix | First pass failed: see A5 |
| B3 Keyboard and focus | Pass after fix | First pass failed: board scroll region unreachable on mobile, see A7 |
| B4 Primary CTA works end to end | Fail | Success and error states render with a stubbed action; real endpoint is `[NEED]` |
| B5 No horizontal scroll | Pass | 320 to 1440 checked; board scrolls inside its region |
| B6 One h1, ordered headings | Pass | h1, then h2 per section, h3 in FAQ |
| B7 Reduced motion | Pass | With reduce set, board renders final state; no transitions |
| B8 No visible markers on a public URL | Fail until filled | Three `[NEED]`s visible; fine on the preview, blocks production |

### Audits
| Audit | Result | Evidence / fix applied |
| --- | --- | --- |
| A1 Squint | Pass after fix | At 1280 the index card (2px tick-red border, rotated 1 degree) competed with the h1 -> 1px `rule` border, no rotation. Now one dominant element per screen; CTA found first on hero and final CTA |
| A2 Swap | Pass | Same 5 specific elements as the plan, all present in the build |
| A3 Tell scan | Pass after fix | Code scan found `rounded-2xl` on the index card (T9) and a `lucide-react` `ArrowRight` on the hero button (T16), both pasted from the starter -> `rounded-sm` token, arrow removed |
| A4 Icon audit | Pass after fix | Arrow removed; inventory is now one functional FAQ marker (CSS, `aria-hidden`). Ticks and stamps are status content with text alternatives |
| A5 Contrast | Pass after fix | Build added a `pencil-light` `#8A938C` for "not started" cells: 2.66 on binder, fails 4.5:1 -> token deleted; those cells use `pencil` (5.30 on binder) with an en dash and sr-only "Not started". All 14 rendered pairs now pass, lowest is pencil on blocked-tint at 5.00 |
| A6 Mobile 375 | Pass after fix | h1 in 4 lines; CTA above the fold at 375x667; inputs 16px. Failed row: board region had no focus or hint -> `role="region"`, `aria-labelledby`, `tabindex="0"`, visible "Scroll for all 6 steps" below 768px |
| A7 Keyboard | Pass after fix | Board region now focusable and scrolls with arrow keys; skip link first; FAQ opens with Enter and Space; focus ring ink on paper 14.34 |
| A8 Performance | Not verified | Static checks pass: 4 font files, 2 preloads, LCP element is the h1 text and is not animated, no raster images above the fold, no effect library. Lighthouse needs a deployed preview |
| A9 Content | Pass, with markers | No lorem; every number traces to company.md; button reads "Join the waitlist"; error and success states have real words; 3 `[NEED]`s listed above |

### Scorecard
| Dimension | First pass | Final | Evidence / fix |
| --- | --- | --- | --- |
| Distinctiveness | 1 | 3 | Capped at 1 by unjustified T9 and T16; both removed; signature passes all five tests |
| Hierarchy | 2 | 3 | Index card toned down; squint passes at every width |
| Typography | 3 | 3 | Scale, tracking, measure, tabular figures as planned |
| Colour | 0 | 3 | `pencil-light` contrast failure removed; all pairs recorded |
| Layout and rhythm | 3 | 3 | Density map followed; 2 left edges per screen |
| Imagery and icons | 1 | 3 | Decorative arrow removed; board labelled as concept |
| Motion | 3 | 3 | Ticks use `transform` only; sequence 1120ms, once; still state designed |
| Mobile | 2 | 3 | Board region fixed; all A6 rows pass |
| Accessibility | 1 | 2 | First pass: axe flagged the board's scroll region (`scrollable-region-focusable`) and the keyboard audit failed on it. Final: axe clean, keyboard audit passes; screen reader pass on the board not run (no screen reader in this environment), so capped at 2 |
| Performance and build hygiene | 2 | 2 | Static checks only, not measured: capped at 2 |

- Screenshots: taken at 320/375/768/1280/1440.
- Total: 18/30 -> 28/30 (threshold 24, none under 2). Verdict: DO NOT SHIP, because B4 (no waitlist endpoint) and B8 (visible `[NEED]`s) fail. Once both close, the verdict becomes SHIP AFTER FOUNDER CHECKS: run PageSpeed Insights on the preview (pass: LCP 2.5s or less, CLS 0.1 or less) and a VoiceOver or NVDA pass on the board (pass: each row reads client, step, and status).

## Next step
Send me three things by 2026-10-23: the current waitlist provider and endpoint, the pilot start date, and a privacy policy URL. Your answer to "we already pay for Karbon" can wait; I will cut that FAQ item rather than ship a placeholder. I wire them in the same day so the page is live before the pilot kickoff emails `[ASSUMPTION: 2026-10-26]`. Logged to `.foundora/journal.md`:

```markdown
### 2026-10-21 — review: Waitlist page pre-ship critique
- Score 18/30 first pass -> 28/30 after fixes (T9, T16, pencil-light contrast, board scroll region, index card weight)
- Verdict DO NOT SHIP: B4 waitlist endpoint and B8 visible [NEED]s depend on founder inputs
- Not verified: PageSpeed on preview, screen reader pass on the board
- Revisit: 2026-10-23, once the three inputs arrive; ship before pilot kickoff
- Source: website-design
```
