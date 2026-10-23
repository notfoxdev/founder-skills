# Worked example: website-design

> Illustrative and fictional (Ledgerline fixture). Calibrates depth and format only; never reuse its content.

**Request:** "Design our waitlist landing page."

**Context used:** `evals/fixture-company.md` as `.foundora/company.md`. Validation stage, waitlist page only, 62 signups (9 in the target size band), 2 free concierge pilots start next week, no revenue, no product UI. Buyer is the managing partner; ops leads and bookkeepers use it daily. Tone: direct, tables over paragraphs, US spelling. No brand assets, no copy, no repo, so: Plan mode, copy marked `[DRAFT]`, stack `[ASSUMPTION]` Next.js + Tailwind v4. Hard parts shown: no UI exists (concept label), no proof (stage statement plus `[NEED]`), first accent failed contrast.

---

## Direction
Make the page look like a well-kept close binder, not a SaaS site: cream columnar paper, green ledger rules, red pencil ticks, and one close board where ticks land row by row and a blocked client gets stamped. The board is the only bold moment and is labelled "Concept" because the pilots run concierge and no UI exists; a dashboard mockup in the hero is the first thing a skeptical partner would test, so there is none. Before build I need `[NEED: final hero copy from landing-page-copy]` and `[NEED: OK to describe the 2 pilot firms by size, unnamed]`. Scope: the page is not your bottleneck this month, the pilots are, so this is one short scroll (no pricing or features sections) that two days of work can ship; its job is to catch partners arriving from your LinkedIn post and pilot referrals.

## Design brief
- Audience: managing partner or ops lead at a 3–15 person bookkeeping firm, arriving from the founder's LinkedIn post. One minute earlier: in the close spreadsheet, chasing a client for a statement. | State of mind: skeptical, numerate, short on time. | Feel: accountable. | Primary action: join the waitlist with a work email.
- Material world: green columnar ledger paper, red pencil tick marks beside reconciled lines, reviewer initials and rubber stamps (RECONCILED, REVIEWED), the month-end close calendar, client binder tabs.

## Design plan
### Palette
| Name | Hex | Role | Pairs with (contrast) |
| --- | --- | --- | --- |
| `ledger-paper` | `#F6F3EA` | Page background, cream columnar paper | base for all pairs below |
| `ink` | `#1B2420` | Headlines, body, focus ring; green-black ledger ink | on paper 14.34:1 |
| `pencil` | `#59625C` | Captions, secondary text, input borders | on paper 5.69:1 (text and 3:1 boundary) |
| `rule` | `#C5D3C2` | Ledger rules and dividers, decoration only | on paper 1.41:1, never the only cue for a control |
| `tick-red` | `#A3341F` | CTA fill, tick marks, stamps, margin rule | paper text on it 6.17:1; as text on paper 6.17:1 |
| `reconciled` | `#2D5C4C` | "Reconciled" state in the board, success messages | on paper 6.89:1 |

Hover/active state for the CTA: `#8E2D1B` (paper text 7.45:1), a state of `tick-red`, not a seventh colour. Proportion: about 80% paper, 15% ink and pencil, under 5% red. Ratios computed with the WCAG script in `color-and-motion.md`.

### Type
- Display: Libre Caslon Display 400 (Google Fonts). Why: Caslon was the everyday face of 18th-century English and American printing; at 40–72px it reads as printed records, not software. Display only, never below 28px, where its hairlines thin out.
- Text: IBM Plex Sans 400/600 (Google Fonts). Why: drawn for a business-machines company, plain at 16–17px, tabular figures for dates and counts.
- Mono: IBM Plex Mono 400 (Google Fonts). Board figures, dates, client codes, stamps; reads like adding-machine tape.
- Files: 4 (Caslon 400, Plex Sans 400 and 600, Plex Mono 400). Preload Caslon 400 and Plex Sans 400.
- Scale: desktop base 17, ratio 1.333 (17 × 1.333^n = 22.7, 30.2, 40.3, 53.7, 71.5 for n = 1–5); mobile base 16, ratio 1.2 (19.2, 23.0, 27.6, 33.2, 39.8). Title n=1, headline n=3, display n=5. Body-lg is a half step (17 × 1.333^0.5 = 19.6; 16 × 1.2^0.5 = 17.5). Leading snaps to 4px; desktop body leading 28px is also the ledger rule spacing.

