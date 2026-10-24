# Worked example: mvp-scoper

> Illustrative and fictional (Ledgerline fixture). Calibrates depth and format only; never reuse its content.

## Request

"We're about to build integrations with QBO and Xero. Scope the MVP."

## Context used

- `.foundora/company.md`: the Ledgerline fixture (`evals/fixture-company.md`). Working preferences: direct, tables over paragraphs, US spelling.
- `.foundora/journal.md`: not present, so no idea-validator scores to reuse. 11 discovery interviews clears the "too early for an MVP" floor of 5.
- Date: Friday 2026-10-23. The plan runs Monday 2026-10-26 to Friday 2026-10-30.
- No question asked first: hours and budget are covered by company.md (both founders full-time, no acquisition budget). Pilot kickoff dates are missing and marked `[NEED]`.

## Model answer

# MVP scope — Ledgerline — 2026-10-23

**Riskiest assumption:** We believe managing partners at bookkeeping firms with 3–15 staff will pay at least $150/month for close tracking, separate from Karbon or TaxDome.
**Test:** Paid concierge pilot. You run each firm's close board by hand for 30 days, with $150/month conversion terms agreed at kickoff.
**90/10 version:** A shared close board per firm that you keep current, plus a Friday email to the partner listing blocked clients. No sync, no logins.
**Instead of:** QBO and Xero integrations. The strongest case for them: firms won't take a close tool seriously if status is typed in by hand. The objection: an integration answers "can we build it", and your biggest risk is "will they pay separately". Two pilot firms can be updated by hand, so neither needs a sync to answer that. Integrations move to Later with a trigger.
**Live with real users by:** 2026-10-27 (day 2) [NEED: actual kickoff dates]   **Decision date:** 2026-11-27 for the first two pilots (30 days after the second kickoff on 2026-10-28 [ASSUMPTION])

## Assumptions ranked

| # | Assumption | Category | Risk | Uncertainty | Score | Evidence |
|---|---|---|---|---|---|---|
| 1 | Partners pay $150+/month separately from Karbon/TaxDome | Willingness to pay | 5 | 5 | 25 | None: pilots are free, no price discussed |
| 2 | Firms won't wait for Karbon/TaxDome to add close tracking | Demand | 5 | 4 | 20 | Their templates are already used for close (company.md) |
| 3 | A client-by-client close board means fewer slipped deadlines | Value | 4 | 4 | 16 | Problem stated in company.md; never measured |
| 4 | Ops leads update the board instead of their spreadsheet | Value | 4 | 4 | 16 | None |
| 5 | We can recruit 4 more in-band pilot firms in 2 weeks | Channel | 4 | 3 | 12 | 9 in-band waitlist signups; 11 interviewees |
| 6 | Firms will give a new vendor access to QBO/Xero | Feasibility | 3 | 4 | 12 | None |
| 7 | Partners read a weekly blocked-clients summary | Value | 3 | 4 | 12 | None |
| 8 | QBO and Xero APIs expose the reconciliation status we need | Feasibility | 2 | 4 | 8 | Not checked. Risk is 2 because manual entry works for a pilot |
| 9 | Founder hours per firm stay manageable at 6 firms | Feasibility | 2 | 3 | 6 | You ran close at a 9-person firm for 4 years |

Top: #1. Second: #3, because the same pilot tests it. #2 can't be tested in 30 days; a firm that pays for #1 is partial evidence it won't wait.

Test type, from the tree: willingness to pay → no traffic from the segment (waitlist page only, 9 of 62 signups in band) → can you name 20+ prospects? Probably: 11 interviewees plus 9 in-band waitlist firms, minus the 2 pilots and any overlap [NEED: deduplicated list]. That gives a direct presale. Value delivery → a person can deliver it and the firm can know → concierge. Both top assumptions point to one artefact: a paid concierge pilot.

## Thresholds (set before build)

| Metric (definition) | Denominator | Sample | Window | Pass if | Fail if | Grey zone action |
|---|---|---|---|---|---|---|
| Recruitment: in-band firms that accept a 30-day pilot with $150/month conversion terms | Direct asks made | 20 (presale floor) | To 2026-11-06 | 4+ of 20 | 0–1 of 20 | 2–3: run with 4–5 pilots; ask each pilot partner for 2 referrals for one more week |
| Paid conversion: pilot firms paying $150+/month at day 30 | Firms that started a pilot | 6 (under the floor of 10: directional) | Each firm's day 30 | 3+ of 6 | 0–1 of 6 | 2 of 6: interview both converters and non-converters on which budget it came from, then re-run `idea-validator` before more pilots |
| Value: clients past their close deadline in the pilot month vs the month before | Clients in close, per firm | 2 firms first | First pilot month | Fewer than baseline in both firms | Same or more in both | Mixed: check whether the ops lead used the board |

