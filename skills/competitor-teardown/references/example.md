# Worked example (illustrative, fictional)

> Uses the fictional Ledgerline fixture (`evals/fixture-company.md`). It calibrates depth, tone and format only. Never copy its content, claims or wording into a real answer.

## Request

"Tear down Karbon and the Sheets checklist before the pilots start. Honestly Karbon is clunky and everyone hates it. I want a battlecard and a 'Karbon alternative' page for the site."

## Context used

- `.foundora/company.md`: the Ledgerline fixture. Alternatives listed: Google Sheets close checklists, Karbon and TaxDome workflow templates, doing nothing. Biggest risk: will firms pay separately for close tracking, or will practice tools add it. Founder ran ops at a 9-person bookkeeping firm for 4 years. Site is a waitlist page. Working preferences: direct, tables over paragraphs, US spelling.
- `.foundora/journal.md`: not present. Raw interview notes: not pasted, so only the founder's summary of 11 interviews in `## Problem` is available.
- No web search or fetch tools in this session. Every fact about Karbon is a `[NEED]` with the page to check.
- Date: 2026-10-23. TaxDome is left out at the founder's request (cap of 3 targets, Karbon named).
- Hard parts shown: pushback on "everyone hates it", a "no proven win yet" verdict, the incumbent risk stated honestly, and a public page held back.

## Model answer

# Competitor teardown — Karbon, Sheets close checklist, do nothing — 2026-10-23

**Verdict:** I can't tell you yet whether your real rival is Karbon or the spreadsheet, and that's the first thing to fix. Where we win: no proven win yet. Don't fight: Karbon as the firm's practice hub, the tool partners already pay for and run all their work through (company.md).
**What we understand that they don't:** "Close status lives at the reconciliation, not the task" (founder's hypothesis from 4 years running ops at a 9-person firm) — `[ASSUMPTION]` until 2 independent firms describe it unprompted.
**Evidence mode:** no web tools this session. Karbon facts below are a research plan, not findings.

On "Karbon is clunky, everyone hates it": the strongest version of Karbon's case is that firms chose it, pay for it every month and run their whole practice in it. Your interview summary says partners can't see which clients are blocked. It doesn't say they hate Karbon. So that stays a **Hunch**. Cheapest test: ask the next three Karbon users "If Karbon disappeared tomorrow, what would you miss first?" If two of three name close, you've found a strength, not a weakness.

## Targets

| Alternative | Who uses it today (n of N, source) | In or out | Why |
|---|---|---|---|
| Google Sheets close checklist | [NEED: n of 11 interviewees] | In | Listed first in company.md; free and already open |
| Karbon workflow templates | [NEED: n of 11; and whether either pilot firm uses Karbon] | In | Named in the biggest risk |
| Do nothing | [NEED: n of 11] | In, short row | Cost of slipped deadlines and redone review |
| TaxDome | [NEED] | Out for now | Founder asked for Karbon; same questions apply next round |

## Google Sheets close checklist

**Hired for:** "Give me one place to tick off each client's close." Free, already open, everyone at the firm knows it, and it bends to any process.
| Strengths (fair) | Evidence |
|---|---|
| Costs nothing extra and needs no training | Reasoning; [NEED: confirm in notes] |
| Fits whatever columns the firm wants | Reasoning; [NEED: example sheet from a pilot firm] |

| Where it hurts | Strength | Sources |
|---|---|---|
| Partners can't see which clients are blocked | Signal | company.md summary of 11 interviews (counts once until raw notes give n of 11) |
| Reviewers redo work because nobody knows what was reconciled | Signal | Same summary |

**Switching cost:** Low (habit). They give up a sheet they control. We lower it by importing their sheet and setting up the first close with them.

## Karbon

**Hired for:** [NEED: in an interviewee's words]. **Built for (their words):** [NEED: homepage headline, Karbon's homepage, checked on date].
| Strengths (fair) | Evidence |
|---|---|
| Already the firm's practice tool, paid for | company.md Target customer |
| Has workflow templates firms use for close | company.md Alternatives |
| [NEED: what Karbon users would miss, from 3 conversations] | Test below |

| Where it hurts | Strength | Sources |
|---|---|---|
| "Clunky, everyone hates it" | Hunch `[ASSUMPTION]` | Founder belief only |