| Token | Mobile size/LH | Desktop size/LH | Tracking | Weight | Use |
| --- | --- | --- | --- | --- | --- |
| `display` | 40/44 | 72/76 | -0.02em | 400 | `h1` only (Caslon) |
| `headline` | 28/32 | 40/44 | -0.015em | 400 | Section `h2` (Caslon) |
| `title` | 19/24 | 23/28 | -0.005em | 600 | `h3`, FAQ questions (Plex Sans) |
| `body-lg` | 18/26 | 20/28 | 0 | 400 | Hero subhead, 52ch max |
| `body` | 16/26 | 17/28 | 0 | 400 | Paragraphs, 62ch max |
| `caption` | 13/20 | 13/20 | 0.01em | 400 | Form help, board caption |
| `figure` | 13/20 | 14/20 | 0 | 400 | Board cells, dates (Plex Mono, tabular) |
| `stamp` | 12/16 | 13/16 | 0.08em | 400 | Stamps and board headers only, caps |

### Spacing and layout
- Base 4px. Section padding: tight 48px, default 64px mobile / 96px desktop, generous 96px / 128px (before and after the board). Max widths: text 62ch, content 1200px.
- Grid: 12 columns, 32px gutter desktop; 4 columns, 16px gutter mobile. Alignment axis: a double `tick-red` margin rule (1px, 3px apart) at the left of column 2 on desktop, like the money-column rules on ledger paper. Every heading and paragraph starts on it. Two left edges per screen at most.

```
1280px                                                       section ID
+------------------------------------------------------------+
| Ledgerline (wordmark, Caslon)     Join the waitlist (link) | header
+------------------------------------------------------------+
|    ||  h1 See which clients are blocked   +--------------+ | hero
|    ||     before close day.               | Index card:  | | 7/5 split
|    ||  subhead, 2 lines, 52ch             | founder note | | rules every
|    ||  Work email [______________]        | 4 yrs ops at | | 28px behind
|    ||  [Join the waitlist]                | a 9-person   | | the text
|    ||  caption [NEED: what we email]      | firm, - init | |
|    ||                                     +--------------+ |
+------------------------------------------------------------+
|    ||  h2 Close runs on a spreadsheet nobody trusts        | problem
|    ||  01  Partners can't see which clients are blocked    | ruled lines,
|    ||  02  Deadlines slip                                  | mono numerals
|    ||  03  Reviewers redo work already reconciled          |
+------------------------------------------------------------+
| CLOSE BOARD - OCTOBER   CONCEPT. SAMPLE DATA.              | how-it-works
| Client   Bank  Cards  AP   AR   Payroll  Review            | full-bleed
| C-01      v     v     v    v     v       [REVIEWED]        | (the only
| C-04      v     v    [BLOCKED: waiting on client stmt]     | full-bleed
| ...6 rows; callouts 1-2-3 in the right margin              | element)
+------------------------------------------------------------+
|    ||  Pilots with 2 bookkeeping firms start [NEED: date]  | proof
|    ||  [NEED: pilot result, with permission, after day 30] |
+------------------------------------------------------------+
|    ||  h2 Questions partners ask        (4 details rows)   | faq
+------------------------------------------------------------+
|         Your next close, on one page. [Join the waitlist]  | final-cta
+------------------------------------------------------------+
| Privacy [NEED: URL]   Contact   (c) Ledgerline             | footer
+------------------------------------------------------------+
```
All wireframe copy is `[DRAFT]`. Mobile (375px): margin rule becomes a single 1px rule at 16px; index card stacks below the form; board scrolls horizontally inside a labelled region with the Client column sticky.

