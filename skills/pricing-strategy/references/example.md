# Worked example: pricing-strategy

> Illustrative and fictional (Ledgerline fixture). Calibrates depth and format only; never reuse its content.

## Request

"What should we charge?"

## Context used

`.foundora/company.md` is the Ledgerline fixture (`evals/fixture-company.md`): validation stage, no revenue, 2 free 30-day concierge pilots starting next week, 90-day goal of 3 firms at ≥ $150/month, buyer is the managing partner paying by card or annual invoice. No journal, so no lean-canvas numbers to reuse; gross margin and churn are stated as `[ASSUMPTION]`. No questions asked: the missing inputs (value in hours, practice-tool spend) cannot be answered from memory anyway, so they become `[NEED]` items and tests.

## Model answer

# Pricing recommendation: Ledgerline (2026-10-21)

**Answer:** $299/month per firm for up to 60 active clients ($2,990/year). Evidence level 0: founder opinion. The pilots get a written founding price of $239/month before they start. This changes after the price ladder in test 2.

Your 90-day goal says $150. That is the floor you need, not the price the value supports, and nobody has been asked to pay anything yet. Start higher and let the ladder bring it down if it must.

## Recommendation
- **Model:** tiered by active-client bands
- **Value metric:** active clients closed per month. Firms already know this number, and value grows with every client whose close is tracked
- **Acquisition motion:** paid pilot, no free tier. 62 waitlist signups is far under the ~100 active users freemium needs
- **Evidence level:** 0 founder opinion

## Value metric scoring
| Candidate | Value | Understandable | Grows | Hard to game | Cost aligned | Total |
|---|---|---|---|---|---|---|
| Active clients closed per month | 3 | 3 | 3 | 2 | 2 | 13 |
| Reconciled accounts | 2 | 1 | 3 | 2 | 3 | 11 |
| Staff seats | 2 | 3 | 2 | 1 | 2 | 10 |
| Flat per firm | 1 | 3 | 1 | 3 | 1 | 9 |

Seats also fail the access rule: per-seat pricing makes partners limit who can log in, and reviewers are exactly the people who need to see close status. Even if Karbon and TaxDome price per seat [NEED: Karbon price, verify on their site] [NEED: TaxDome price, verify on their site], do not copy it.

## Founding offer (use instead of Tiers below 10 paying customers)
| Price | Value-metric allowance | Terms | Expiry | Evidence level |
|---|---|---|---|---|
| $239/month (20% off the $299 list price), from day 31 | Up to 60 active clients closed per month | Free 30-day pilot as promised; converts unless cancelled by day 30; price locked 12 months; case study + one reference call | Offer expires at pilot start | 0 (founder opinion); becomes 5 once a pilot signs |

Draft tiers for later, not published: Small practice $149 (up to 25 clients), Growing firm $299 (up to 60, recommended), Multi-reviewer $599 (up to 120) [ASSUMPTION]. Spacing 2.0x each step; the fixture's 20–80 clients per firm lands mostly in the middle tier.

Why $299 list and not the $150 in your 90-day goal: $150 is a target, not evidence (level 0), and pricing at the target leaves no room to learn if firms would pay more. The pilots test $239; the waitlist ladder (test 2) tests $299.

## Rationale
- Why this model and metric: firms differ by client count (20–80), and client count tracks the value: more clients means more closes to chase.
- Why these price points: the 10–30% of value heuristic says $299 needs $299 ÷ 0.30 = $997 to $299 ÷ 0.10 = $2,990 of monthly value per firm. That is staff hours not spent chasing status or redoing reconciled work, times their cost. [NEED: hours saved per close and blended staff cost per hour, measured in the pilots.] The buyer's anchor is their practice-tool bill: [NEED: what pilot firms pay per month for Karbon or TaxDome, from the firms]. If $299 is a large share of that bill, expect "why can't Karbon do this" on every call.
- What we are deliberately not doing: no free tier, no per-seat pricing, no public pricing page, no price below $150.

## Policies
- Founding / pilot offer: the free 30 days stay as promised. Before day 1, both firms sign a one-page term: $239/month (20% off $299) from day 31 unless they cancel by day 30, locked for 12 months, in exchange for a case study and one reference call. Offer expires at pilot start.
- Discounts: max 20% without both founders signing off, always traded for annual prepay, a case study, or a referral, each with an expiry date.
- Grandfathering: founding firms keep their price for 12 months from first payment; at least 30 days' written notice before any change.
- Annual: 2 months free (about 17% off).

## Unit economics check
Shared definitions; churn 4% monthly [ASSUMPTION], so lifetime = 1 ÷ 0.04 = 25 months.

| Tier | ARPA | Gross margin | Gross profit / month | CAC (channel) | Payback | Max allowable CAC | CAC ceiling at 12-month payback | Flag |
|---|---|---|---|---|---|---|---|---|
| Small practice | $149 | 80% | $119.20 | [NEED] | [NEED] | 119.20 × 25 ÷ 3 = $993 | 12 × 119.20 = $1,430 | Tightest: founder-led selling with demos must cost under $993 |
| Growing firm | $299 | 80% | $239.20 | [NEED] | [NEED] | $1,993 | $2,870 | None |
| Multi-reviewer | $599 | 80% | $479.20 | [NEED] | [NEED] | $3,993 | $5,750 | None |
| Founding ($239) | $239 | 80% | $191.20 | [NEED] | [NEED] | $1,593 | $2,294 | None |

CAC is unknown until outreach runs; run lean-canvas to model it.

## Test plan
| # | Hypothesis | Change | Audience | Metric | Duration / sample | Pass if |
|---|---|---|---|---|---|---|
| 1 | Pilot firms will pay separately from their practice tool | Signed founding term before day 1 | 2 pilot firms | Signed terms, then day-31 conversion | Sign by pilot start; convert by day 31 | 2 of 2 sign. 0 of 2: stop and run value interviews before building more. 1 of 2: interview the firm that declined |
| 2 | The recommended tier holds at $299 or higher | Sequential ladder: $249 to 3 firms, then $299 to 3, then $349 to 3 | 9 in-band waitlist firms | Paid-pilot yes (card or signed order) | 21 days, n = 9, directional | Move up a step only if ≥ 2 of 3 say yes. Hold at the highest step with ≥ 1 of 3. 0 of 3 at $249: re-run value interviews |
| 3 | Firms will prepay to lock the price | Offer annual at 2 months free to every converting firm | First 3 paying firms | Annual uptake | Until 3 firms pay | ≥ 1 of 3 picks annual |

Policy for test 2: firms talk to each other, so anyone quoted a higher step who learns of a lower one gets the lower price.

## Open data
- [NEED: Karbon price, verify on their site]
- [NEED: TaxDome price, verify on their site]
- [NEED: monthly practice-tool spend at each pilot firm, from the firms]
- [NEED: hours saved per close and staff cost per hour, measured during the pilots]
- [NEED: active client count at each pilot firm, to confirm which tier their founding price applies to]
- [NEED: hosting and payment cost per firm, to replace the 80% margin assumption]

## Logged
```markdown
### 2026-10-21 — decision: Pricing v1, tiered per active clients closed
- Prices: $149 / $299 (recommended) / $599 per month, annual = 10x monthly; evidence level 0 (founder opinion)
- Founding / pilot offer: $239/month from day 31, locked 12 months, for case study + reference call; expires at pilot start
- Test started: pilot conversion terms + $249/$299/$349 ladder on 9 waitlist firms. Pass if 2 of 2 pilots sign and ≥ 2 of 3 accept at a step, by 2026-11-11
- Source: pricing-strategy
```
