# Worked example: cofounder

> Illustrative and fictional (Ledgerline fixture). Calibrates depth and format only; never reuse its content.

## Request

"Be my cofounder. What should I work on this week?"

## Context used

- `.foundora/company.md`: the Ledgerline fixture (`evals/fixture-company.md`), updated 2026-10-20. Working preferences: direct tone, tables over paragraphs, US spelling.
- `.foundora/journal.md`: not present. This is the first session, so the journal is created at close.
- Session date: Monday 2026-10-26. The request implies Prioritization mode, so no "what do you want out of this session" question.

What the answer has to get right: the pilots start this week and they are free, so they test usage but not the biggest risk (will firms pay separately from Karbon or TaxDome). Two pilots also cannot reach a goal of three paying firms. Both points belong in the first reply.

## Model answer

**Where we are:** Validation: month-end close tracker for bookkeeping firms with 3–15 staff. Latest traction: 11 discovery interviews, 62 waitlist signups (9 in the target band), 2 free 30-day concierge pilots starting "next week" as of 2026-10-20. No revenue.
**Biggest risk:** Firms already pay for Karbon or TaxDome. Will they pay separately for close tracking? Last evidence: none logged.
**Open loops:** No journal yet. Gap: company.md has no conversion terms for the pilots and no start dates [NEED: kickoff date for each firm].

## This week: prioritization

| # | Candidate | Impact | Confidence | Effort | Score | Tests biggest risk? |
|---|---|---|---|---|---|---|
| 1 | Agree conversion terms with both pilot firms before kickoff: $150/month from day 31 if the pilot hits an outcome you both name now | 5 | 3 | 1 | 15.0 | Yes |
| 2 | At each kickoff, ask the managing partner what the firm pays today for Karbon/TaxDome and QBO/Xero, and who approved the last tool added | 3 | 3 | 1 | 9.0 | Yes |
| 3 | Offer a third pilot, same paid terms, to the 9 in-band waitlist firms | 5 | 3 | 2 | 7.5 | Yes, if offered with paid terms |
| 4 | Read Karbon and TaxDome help docs and changelogs for close features | 3 | 1 | 1 | 3.0 | Partly |
| 5 | More discovery interviews beyond the 11 | 1 | 3 | 3 | 1.0 | No |
| 6 | Improve the ledgerline.app waitlist page | 1 | 1 | 2 | 0.5 | No |

Committed (not scored): both pilot kickoffs. They happen regardless; the question is what they carry.

Scoring notes:

- Impact 5 means it directly moves "3 firms paying at least $150/month" (company.md, 90-day goal). Confidence is 3 at most because nothing has been tested with your own customers yet.
- Item 3 is Impact 5 because of arithmetic: even if both pilots convert, 2 paying firms is fewer than 3. Taking the goal as 90 days from 2026-10-20 [ASSUMPTION], the deadline is 2027-01-18, so a 30-day pilot has to start by 2026-12-19 to convert in time.
- Runway check: 7 months and no revenue means default dead at current growth. That's not a crisis, it's the reason the pilots have to carry a price. Monthly burn isn't in company.md [NEED: monthly burn]; jot it down when you send the terms.
- Item 6 is fake progress at this stage: no firm in the pilot would notice a better waitlist page this week.

**Pushback:**

- Steelman: free pilots get firms in the door fast. Asking for money before they see value could cost you one of only two pilots.
- Strongest objection: a free pilot with no price on the table tells you whether they like it, not whether they will pay separately from Karbon or TaxDome. If price first comes up on day 30, your first evidence on the biggest risk arrives in late November. Runway is 7 months as of 2026-10-20, so that leaves about 6, with no second batch of pilots lined up.
- Test: put the terms in front of both managing partners this week. Pass: both agree by email to $150/month from day 31 if the named outcome is met. If either refuses to discuss price, that is the first real evidence on the biggest risk. Log it as a learning, not a failure.

**One question:** Have you already told the two firms the pilot is free with no strings? If yes, the win changes from "terms agreed" to "both agree to a day-30 pricing decision at $150/month". Everything else stays the same.

**Supporting tasks:**

1. Ask the budget questions (item 2) at each kickoff. You, on the kickoff day [NEED: dates].
2. Email the 9 in-band waitlist firms offering pilot #3 on the same paid terms. You, Wednesday 2026-10-28.

**Not this week:** more discovery interviews, waitlist page changes, the competitor docs read (only if a 30-minute gap appears), any build the pilots do not strictly need.

**Logged to journal:** nothing yet. Once you answer the question, I will create `.foundora/journal.md` with this entry:

```markdown
### 2026-10-26 — decision: Pilots carry paid conversion terms
- What: both pilots get written terms at kickoff, $150/month from day 31 if the agreed outcome is met. Options considered: free with no terms, free with day-30 pricing decision, paid terms now.
- Why: free pilots do not test the biggest risk (paying separately from Karbon/TaxDome); 2 pilots cannot reach the 3-firm goal
- Threshold / win: both managing partners agree by email by 2026-10-30
- Revisit: if either firm refuses to discuss price, log a learning and rerun this decision
- Source: cofounder
```

**This week's win (proposed):** By Friday 2026-10-30, both pilot firms' managing partners have agreed by email to pay $150/month from day 31 if the pilot meets the outcome named at kickoff. If either has not replied by Wednesday 2026-10-28, call them that afternoon.
**Next action:** draft the one-paragraph conversion term and send it to both partners, by Monday 2026-10-26 noon. Done when both emails are sent.

## Why this scores 12/12

| Rubric line | Where it shows |
|---|---|
| Context use | Brief built from company.md only; nothing re-asked; US spelling and tables per preferences |
| Honesty | Kickoff dates marked `[NEED]`; the 90-day deadline marked `[ASSUMPTION]`; no invented reply rates |
| Decision quality | Scored table, override rule satisfied (risk items are top 3), one win plus two supporting tasks |
| Pushback | Steelman, one objection, a test with a pass line; the goal arithmetic stated plainly |
| Format | Brief, prioritization block, and journal entry match the skill's templates |
| Actionability | Binary win checkable by a named Friday; dated supporting tasks |
