# Willingness-to-pay research

Read this when setting price levels from evidence. Stated willingness to pay is weaker than paid behaviour. Treat every method below as a way to narrow a range, then confirm with real purchases.

Which method, by stage:
- **No customers, fewer than ~30 reachable qualified buyers:** interviews with a named price, then a paid-pilot ask. Skip surveys.
- **30+ qualified respondents who understand the product:** Van Westendorp for the range, Gabor-Granger for points inside it.
- **Live pipeline or pricing page traffic:** behavioural tests beat any survey.

## Evidence ladder

| Level | Evidence | Weight |
|---|---|---|
| 0 | Founder opinion | Starting guess only |
| 1 | Competitor or alternative prices (founder-sourced, verified on their site) | Anchor, not answer |
| 2 | Interview statements ("I'd pay about...") | Directional |
| 3 | Van Westendorp or Gabor-Granger survey | Range, sample-size dependent |
| 4 | Verbal yes to a specific quoted price in a sales conversation | Moderate |
| 5 | Signed LOI, deposit, or paid pilot at the price | Strong |
| 6 | Self-serve paid conversion at the price | Strongest |

Always state the level reached next to any recommended price.

## Customer interviews

Goal: learn how they value the problem and what they spend today, before naming a price.

Sequence (30 minutes):
1. **Current spend and process.** "Walk me through how you handle <problem> today." "What does that cost you per month, in tools, people, or hours?" "Who approves that spend?"
2. **Cost of the problem.** "What happens when it goes wrong? How often? What did the last time cost?"
3. **Budget and buying process.** "If you bought something for this, whose budget does it come from?" "What is the largest purchase you can make without approval?"
4. **Value framing.** Show the solution or describe it. "What would change for you if this worked?" Push for numbers: hours, revenue, risk.
5. **Price reaction.** Name a specific price and watch the response. Do not ask "what would you pay?" first; people anchor low.
   - "We're planning <price> per <metric>. How does that land?"
   - Follow with "What would make that a clear yes?" and "At what point would it be a clear no?"
6. **Commitment test.** "Would you start a paid pilot at that price next month?" A yes without a next step does not count above level 2.

Read signals:
- Immediate yes, no questions → probably too low.
- Questions about details, terms, or approval → engaged, price within range.
- Pause, then "that's a lot" → near the upper bound; test value framing before lowering.
- Laughter or "we'd never pay that" from a well-qualified buyer → above range for this segment, or wrong value framing.

Log each interview: segment, role, current spend (stated), price named, reaction, commitment level.

## Van Westendorp Price Sensitivity Meter

Four open-ended price questions about a clearly described product. Practitioners use different question orders; pick one and keep it identical for every respondent:

1. At what price would this be so expensive that you would not consider buying it? (too expensive)
2. At what price would you start to think it is expensive, but still worth considering? (expensive)
3. At what price would you think it is a bargain, a great buy for the money? (cheap)
4. At what price would it be so cheap that you would doubt its quality? (too cheap)

Analysis:
- Plot cumulative distributions: "too cheap" and "cheap" descending with price; "expensive" and "too expensive" ascending.
- Commonly used intersection points:
  - **Point of marginal cheapness:** "too cheap" crosses "not cheap" (inverse of cheap).
  - **Point of marginal expensiveness:** "too expensive" crosses "not expensive" (inverse of expensive).
  - **Optimal price point:** "too cheap" crosses "too expensive".
  - **Indifference price point:** "cheap" crosses "expensive".
- The acceptable price range sits between marginal cheapness and marginal expensiveness.
- Conventions differ: some analysts define the marginal points with the "expensive" and "cheap" curves instead of their inverses. State which definition you used.
- The method gives an acceptable range, not purchase likelihood or a demand curve. The Newton-Miller-Smith extension adds purchase-likelihood questions at the respondent's own "cheap" and "expensive" prices if you need that.

Rules:
- Respondents must be in the target segment and understand the product. Show a description, demo, or screenshot first.
- Under ~30 qualified responses, report the range as directional. More is better; state n.
- Responses cluster on round numbers and current alternative prices. The method shows the acceptable range, not the revenue-maximising price.
- Segment results by persona or company size; blended results hide distinct ranges.

## Gabor-Granger

Measures purchase likelihood at specific prices, giving a rough demand curve.

Method:
1. Choose 4–6 price points spanning the plausible range (use Van Westendorp or interviews to set it).
2. Ask each respondent: "Would you buy <product> at <price>?" with a 5-point scale (definitely, probably, maybe, probably not, definitely not), or yes/no.
3. Start at a random or high price; move down after a no, up after a yes. Stop when the respondent's threshold is found.
4. For each price, compute % who would buy (count "definitely" fully and "probably" at a discount, for example 50%, to correct for overstatement; state the weighting).
5. Revenue index = price × % buying. The peak suggests a revenue-maximising price.

Rules:
- Same sample-size caution as Van Westendorp.
- Stated intent overstates real purchase. Use relative differences between price points, not absolute conversion.
- Check the peak against unit economics; the revenue-maximising price may still fail on CAC payback.

## Behavioural tests

Stronger than surveys. Prefer these as soon as there is traffic or a pipeline.

| Test | How | Read |
|---|---|---|
| Price laddering in sales | Quote a higher price to each next batch of 3–5 qualified prospects | Hold when close rate falls to about two-thirds of the previous step or lower. Batches this small are directional; look for a clear drop, not one lost deal |
| Pre-sale / deposit | Ask for a refundable deposit or annual prepay at the target price | % of qualified prospects who pay |
| Sequential cohort on pricing page | Change price for new visitors in a time-boxed window, compare to prior window | Conversion and ARPA per visitor; watch seasonality |
| Fake-door tier or add-on | Show the option; measure clicks; explain it is coming | Click-through as demand signal, not revenue |
| Annual plan uptake | Offer annual at a stated discount | % choosing annual; indicates confidence and cash |

Decision rule: a price increase that lowers conversion but raises revenue per visitor (or per qualified prospect) is usually a win at early stage, provided churn does not rise in the following cohorts.

## Ethics and practicality

- Do not mislead respondents about whether a product exists. "We're building this" is fine; fake checkout without disclosure is not.
- When testing different prices, have a policy for customers who discover a lower price (honour it).
- Keep interview notes free of sensitive personal data beyond what is needed.