### Signature moment
The close board in `how-it-works`. A real `<table>` set on ruled paper: 6 sample clients by 6 close steps. When 40% of it is visible, red ticks draw across each row, row C-04 stops at AP and takes a tilted BLOCKED stamp ("Waiting on client: card statement"), then a REVIEWED stamp lands by the reviewer initials on C-01. Header line: "5 of 6 clients ready for review. 1 blocked." It answers your core problem (partners can't see who is blocked) in one picture. Cells carry visually hidden text ("Done", "Blocked"); ticks are `aria-hidden`. Reduced motion: final state, no drop. Caption: "Concept. Sample data. Not a product screen yet."

### Motion
| Element | Property | Duration | Easing | Reduced motion |
| --- | --- | --- | --- | --- |
| Board ticks, per row | `clip-path: inset(0 100% 0 0)` to `inset(0)` | 240ms, rows staggered 90ms | `cubic-bezier(0.2, 0, 0, 1)` | Final state shown |
| Stamps | opacity 0 to 1, scale 1.08 to 1 | 220ms at 760ms and 900ms | `cubic-bezier(0.16, 1, 0.3, 1)` | Static |
| CTA | background-color | 120ms | `ease-out` | Unchanged |

Total board sequence about 1.1s, runs once. Nothing else moves.

### Revisions after self-review
- Accent `#D9483B` (brighter pencil red): paper text 3.83:1, fails 4.5:1 for a 17px label -> darkened to `#A3341F` (6.17:1); the bright red is dropped, not kept for fills.
- Input border used `rule` (1.41:1, fails 3:1 for a control) -> inputs use `pencil` (5.69:1).
- Hero draft had a tilted dashboard mockup -> removed: no UI exists (banned tell). Founder note card in the hero; board moved to `how-it-works` with the Concept label.
- Header CTA was a second filled button in the first viewport -> quiet text link to the hero form.
- Ledger rules covered the whole page -> limited to hero and board, so they read as material, not wallpaper.
- Stamp style spread into caps eyebrows over each `h2` -> caps live only in stamps and board headers.
- `problem` drafted as 3 icon cards -> 3 ruled lines with mono numerals.
- `proof` draft showed "62 on the waitlist" -> cut: only 9 are in-band firms and a partner reads 62 as small; the pilot statement carries more weight.
- Swap test: with Karbon's logo the Caslon headline, ledger axis, and blocked-client board fit a broad practice suite poorly; pass. Squint test: hero reads as `h1` + form, board reads as the stamped row; pass.

## Build (planned)
- Stack: `[ASSUMPTION]` Next.js + Tailwind v4; the open repo is not ledgerline.app's, so `[NEED: framework/host for ledgerline.app]`.
- Files to create on approval: `app/fonts.ts`, `app/globals.css`, `components/Section.tsx`, `components/WaitlistForm.tsx`, `components/CloseBoard.tsx`, `app/page.tsx`. Dependencies added: none (`next/font`, native IntersectionObserver).
- Token layer (`app/globals.css`, first file written):

```css
@import "tailwindcss";

@theme {
  --color-paper: #F6F3EA;       /* ledger-paper */
  --color-ink: #1B2420;         /* 14.34:1 on paper */
  --color-pencil: #59625C;      /* 5.69:1; text and input borders */
  --color-rule: #C5D3C2;        /* 1.41:1; decoration only */
  --color-tick: #A3341F;        /* paper text on it 6.17:1 */
  --color-tick-press: #8E2D1B;  /* hover/active, 7.45:1 */
  --color-reconciled: #2D5C4C;  /* 6.89:1 on paper */
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
  --text-headline: clamp(1.75rem, 1.439rem + 1.326vw, 2.5rem); /* 28px -> 40px */
  --text-body: 1rem;  --leading-body: 1.625;  --rule-gap: 26px;
  --section-default: 64px;  --section-generous: 96px;
  --ease-standard: cubic-bezier(0.2, 0, 0, 1);
  --ease-emphasized: cubic-bezier(0.16, 1, 0.3, 1);
}
@media (min-width: 768px) {
  :root { --text-body: 1.0625rem; --leading-body: 1.647; --rule-gap: 28px;
          --section-default: 96px; --section-generous: 128px; }
}
.ledger-rules { /* hard-stop 1px rules, spacing = body leading; not a gradient wash */
  background-image: repeating-linear-gradient(to bottom, transparent 0 calc(var(--rule-gap) - 1px),
    var(--color-rule) calc(var(--rule-gap) - 1px) var(--rule-gap));
}
```
- Open placeholders: `[NEED: hero copy]`, `[NEED: pilot start date]`, `[NEED: permission to describe pilot firms]`, `[NEED: answer to "we already pay for Karbon"]`, `[NEED: privacy policy URL]`.

Pre-ship critique runs after the build (checklist plus screenshots at 375/768/1280/1440); plan-level checks are in Revisions above.

## Next step
Approve or change this plan by 2026-10-22, and run `landing-page-copy` for the hero the same day. I build on approval so the page is live before the pilot kickoff emails link to it `[ASSUMPTION: pilots start 2026-10-26]`. Logged to `.foundora/journal.md`:

```markdown
### 2026-10-20 — decision: Waitlist page visual direction
- Ledger-paper direction: Libre Caslon Display + IBM Plex Sans/Mono, accent tick-red #A3341F (6.17:1 with paper text)
- Signature moment: close board in how-it-works, labelled Concept until pilot UI exists
- Revisit: replace the concept board with a real screenshot after pilot day 30
- Source: website-design
```