Calculation:
- Goal: 3 firms paying at least $150/month (company.md). Two pilots can produce at most 2, one short.
- Plan for 6 pilot firms so the goal survives half of them not converting: 3 / 6 = 50%. That is a planning choice [ASSUMPTION], not a benchmark.
- 6 = 2 current + 4 new. Recruiting 4 from 20 asks needs 4 / 20 = 20% to accept.
- Value baseline: [NEED: last month's slipped-client count from each firm, collected at kickoff].

## Feature triage

| Feature | Bucket | Assumption served / reason |
|---|---|---|
| Per-firm close board (no-code table: client, close steps, owner, status, blocked reason, due date) | Must | #3, #4; it is also the thing they would pay for |
| Weekly blocked-clients summary to the partner, written by you from the board | Must | #3, #7 |
| Conversion terms one-pager + payment link ($150/month from day 31) | Must | #1 |
| QBO integration | Later | #6, #8; not the top assumption |
| Xero integration | Later | Same |
| Automatic reminders to bookkeepers | Later | Needs the board to prove useful first |
| Karbon/TaxDome connector | Never (for this test) | Tests coexistence, not willingness to pay |
| Logins, roles, permissions, admin panel, settings | Never | You operate the board; firms get view links |
| Billing automation | Never | Payment link |

Musts: 3/3   Estimated build: 2 days

## Build plan

| Day | Work | Done when |
|---|---|---|
| 1 (Mon 10-26) | Board template from your own close checklist; terms one-pager; payment link | Template filled with one dummy client; payment link tested |
| 2 (Tue 10-27) | Firm A kickoff: terms, baseline count, load clients | Terms agreed or declined by email (logged either way); board live |
| 3 (Wed 10-28) | Firm B kickoff; send the first 10 of 20 pilot asks | Board live; 10 asks sent |
| 4 (Thu 10-29) | First daily status sweep for both firms; send the other 10 asks | Both boards current; 20 asks sent |
| 5 (Fri 10-30) | First partner summary to both firms; log your hours per firm | Summaries sent; hours logged |

Midpoint checkpoint (day 3): if behind, the board drops to client, status, and blocked reason only.

Priya: [NEED: her hours during the pilot]. If she has capacity, a 3-day read-only QBO spike is allowed as a Later item. It does not enter the Musts.

## Deliberately not building

| Feature | Why not now | Brings it back |
|---|---|---|
| QBO + Xero integrations | Feasibility, not willingness to pay; manual updates work for up to 6 firms | 2+ paying firms name manual updates as a reason to cancel, or founder hours pass the break point below |
| Automatic reminders | Value of the board unproven | Ops leads update the board unprompted 3+ days a week in week 2 |
| Logins and roles | One operator (you) | A paying firm asks for staff access |
| Karbon/TaxDome connector | Not the question | 2+ pilot firms refuse to pay unless it lives inside their practice tool. Log that as evidence on the biggest risk too |

## Manual steps behind the curtain

You chase each ops lead for status daily, update the board, and write the Friday summary. [NEED: your hours per firm, measured in week 1.] Break point, chosen now: when manual work passes 10 founder-hours a week across all firms, automate the most time-consuming step first. That step is the first integration candidate.

Logged to `.foundora/journal.md` (created):

```markdown
### 2026-10-23 — experiment: Paid concierge pilot
- Assumption: We believe partners will pay $150+/month separately from Karbon/TaxDome
- Test: concierge pilot with conversion terms, live by 2026-10-27, decide by 2026-11-27
- Pass if: 3+ of 6 pilot firms paying at day 30  Fail if: 0–1 of 6  Grey zone: interview, re-run idea-validator
- Sample: 6 firms, directional (floor is 10)
- Source: mvp-scoper
```

```markdown
### 2026-10-23 — decision: QBO and Xero integrations deferred
- What: both integrations moved to Later
- Why: they test feasibility; the top assumption is willingness to pay separately
- Revisit: 2+ paying firms cite manual updates as a reason to cancel, or 10+ founder-hours a week on manual work
- Source: mvp-scoper
```

## Why this scores 12/12

| Rubric line | Where it shows |
|---|---|
| Context use | Goal, runway, pilots, waitlist from company.md; only kickoff dates and Priya's hours requested |
| Honesty | No benchmark rates; 50% marked as a planning assumption; directional sample stated |
| Decision quality | Risk x uncertainty table, decision tree path shown, 3-Must cap held |
| Pushback | Integrations steelmanned, objected to, moved to Later with a trigger |
| Format | Exact output template, tables, US spelling |
| Actionability | Dated 5-day plan; thresholds derived from the 90-day goal; decision date 2026-11-27 |
