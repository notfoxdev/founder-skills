# Worked example: lean-canvas

> Illustrative and fictional (Ledgerline fixture). Calibrates depth and format only; never reuse its content.

## Request

"Fill in my lean canvas and tell me if the economics can work."

## Context used

`.foundora/company.md` is the Ledgerline fixture (`evals/fixture-company.md`). No journal yet. No revenue, no churn, no acquisition spend, so every unit-economics input is an `[ASSUMPTION]` and the answer runs three scenarios. No questions asked: the file covers segment, alternatives, and the $150/month goal, and the gaps go to Open data.

## Model answer

# Lean Canvas: Ledgerline, small bookkeeping firms (v1, 2026-10-21)

**Verdict:** works only if firms pay at least about $143/month on top of their practice tool and founder-led outreach converts near the base funnel. In the pessimistic case you lose money on every customer, and nothing you have today rules that case out.

| # | Block | Content | Source |
|---|---|---|---|
| 1 | Customer segments | Bookkeeping firms with 3–15 staff closing books monthly for 20–80 clients. Managing partner buys; ops lead and bookkeepers use it daily | (F) |
|   | Early adopters | Firms that pay for Karbon or TaxDome but still run close from Google Sheets and email. First list: the 9 in-band waitlist firms | (F) / [ASSUMPTION] on "still use Sheets" |
| 2 | Problem | 1. Partners cannot see which clients are blocked 2. Deadlines slip 3. Reviewers redo work because nobody knows what was reconciled | (F) |
|   | Existing alternatives | Google Sheets checklists, Karbon and TaxDome workflow templates, doing nothing | (F) |
| 3 | Unique value proposition | See every client's close status and what is already reconciled, alongside the practice tool you already use | [ASSUMPTION] |
|   | High-level concept | The corporate close checklist, sized for a 3–15 person bookkeeping firm | [ASSUMPTION] |
| 4 | Solution | 1 → cross-client close board with blocked flags. 2 → per-client due dates with overdue alerts. 3 → per-account reconciliation log (who, what, when) | [ASSUMPTION] |
| 5 | Channels | First 10: founder outreach to the 9 in-band waitlist firms and the founder's network from 4 years in firm ops. At scale: practice-tool marketplaces, referrals | (F) / [ASSUMPTION] |
| 6 | Revenue streams | Subscription per firm, $150/month, card or annual invoice | Price [ASSUMPTION] from the 90-day goal; billing (F) |
| 7 | Cost structure | Fixed: two full-time founders, about 7 months runway, burn [NEED]. Variable: hosting, payment fees, onboarding and support time | (F) / [NEED] |
| 8 | Key metrics | Paid commitments at ≥ $150/month (goal: 3 in 90 days); share of interviewees ranking close visibility top 3. Not the 62-person waitlist | (F) / [NEED] |
| 9 | Unfair advantage | CEO ran ops at a 9-person bookkeeping firm for 4 years. Accepted as insider expertise; it is not a moat against Karbon or TaxDome adding this feature | (F) |

## Value proposition fit
| Job / pain / gain | Evidence | Solution element | Fit |
|---|---|---|---|
| Pain: partner cannot see blocked clients | Named in company.md; [NEED: how many of the 11 interviews raised it unprompted] | Close board | Weak (unranked) |
| Pain: reviewers redo reconciled work | Named in company.md; [NEED: hours lost per close] | Reconciliation log | Weak (unranked) |
| Job: hit every client's close deadline | "Deadlines slip" (F) | Due dates, overdue alerts | Weak |

The top pain is plausible but unranked, so the problem block scores 2 on likelihood below.

## Unit economics
Steady state after the concierge pilots. Pilot margin is lower because founder hours are COGS: [NEED: hours per pilot firm per month].

| Metric | Pessimistic | Base | Optimistic | Working | Source |
|---|---|---|---|---|---|
| ARPA (monthly) | $100 | $150 | $250 | Base = 90-day goal floor | [ASSUMPTION] |
| Gross margin % | 70% | 80% | 85% | Hosting, payment fees, support | [ASSUMPTION] |
| Gross profit / customer / month | $70 | $120 | $212.50 | ARPA × GM | Calculation |
| CAC | $2,125 | $950 | $350 | Funnel below | Calculation on [ASSUMPTION] |
| Monthly churn | 6% | 4% | 2.5% | SMB heuristic range 3–7% | [ASSUMPTION] |
| Lifetime (months) | 16.7 | 25 | 36 (cap) | 1 ÷ churn; 1 ÷ 0.025 = 40, capped | Calculation |
| LTV | $1,167 | $3,000 | $7,650 | 70 ÷ 0.06; 120 × 25; 212.50 × 36 | Calculation |
| LTV:CAC | 0.5 | 3.2 | 21.9 | 1,167 ÷ 2,125; 3,000 ÷ 950; 7,650 ÷ 350 | Calculation |
| CAC payback (months) | 30.4 | 7.9 | 1.6 | 2,125 ÷ 70; 950 ÷ 120; 350 ÷ 212.50 | Calculation |
| Max allowable CAC | $389 | $1,000 | $2,550 | LTV ÷ 3 | Calculation |
| Contribution margin / customer / month | $70 | $120 | $212.50 | No variable selling costs yet | Calculation |

