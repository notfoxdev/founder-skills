# Unit economics reference

Read this when computing unit economics, interpreting results, or estimating with little or no data. Every input in the founder's table must carry a source tag: founder-provided, calculation, `[ASSUMPTION]`, or public source the founder should verify.

## Core formulas (subscription / SaaS)

Use monthly figures throughout. Convert annual figures before plugging in. These definitions are shared with pricing-strategy; keep them identical if either skill changes.

| Metric | Formula | Notes |
|---|---|---|
| MRR | Sum of monthly recurring revenue from paying customers | Annual contracts ÷ 12 |
| ARPA | MRR ÷ paying customers | Use per-account, not per-seat, unless pricing is per-seat and you model seats |
| COGS | Hosting, inference/API costs, third-party licences per customer, payment fees, customer support and onboarding labour | Not R&D, not sales |
| Gross margin % | (Revenue − COGS) ÷ Revenue | |
| Gross profit / customer / month | ARPA × Gross margin % | The denominator of payback and the monthly building block of LTV |
| CAC | (Sales + marketing spend in period, fully loaded) ÷ new paying customers in period | Include salaries, tools, ads, agencies, events, founder sales time at a stated rate |
| Monthly churn (logo) | Customers lost in month ÷ customers at start of month | |
| Revenue churn | MRR lost (cancellations + downgrades) ÷ MRR at start of month | Use when ARPA varies a lot |
| Lifetime (months) | 1 ÷ monthly churn | Cap at 36 months pre-PMF, 60 months post-PMF. Tiny churn on a small sample produces fantasy lifetimes |
| LTV | ARPA × Gross margin % × Lifetime | Equivalent: ARPA × GM% ÷ monthly churn (before the cap) |
| LTV:CAC | LTV ÷ CAC | |
| CAC payback (months) | CAC ÷ (ARPA × Gross margin %) | Months of gross profit to recover acquisition cost |
| Max allowable CAC | LTV ÷ 3 | The most you can spend per customer and still hit the 3:1 heuristic |
| Contribution margin / customer / month | ARPA − all variable costs per customer | Variable costs = COGS + any variable selling cost (commissions, affiliate fees, transaction fees) |
| Contribution margin % | Contribution margin ÷ ARPA | |

Annual churn to monthly: monthly = 1 − (1 − annual)^(1/12). Dividing annual churn by 12 understates monthly churn and overstates lifetime, and the error grows as churn rises (50% annual is about 5.6% monthly, not 4.2%).

### Blended vs. paid CAC

- **Blended CAC** includes organic customers and makes economics look better.
- **Paid / channel CAC** isolates one channel. Use it for decisions about where to spend.
- Report both when data allows. If only blended is available, note it.

### Expansion

If customers reliably upgrade or add seats, net revenue retention (NRR) matters more than logo churn.
NRR = (Starting MRR + expansion − contraction − churned MRR) ÷ Starting MRR, measured over 12 months on a cohort.
Do not model expansion without at least a few months of observed upgrades. Tag it `[ASSUMPTION]` otherwise.

## Variants

### B2C subscription
Same formulas. Churn is usually higher and CAC more channel-dependent. Model per-channel CAC (paid social, app store search, referral) separately; blended numbers hide that one channel may be unprofitable.

### Transactional / e-commerce
- Contribution per order = AOV − COGS − shipping − payment fees − returns allowance − variable marketing per order.
- LTV = contribution per order × expected orders per customer over a fixed window (12 or 24 months).
- Expected orders comes from observed repeat rate. Without data, model 1 order (no repeat) as the pessimistic case.

### Marketplace
- Net revenue = GMV × take rate.
- Contribution per transaction = take rate revenue − payment fees − trust/safety, support, insurance, incentives per transaction.
- Compute CAC separately for each side. The cheaper-to-acquire side is often subsidised; make the subsidy explicit.
- Liquidity (share of listings or requests that result in a transaction) is a key metric before unit economics stabilise.

### Usage-based
- ARPA varies with usage. Use median and 25th percentile, not mean, when a few large accounts skew it.
- Gross margin must be computed per unit of usage (price per unit − cost per unit). Inference-heavy AI products often have margins that move with model pricing and usage mix; recompute when either changes.
- Check margin at the 90th percentile customer, not only the median. A flat price with uncapped usage can make heavy users unprofitable while the average looks fine.

## Heuristic ranges

