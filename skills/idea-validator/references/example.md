# Worked example: idea-validator

> Illustrative and fictional (Ledgerline fixture). Calibrates depth and format only; never reuse its content.

## Request

"Tear this idea apart and give me a verdict."

## Context used

- `.foundora/company.md`: the Ledgerline fixture (`evals/fixture-company.md`). Working preferences: direct, tables over paragraphs, US spelling.
- `.foundora/journal.md`: not present, so no earlier verdict to reuse.
- No interview notes were shared. The answer scores the counts in company.md, applies the caps, and marks the notes as `[NEED]` instead of asking first, because the notes would raise scores, not change the verdict.
- Date: 2026-10-23.

## Model answer

# Idea pressure test — Ledgerline — 2026-10-23

**Verdict:** KEEP TESTING
**Why, in one sentence:** The deciding hypothesis is H4: nobody has been asked to pay and both pilots are free, so there is no evidence yet that firms will pay for close tracking on top of Karbon or TaxDome.
**What would change this:** Both pilot firms agreeing to $150/month conversion terms (H4 to 4 or 5), plus notes showing at least 5 of the 11 interviewees describing a specific recent close failure (H2 and H3 to 4). That makes BUILD reachable.
**Not counted as evidence:** The 2 free pilots count toward H1 (time commitment), not H4. The 62 waitlist signups are attention, not demand, and 53 of them are outside your band. Your 4 years running close at a firm count toward H7; for H2 and H3 they are one data point (cap 2).

## Problem profile

| Popular | Growing | Urgent | Expensive | Mandatory | Frequent |
|---|---|---|---|---|---|
| Partly: 11 interviewees in band; [NEED: count of firms with 3–15 staff, from a source you can check] | [NEED]: nothing dated in company.md (same gap as H6) | Yes: client close deadlines slip (company.md) | Partly: reviewers redo work, hours not counted [NEED: hours per close] | Partly: close is required for every client; tracking it is not | Yes: every month, across 20–80 clients |

**Read:** urgent and frequent, so it's not a nice-to-have. What's unproven is the money: nobody has put a cost on a slipped close, and that's what a partner pays to avoid.

## Red flags

| Flag | Status | Evidence | Clears if |
|---|---|---|---|
| Solution in search of a problem | Clear | You ran close at a 9-person firm for 4 years; the problem came first (company.md) | n/a |
| Tarpit | [NEED] | Practice tools exist and do adjacent jobs, which is a good sign for the market. Unknown: has anyone sold a standalone close tracker to small firms and stalled or been absorbed? | A 2-hour search names past attempts and why they stalled, or finds none |
| Made-up idea | Clear | 2 firms gave a month of their time to a pilot | n/a |
| Wide, not deep | Clear, watch it | The depth is 2 pilot firms and 11 interviews, not the 62 signups. Don't let the waitlist count become the story | Stays clear while the scoreboard counts pilot firms, not signups |

The tarpit check at `[NEED]` blocks BUILD on its own, so it's test 6 below.

## Hypotheses and scores

| # | Hypothesis (We believe... / Wrong if...) | Score | Evidence (type, source) | Cap applied |
|---|---|---|---|---|
| H1 Customer | Managing partners and ops leads at bookkeeping firms with 3–15 staff, closing 20–80 clients a month on spreadsheets and email. Wrong if fewer than 3 in-band firms we approach run close that way. | 4/5 | 11 interviews in segment (8 partners, 3 ops leads); 2 firms agreed to a dated pilot, a time commitment (company.md) | Commitments allow 5; held at 4 until a pilot runs on real client data |
| H2 Problem | Partners can't see which clients are blocked, so deadlines slip and reviewers redo work. Wrong if fewer than 5 of 11 interviewees describe a specific recent close where that happened. | 3/5 | 11 interviews, no notes shared; the problem is stated in company.md in your words. [NEED: notes or per-person counts] | 3 until a pattern is shown. Pattern = 40% of 11 = 4.4, so 5 people |
| H3 Frequency / intensity | Close runs monthly across 20–80 clients, and each slip costs reviewer hours. Wrong if interviewees can't name hours or a consequence from their last close. | 3/5 | Monthly cadence and consequences (slips, rework) from company.md; paid-for workarounds exist (Karbon, TaxDome templates). No hours quantified. [NEED: hours lost per close, from notes] | 3, pattern unverified |
| H4 Willingness to pay | The managing partner pays at least $150/month for close tracking, separate from the practice tool. Wrong if pilot firms won't discuss price or say it must come out of the Karbon/TaxDome budget. | 2/5 | Payer and purchase path known: partner, card or annual invoice (company.md). Existing spend is on the substitute, not on close tracking. Pilots are free. [NEED: did price come up in any of the 11?] | Between anchors: payer located (part of 3), no price discussed (1). Missing evidence, not negative |
| H5 Channel | The first 10 customers come from your bookkeeping network and the waitlist. Wrong if fewer than 2 of the 9 in-band waitlist firms accept a direct pilot offer. | 3/5 | 11 target interviews reached; source not recorded [NEED: where the 11 and the 62 came from]. In-band share of waitlist: 9 / 62 = 14.5% | 3: reached 10+, rate not measured |
| H6 Why now | Something dated has changed that makes close tracking newly needed or possible. Wrong if nothing specific can be named. | 1/5 | Nothing in company.md. [NEED: a specific, dated change with a source you can check] | 1, no answer |
| H7 Why you | Four years running ops at a 9-person bookkeeping firm, plus a CTO from fintech, give access and insight competitors lack. Wrong if that network produces fewer than 3 intros in 30 days. | 4/5 | Team section, company.md | 4: years in the role; 5 needs sales to the segment |

