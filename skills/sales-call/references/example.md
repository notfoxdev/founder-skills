# Worked example (illustrative, fictional)

> Uses the fictional Ledgerline fixture (`evals/fixture-company.md`) plus two invented journal entries. It calibrates depth, format and tone only. Never copy its names, wording or answers into a real prep sheet.

## Request

"Tuesday is the day-30 call with Firm A's managing partner, Dana. I want her on $150/month. At last week's check-in she said 'honestly, Karbon already does this, we just never set it up properly.' Prep me."

## Context used

- `.foundora/company.md`: the Ledgerline fixture. Partner buys by card or annual invoice, no procurement. Firms already pay for Karbon or TaxDome. Biggest risk: will firms pay separately from their practice tool. 90-day goal: 3 firms paying at least $150/month. 2 pilot firms. Working preferences: direct, tables, US spelling.
- `.foundora/journal.md` (fictional for this example): "2026-10-27 — decision: Firm A pilot kicked off, free 30 days, conversion terms not discussed" and the founder's verbatim note of Dana's Karbon line from the check-in.
- Date: Friday 2026-11-20. Call: Tuesday 2026-11-24. Pilot ends 2026-11-26 (2026-10-27 + 30 days).
- No question asked first. The missing pieces are marked `[NEED]` and none of them changes the goal.

## Model answer

# Sales call prep — Dana, Firm A — 2026-11-24
**Call goal:** Dana agrees to $150/month from 2026-11-27, month to month, and pays by Friday 2026-11-27; or gives a clear no with the reason.
**Learn on this call:** where October close actually happened, on the board or in Karbon and the sheet. That's your biggest risk, answered by a paying customer or not.
**Most likely objection:** "Karbon already does this." Answer with her own second half: "we never set it up properly."

Two things to fix before Tuesday. First, the pilot started with no written success criteria, so you can't tell her it worked. You can only ask her, and bring what the board shows. Second, don't argue about Karbon's features. You haven't checked what its close templates do today, and she uses it every day. Let her tell you.

## What we know
| Fact | Source | Status |
|---|---|---|
| Free 30-day pilot since 2026-10-27, no conversion terms agreed | Journal, 2026-10-27 | verified |
| Dana buys; firms like hers pay by card or annual invoice | company.md (buyer pattern) | [NEED: confirm for Firm A] |
| Firm A pays for Karbon | Dana, at the check-in | verified, her words |
| "Karbon already does this, we just never set it up properly" | Your note, verbatim | verified |
| October close on the board: clients, blocked, late | The board | [NEED: pull before Tuesday] |
| Late clients in September, before the pilot | Ops lead | [NEED: ask Monday] |
| What Karbon's close templates do today | Karbon's current help docs | [UNVERIFIED]: read them, or ask her to show you |
| Whether another partner must agree | Nobody yet | [NEED]: ask on the call |

## Pain hypothesis
She couldn't see which clients were blocked without asking (company.md). During October she could. [ASSUMPTION] until she says so herself.

## Discovery (must-ask marked [MUST])
1. [MUST] "Walk me through October close. When you wanted to know who was blocked, where did you look?"
2. [MUST] "You said Karbon could do this but it never got set up. What got in the way?"
3. "Did the old close sheet keep running alongside the board?"
4. [MUST] "Compared with September, what was different this time? Anything that usually goes wrong and didn't?"
5. "If we stopped on Thursday, what would November close run on?"
6. [MUST] "Does anyone else need to agree before you add a monthly tool?"

## Qualify by minute 15
| Check | What we know | Question that settles it |
|---|---|---|
| Problem | Stated in company.md; pilot evidence [NEED] | Q1, Q4 |
| Payer | She pays for Karbon, so she buys tools | Q6 |
| Person who can say yes | Dana [ASSUMPTION: no co-partner] | Q6 |
| Reason to act now | November close starts days after the pilot ends | Q5 |

If Q1 and Q3 show October ran on the old sheet and the board sat unused, that's 0 of 4 on Problem in practice. Don't demo or ask for money. Go to the walk-away line.

## Demo plan
| Their words | What you show | Check-in question |
|---|---|---|
| Her answer to Q1 | Firm A's October board, blocked clients at the top | "Is that the view you were missing?" |
| Her answer to Q4 | The client that held up close longest, and when it got unblocked | "When did you find out about this one in September?" |

Two rows. Nothing about integrations, nothing on the roadmap.

## Likely objections
| Objection | What's probably under it | Question to ask | Answer from evidence |
|---|---|---|---|
| "Karbon already does this" | Paying twice for overlap; or Karbon could, but nobody had time to build it | "In October, did you open Karbon or the board to see who was blocked?" | If the board: "So the choice is setting Karbon up or keeping this. Which would your ops lead pick?" If Karbon would really cover it: agree, ask what setting it up would take, and log it as evidence on the biggest risk. Don't describe Karbon's features. |
| "Can we keep it free another month?" | Not convinced yet, or just used to free | "What would you need to see in December that you didn't see in October?" | No free extension. Offer $150 month to month, cancel any time. If she names a real test, write it down as the criterion and charge from the 27th. |
| "$150 is a lot next to what we pay Karbon" | Comparing to Karbon's price | "Compared to what?" | Only the cost she names in Q4. If she names none, don't make one up; ask what October close cost the firm. |

## Price and terms
$150/month (company.md, the 90-day goal floor), month to month, from 2026-11-27, paid by card through a link. If she asks for a discount, the only trade is annual upfront [NEED: decide the annual price before Tuesday with `pricing-strategy`]. Nothing else moves on the call.

## The ask (word for word)
> "You've had a month and one full close on it. I'd like you to keep it at $150 a month from the 27th, month to month. Can I send the link now?"

Then stop talking.

**Walk away if:** October close ran in Karbon or the sheet and nobody used the board. Thank her, ask what would have made it the place she looked, and log that as the clearest evidence yet on your biggest risk.

## Pipeline
Live deals with a dated next step: 1 (Firm A, Tuesday). Firm B: [NEED: date of its day-30 call]. Customers still needed: 3. Funnel rule: 2 x 3 = 6 live deals, so even with Firm B you're short by 4. Two pilots can't produce three customers even if both convert. Book more calls this week with `cold-outreach`, whatever happens Tuesday.

## Follow-up email (draft for a yes, send the same day)
Subject: Ledgerline from the 27th

> Hi Dana, thanks for today. You said <her words about October close>, and that's what we'll keep doing. From the 27th it's $150 a month, month to month, and you can stop any time. The link is below. I'll check in with <ops lead> before November close starts, and I'll send <anything you promised on the call> by <day>.

Logged to `.foundora/journal.md`:

```markdown
### 2026-11-20 — experiment: Firm A conversion ask
- Terms: $150/month from 2026-11-27, month to month
- Success criteria: none written at kickoff [NEED]; the call tests the biggest risk directly
- Converts if: Dana pays by 2026-11-27  Ends if: clear no, reason logged
- Decide by: 2026-11-27
- Source: sales-call
```

After Tuesday's call, I'll write the learning entry with the stage and the evidence for it.