These are commonly cited ranges for early orientation. They vary by segment, geography, year, and source. Present them as "rough heuristics the founder should sanity-check against current public data for their segment", never as targets.

| Metric | Rough heuristic | Context |
|---|---|---|
| LTV:CAC | 3:1 or better is the usual rule of thumb | Well above 5:1 can mean under-investing in growth |
| CAC payback | Under ~12 months SMB/self-serve; ~12–24 months mid-market/enterprise | Longer is survivable only with strong funding and retention |
| Gross margin, SaaS | Often ~70–85% | AI/inference-heavy or services-heavy products often lower |
| Gross margin, marketplace (on net revenue) | Often ~60–80% | Depends on payments, insurance, support |
| Gross margin, e-commerce | Wide, often ~30–60% | Category-dependent |
| Monthly logo churn, SMB | Often ~3–7% | Very small businesses churn more |
| Monthly logo churn, mid-market | Often ~1–2% | |
| Monthly logo churn, enterprise | Often under 1% | Annual contracts make this lumpy |
| Marketplace take rate | Often ~5–30% | Higher where the platform does more of the work |

## Estimating with no data

Pre-revenue founders still need a rough model. Build it bottom-up from observable steps, tag every input, and run three scenarios.

### CAC from a funnel
CAC = cost per lead ÷ (lead → customer conversion rate)

Or step-by-step for outbound:
- Founder hours per closed deal = (messages to send ÷ reply rate ÷ meeting rate ÷ close rate) × minutes per touch, plus meeting and follow-up time.
- CAC = hours × stated hourly value + tool costs per deal.

For paid channels:
- CAC = CPC ÷ (click → signup rate × signup → paid rate).
- CPC must come from the ad platform's own estimate tool or a small test spend, not from memory. Tag `[NEED: CPC from a test]` until then.

### Churn without history
- Use the heuristic range for the segment as pessimistic/base/optimistic, tagged `[ASSUMPTION]`.
- Switch to observed cohort churn once you have at least 3 months and about 20 customers. Before that, show observed churn next to the heuristic range with the sample size, and model on the range.

### Gross margin without history
- List every per-customer cost line: hosting, inference per action × expected actions, third-party APIs, payment fees, support minutes × hourly cost.
- Ask for any vendor price the founder already pays. Do not supply vendor prices from memory; mark `[NEED: current vendor price]`.

### Work backwards
When almost everything is unknown, flip the question:
1. Take the intended price and an assumed gross margin.
2. Take a pessimistic lifetime (e.g. 12–18 months for SMB).
3. Compute LTV, then max allowable CAC = LTV ÷ 3.
4. Ask: can the chosen first channel acquire a customer for less than that? If the honest answer is "unlikely", the model has a channel-price mismatch now, before any money is spent.

## Worked example (illustrative numbers only)

Inputs: ARPA $200/month [ASSUMPTION], gross margin 80% [ASSUMPTION], monthly churn 4% [ASSUMPTION], CAC $1,500 [calculation from funnel].

- Gross profit per month = 200 × 0.80 = $160
- Lifetime = 1 ÷ 0.04 = 25 months (under the 36-month cap)
- LTV = 160 × 25 = $4,000
- LTV:CAC = 4,000 ÷ 1,500 = 2.7 → below the 3:1 heuristic, flag
- Max allowable CAC = 4,000 ÷ 3 = $1,333 → CAC must fall by about $167 to clear 3:1
- Payback = 1,500 ÷ 160 = 9.4 months → within SMB heuristic

Reading: payback is acceptable but LTV:CAC is thin. Levers in order of usual ease: reduce churn, raise price, improve conversion to cut CAC.

## Common mistakes

| Mistake | Effect | Fix |
|---|---|---|
| LTV on revenue, not gross profit | Overstates LTV by the COGS share | Multiply by gross margin |
| Excluding salaries or founder time from CAC | CAC looks tiny | Fully load CAC |
| Annual churn treated as monthly (or vice versa) | Lifetimes off by an order of magnitude | Convert explicitly |
| Uncapped lifetime from 0–1% churn on 10 customers | LTV in fantasy territory | Cap lifetime, note sample size |
| Blended CAC used for channel decisions | Unprofitable channels look fine | Split by channel |
| Mean ARPA with one whale | Model depends on one account | Use median, show the whale separately |
| Ignoring payment fees, support, onboarding | Gross margin overstated | List all variable costs |