## Verdict path

- PROVISIONAL: not applied. 11 conversations clears the floor of 5, provided they were about past behavior [NEED: confirm]. If most were demos, this becomes PROVISIONAL — KEEP TESTING.
- KILL: not matched. H2 and H3 are 3, not 2 or below. Incumbent risk is a threat, not a structural blocker. H7 is 4.
- PIVOT: not matched. H2 and H3 are not both 4+. H4's 2 comes from a question never asked, which cannot trigger PIVOT anyway.
- BUILD: not matched. H2 and H3 are below 4; H4 is below 3 with no commitment; the tarpit check is at `[NEED]`.
- KEEP TESTING: matched. Flip hypothesis: H4. Re-run by 2026-11-06.

## How this dies

| # | Mechanism | Likelihood (reason) | Earliest signal | Maps to |
|---|---|---|---|---|
| 1 | Karbon or TaxDome ship close tracking inside the tool firms already pay for | High: company.md lists their workflow templates as a current alternative, so the job already lives in their product | Pilot users ask "can this live in Karbon?" or keep the template running alongside | H4, H6 |
| 2 | Firms use the free pilot but won't add a separate subscription | High: pilots are free and price has never come up | Partner deflects the price question at kickoff | H4 |
| 3 | Ops leads keep the spreadsheet; the tracker becomes a second place to update | Medium: daily users have an existing habit; untested | By pilot week 2, status updates come from you, not the firm | H2, H3 |
| 4 | No repeatable channel beyond your network | Medium: 14.5% of the waitlist is in band; interview source unrecorded | Fewer than 2 of the 9 in-band firms reply to an offer | H5 |
| 5 | Runway ends before the answer arrives | Medium: 7 months, no revenue; 30-day pilots mean no conversion data before late November | No paying firm by 2027-01-18 (90 days from 2026-10-20 [ASSUMPTION]) | H5, H7 |

## Cheapest next tests

| Priority | Assumption | Test | Cost (days / cash) | Duration | Sample | Pass if | Fail if |
|---|---|---|---|---|---|---|---|
| 1 | H4, risk 2 | Conversion terms for both pilots before kickoff: $150/month from day 31 if an outcome named now is met | 0.5 / $0 | 1 week | 2 | 2 of 2 agree by email | 0 of 2 will discuss price (1 of 2: run test 2 before deciding) |
| 2 | H4, H5, risks 2 and 4 | Offer a paid 30-day pilot at $150/month to the 9 in-band waitlist firms; tag the source of each reply | 1 / $0 | 2 weeks | 9 (under the 20-ask floor, directional) | 2+ accept | 0 accept |
| 3 | Risk 1, H4 | Ask the interviewees who use Karbon or TaxDome: "When did you last try to run close in its templates? What happened?" | 2 / $0 | 2 weeks | Up to 11 [NEED: how many use either tool] | 5+ tried and stopped, with a specific reason | 5+ run close in the template and are satisfied |
| 4 | H2, H3 | Recount the 11 sets of notes: per person, a specific recent close failure and hours lost | 0.5 / $0 | 2 days | 11 | 5+ of 11 with an event and hours | 2 or fewer of 11: H2 drops to 2 and the KILL rule (10+ interviews) is checked |
| 5 | H6 | Write the why-now with one dated, sourced change, or accept H6 at 1 | 0.5 / $0 | 2 days | n/a | One specific change with a source | None found: H6 stays 1, flag for `pitch-deck` |
| 6 | Tarpit flag | Search for standalone close trackers aimed at small firms that shut down, pivoted, or were absorbed; ask 3 interviewees what they tried before Sheets | 0.25 / $0 | 2 days | n/a | Attempts named with a reason you can avoid, or none found | 2+ attempts stalled on the same "firms won't pay outside their practice tool" reason: that's the biggest risk confirmed, so rerun the verdict early |

Threshold for test 2, derived: the 90-day goal is 3 paying firms. If both pilots convert you need 1 more; the pass line is 2 to absorb one pilot not converting.

**Re-run verdict by:** 2026-11-06

Logged to `.foundora/journal.md` (created):

```markdown
### 2026-10-23 — decision: Idea verdict KEEP TESTING
- Scores: H1 4, H2 3, H3 3, H4 2, H5 3, H6 1, H7 4
- Evidence base: 11 conversations; 2 time commitments (free pilots); 0 money commitments
- Next test: conversion terms for both pilots at $150/month, pass 2 of 2 by 2026-10-30
- Re-run verdict by: 2026-11-06
- Source: idea-validator
```

## Why this scores 12/12

| Rubric line | Where it shows |
|---|---|
| Context use | All seven scores built from company.md; nothing re-asked; notes requested as `[NEED]`, not as a blocker |
| Honesty | No invented interview content, hours, or competitor facts; H6 left at 1; pricing gap called missing, not negative |
| Decision quality | Caps shown per score; every verdict rule checked in order; flip hypothesis and re-run date named |
| Pushback | Free pilots and waitlist explicitly not counted toward H4; incumbent-feature risk rated High; tarpit left at `[NEED]` and blocking BUILD instead of assumed clear |
| Format | Mode A template, tables, US spelling |
| Actionability | Cheapest money test first, with pass/fail lines and a 2026-11-06 re-run |