| Pricing as listed | Plan / price / period | Source |
|---|---|---|
| [NEED: plan names and per-user price] | [NEED] | Karbon's public pricing page, checked on [date] |

**What our buyer would pay:** a firm with n staff on a per-user price P pays n × P a month. At 9 staff (your old firm's size) that's 9P, and Ledgerline at $150/month makes it 9P + $150. Fill in P before the day-30 conversion talk, because "is $150 small next to what we pay Karbon?" is the question partners will ask.
**Switching cost:** we aren't asking anyone to leave Karbon. The real cost is paying twice and keeping two tools in step (workflow). That's harder to sell than a switch, and it's exactly your biggest risk.
**Next likely build:** close tracking inside templates — **Unknown**. No signals checked yet; see research plan.
**If they ship it:** firms that run close in Karbon would have far less reason to pay you $150 on top. What's left is firms running close in a sheet, firms on tools without close templates, and reconciliation-level detail, but only if your hypothesis holds. If both pilot firms turn out to be Karbon users happy with a template, the biggest risk is live, and that's worth knowing in week one, not month seven.

## Do nothing

Cost: [NEED: hours chasing status and redone reviews last month, from interviews]. Without that number, "do nothing" wins by default.

## Where to win

| Claim | Sources (independent) | Segment match | On don't-fight or Likely build? | Call |
|---|---|---|---|---|
| Partners see blocked clients without asking | 1 (founder summary) | Yes | Unknown | Test |
| Reviewers stop redoing reconciled work | 1 (founder summary) | Yes | Unknown | Test |
| Runs alongside Karbon without double entry | 0 (Hunch) | n/a | Unknown | Test |

Nothing reaches Win: each row needs two firms saying it, from raw notes or pilots. Two partners at one firm count once.

## Tests for the next three conversations

1. "Where did you track close last month? Can you show me?" (Sheets vs Karbon count)
2. "Which client was hardest to close last month, and when did the partner find out?"
3. "Have you tried running close in Karbon's templates? What happened?"
4. "If Karbon disappeared tomorrow, what would you miss first?"

## Research plan

| Fact | Page to check | Due | By |
|---|---|---|---|
| Plans and per-user prices | Karbon pricing page | 2026-10-26 | Founder |
| Close or checklist features shipped in the last 12 months | Karbon changelog or release notes | 2026-10-26 | Priya |
| Open requests about close status | Karbon community or feature-request board | 2026-10-26 | Priya |
| Hiring in workflow or close areas | Karbon careers page, with post dates | 2026-10-26 | Founder |
| Praise and complaints from 3–15 staff firms | Review sites and practitioner forums (see `references/review-mining.md`) | 2026-10-30 | Founder |

# Battlecard — us vs Karbon — DRAFT, checked 2026-10-23, re-check by 2026-11-06

**When they come up:** "We already pay for Karbon," usually when price comes up.
| They're strong at (said fairly) | Our answer | Ask the buyer |
|---|---|---|
| Running the whole practice in one place | Hold: no Win row yet | "Where does close status live today, Karbon or a sheet?" |
| Templates you can shape to your firm | Hold: Test row 1 | "Last month, how did you find out a client was blocked?" |

**If they say "we already pay for Karbon":** "Keep it. We only do close, and the pilot is there to find out whether that's worth a separate line for your firm."
**When to walk away:** a firm that already runs close in Karbon templates and whose partner can see who's blocked without asking.

# Page outline — "Karbon alternative" — hold until the product is live, one row is Win, and every Karbon claim is checked and dated

I'd hold this page. You have a waitlist and no product, and Karbon's team will read a comparison page before most buyers do. If the counts show most firms run close in a sheet, the first public page should be "why change from the close spreadsheet", not "Karbon alternative". Draft both through `seo-content` once a Win row exists.

Logged to `.foundora/journal.md` (created with a `# Ledgerline journal` heading):

```markdown
### 2026-10-23 — decision: Where we win against Karbon
- Call: Test on all three claims; no proven win yet
- Evidence: founder summary of 11 interviews (counts once); "everyone hates Karbon" is a Hunch
- Incumbent risk: Karbon close tracking in templates, Unknown; if it ships, firms on Karbon lose the reason to pay $150 on top
- Re-check: research plan due 2026-10-26; four test questions in the next 3 conversations; battlecard re-check 2026-11-06
- Source: competitor-teardown
```
