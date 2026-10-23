# Instruments: SAFE (post-money) vs priced round

> General information, not legal, tax, or financial advice. Instruments, standard forms, tax treatment, and securities rules vary by jurisdiction and change over time. Confirm with counsel before signing or offering anything.

Explain neutrally. Do not recommend a valuation, cap, or discount. Show math with the founder's numbers. The arithmetic examples below use round illustrative numbers to show mechanics only; never present them as typical terms.

## SAFE (Simple Agreement for Future Equity), post-money

A contract where the investor pays now and receives equity later, usually at the next priced round. The widely used standard forms come from Y Combinator; the founder should get the current version from the source and have counsel review any changes.

**Key terms**
- **Post-money valuation cap:** the valuation used for conversion, measured after all SAFEs and other converting securities convert, but before the new money in the priced round.
- **Ownership when the cap applies:** each holder owns roughly purchase amount ÷ post-money cap of the company immediately before the priced round. If the priced round's price is below the cap price, the SAFE converts at the round price (or the discount price, if it has one and that is lower), and the holder owns more than that.
- **Discount:** optional; converts at a percentage off the next round's price. Some SAFEs have a cap only, some a discount only, some both (the investor gets the lower price).
- **MFN (most favoured nation):** optional; the holder can adopt better terms given to later SAFE holders before the priced round.
- **Pro rata side letter:** optional; right to invest in a future round to maintain ownership.

**Characteristics (neutral)**
- Usually faster and cheaper to document than a priced round.
- No board seat or price-per-share negotiation in the usual form.
- Can be closed investor by investor (rolling close).
- Dilution is deferred, not avoided. Post-money SAFEs stack: each one's percentage is fixed, so founders and other existing holders absorb the dilution from all of them.
- In the YC post-money form, the capitalization used for conversion includes the existing option pool, and a pool increase made as part of the priced round is generally excluded (except to cover promised options). That increase therefore dilutes founders, not SAFE holders. Check the version actually signed.
- Not equity until conversion; holders are not shareholders until then.
- Jurisdiction matters: SAFEs are common in the US. Other regions use their own instruments (for example advance subscription agreements in the UK, often for tax-relief schemes, and convertible loan agreements in much of Europe). Ask counsel what is standard locally.

**Dilution sketch (founder's numbers only)**
```
SAFE i raised:               [$S_i]      (founder-provided)
SAFE i post-money cap:       [$C_i]      (founder-provided / negotiated)
SAFE holders' ownership ≈    Σ (S_i ÷ C_i)            (cap applies; before the priced round)
Founders after conversion ≈  founders' current fully diluted % × (1 − Σ (S_i ÷ C_i))
Then priced round:           founders × (1 − new money ÷ post-money), minus any pool increase
```

Illustrative arithmetic only: $0.5M on a $5M post-money cap is 10%; $1M on a $10M cap is another 10%. SAFE holders own about 20%, so founders at 100% fall to about 80%. A priced round of $3M at a $12M pre-money ($15M post) sells 3 ÷ 15 = 20%, taking founders to about 80% × 0.8 = 64%, before any pool increase in the pre-money.

## Convertible note

Debt that converts to equity. Cap and discount mechanics similar to a SAFE, plus an interest rate (accrued interest usually converts with the principal) and a maturity date. Maturity creates a repayment or renegotiation point. Common where local law or investors prefer debt instruments.

## Priced round (preferred equity)

Investors buy shares at a set price per share based on an agreed pre-money valuation.

**Key terms**
- **Pre-money / post-money valuation:** post = pre + new money. New investors' ownership = new money ÷ post-money. Price per share = pre-money ÷ pre-money fully diluted shares (which usually include converting SAFEs and notes, and the expanded pool).
- **Option pool:** often expanded in the pre-money, so the increase dilutes existing holders, not the new investor. This lowers the effective pre-money; model it explicitly.
- **Liquidation preference:** what preferred holders get back before common in an exit. 1x non-participating is common at early stage; higher multiples or participation are materially more investor-favourable. Explain, do not judge.
- **Board composition, protective provisions, pro rata, information rights, anti-dilution** (broad-based weighted average is the most common form; full ratchet is rare and much more investor-favourable).

**Characteristics (neutral)**
- More legal work and cost; usually a lead investor sets terms.
- Clear cap table immediately after close.
- Governance terms (board, consents) are set now.
- One or a few coordinated closes.

## Comparison

| | SAFE (post-money) | Priced round |
|---|---|---|
| Speed / cost | Usually lower | Usually higher |
| Valuation set now | Cap only | Yes |
| Board / governance | Usually none | Usually yes |
| Closing | Rolling | Coordinated |
| Cap table clarity now | Requires modelling | Immediate |
| Typical use (varies by market) | Pre-seed, often seed | Seed in some markets, Series A |

## Reading a term sheet (neutral checklist)

List each term in a table with the exact wording, what it means in one line, and the counsel question. Do not label terms good or bad.

| Term | What to record |
|---|---|
| Amount and instrument | Total, lead's share, minimum close |
| Valuation or cap | Pre or post, with or without the pool increase |
| Option pool | Size after close, and whether it sits in the pre-money |
| Liquidation preference | Multiple, participating or not |
| Board | Seats by group, observer rights |
| Protective provisions | Actions that need investor consent |
| Pro rata, information rights | Thresholds |
| Anti-dilution | Type |
| Founder vesting | Any reset or acceleration |
| No-shop / exclusivity | Length in days, what it covers |
| Expiry and closing conditions | Dates, diligence items |

## Questions to bring to counsel
- Which instrument is standard in our jurisdiction and with our likely investors?
- What does the cap table look like after all SAFEs convert at a range of next-round prices, with and without a pool increase?
- Are there tax or securities filing requirements for this round?
- Can we accept investors who are not accredited or qualified in our jurisdiction?
- What do the side letters (pro rata, MFN, information rights) commit us to?
- What does the no-shop restrict, and for how long?