CAC funnel (founder-led outbound, no paid budget per company.md). Inputs are `[ASSUMPTION]`: 5 minutes per message, 1.5 hours per demo including prep and follow-up, founder time at $75/hour.

| | Reply | Reply → demo | Demo → paid | Messages per customer | Hours | CAC |
|---|---|---|---|---|---|---|
| Pessimistic | 5% | 40% | 20% | 1 ÷ 0.004 = 250 | (250 × 5 min + 5 demos × 90 min) = 1,700 min = 28.33 h | 28.33 × 75 = $2,125 |
| Base | 10% | 50% | 25% | 1 ÷ 0.0125 = 80 | (400 + 4 × 90) = 760 min = 12.67 h | 12.67 × 75 = $950 |
| Optimistic | 20% | 50% | 50% | 1 ÷ 0.05 = 20 | (100 + 2 × 90) = 280 min = 4.67 h | 4.67 × 75 = $350 |

Break-even price for the base case: 3:1 needs LTV ≥ 3 × 950 = $2,850, so gross profit ≥ 2,850 ÷ 25 = $114/month, so ARPA ≥ 114 ÷ 0.80 = $142.50.

## Sanity check
- LTV:CAC, pessimistic: 0.5 vs 3 (critical, below 1). You would lose about $958 per customer (2,125 − 1,167).
- CAC payback, pessimistic: 30.4 months vs 12. Longer than your 7 months of runway by a wide margin.
- Monthly churn, pessimistic: 6% vs 5%. Retention data starts only after the first firms pay; until then this stays a range.
- LTV:CAC, base: 3.2 clears 3 by a thin margin. A $10 price cut or one more point of churn breaks it.
- Evidence: 100% of inputs are `[ASSUMPTION]`. Confidence is low. These are rough heuristics, not laws.
- Underpricing: can't tell yet, and that's a gap worth closing before the pilots convert. $150 came from the 90-day goal, not from what a slipped close costs a firm [NEED: hours lost per close, and who loses them]. If reviewers redo several hours of work every month, $150 is likely low. Don't cut below $150 to win the pilots. If both firms say yes on the spot, take that as a sign to quote higher to the next firm.

## Default alive?
Dead at current growth, which is expected with no revenue. Monthly burn isn't in company.md [NEED: monthly burn], so here it is per $10,000 of burn: break-even = 10,000 ÷ $120 base contribution margin = 83.3, so 84 paying firms. With about 7 months of runway that's 84 ÷ 7 = 12 new paying firms a month, against a 90-day goal of 3 in total. So the canvas can't get you to profitability on this runway at $10,000/month of burn; revenue has to grow much faster or money has to come in. If you plan to raise, pick the month to start now (several months before cash runs out) and route to fundraising. The per-customer economics and the survival math are separate questions; the pilots answer the first, not the second.

## Top 3 risks
1. **Revenue streams: firms will pay ≥ $150/month for close tracking on top of Karbon or TaxDome.** Likelihood 3 x impact 3 = 9. Nobody has been asked for money yet, and this is the biggest risk in your own file. Test below.
2. **Problem: partners rank close visibility in their top 3 pains.** 2 x 3 = 6. Test: re-read the 11 interview notes and count. Pass if ≥ 6 of 11 raised it unprompted.
3. **Channels: founder outreach converts near the base funnel.** 2 x 3 = 6 (ranks below problem on the tie-break). Test: 40 outreach messages to in-band firms. Pass if ≥ 4 replies and ≥ 2 demos.

## Riskiest block and next test
Revenue streams. Before the pilot starts next week, ask both pilot firms to sign a one-page conversion agreement: free for 30 days, then $150/month unless they cancel before day 30. In the same 14 days, offer the 9 in-band waitlist firms a paid founding pilot at $150/month. Pass if ≥ 3 written commitments (signed agreement or card on file) by 2026-11-04. Fail at ≤ 1: stop feature work and run pricing-strategy and customer-research on why. At exactly 2, extend 14 days with 10 more firms. You will want to argue the free pilot proves enough. It does not: free usage tests the problem, not the payment.

## Open data
- [NEED: monthly burn, to check the test fits inside 7 months of runway and to finish the default-alive check]
- [NEED: hours lost per close at the pilot firms, for the underpricing check]
- [NEED: how many of the 11 interviews raised blocked-client visibility unprompted]
- [NEED: what the pilot firms pay today for Karbon or TaxDome, from the firms themselves]
- [NEED: founder hours per pilot firm per month]
- [NEED: whether the 2 pilot firms are among the 9 in-band waitlist firms]

## Logged
```markdown
### 2026-10-21 — decision: Lean canvas v1 for small bookkeeping firms
- Verdict: works only if price ≥ ~$143/month and base funnel holds; base LTV:CAC 3.2, payback 7.9 months
- Key assumptions: $150 ARPA, 80% GM, 4% monthly churn, $950 founder-time CAC (all [ASSUMPTION])
- Riskiest block: revenue streams (score 9). Test: paid conversion agreements with 2 pilots + 9 waitlist firms. Pass if ≥ 3 commitments at ≥ $150/month by 2026-11-04
- Source: lean-canvas
```
