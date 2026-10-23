# Instruments: SAFE (post-money) vs priced round

> This is general information, not legal or financial advice. Instruments, standard forms, tax treatment, and securities rules vary by jurisdiction and change over time. Confirm with counsel before signing or offering anything.

Explain neutrally. Do not recommend a valuation, cap, or discount. Show math with the founder's numbers.

## SAFE (Simple Agreement for Future Equity), post-money

A contract where the investor pays now and receives equity later, usually at the next priced round. The widely used standard forms originate with Y Combinator; the founder should get the current version from the source and have counsel review any changes.

**Key terms**
- **Post-money valuation cap:** the maximum valuation at which the SAFE converts, measured after all SAFEs convert. Makes the investor's ownership at conversion straightforward to calculate: ownership ≈ investment ÷ post-money cap (before the new round's dilution).
- **Discount:** optional; the SAFE converts at a percentage off the next round's price. Some SAFEs have a cap only, some discount only, some both (investor gets the better result).
- **MFN (most favoured nation):** optional; the investor can adopt better terms given to later SAFE holders.
- **Pro rata side letter:** optional; right to invest in a future round to maintain ownership.

**Characteristics (neutral)**
- Usually faster and cheaper to document than a priced round.
- No board seat or valuation negotiation in the usual form.
- Can be closed investor by investor (rolling close).
- Dilution is deferred, not avoided. Multiple post-money SAFEs stack: each one dilutes founders, and founders bear the dilution from all SAFEs.
- Not equity until conversion; investors are not shareholders until then.
- Jurisdiction matters: SAFEs are common in the US; other regions use their own instruments (e.g. advance subscription agreements, convertible loan notes). Ask counsel what is standard locally.

**Dilution sketch (founder's numbers only)**
```
SAFE total raised:           [$S]        (founder-provided)
Post-money cap:              [$C]        (founder-provided / negotiated)
SAFE holders' ownership ≈    S ÷ C       (before next round and option pool changes)
Founders after conversion ≈  current ownership × (1 − S ÷ C)   [ASSUMPTION: no pool top-up]
```
Then apply the next priced round's dilution and any option pool increase. Flag that pool increases are often required in the pre-money of the next round.

## Convertible note

Debt that converts to equity. Similar cap and discount mechanics to a SAFE, plus interest and a maturity date. Mention when the founder's jurisdiction or investors prefer notes; note that maturity creates a repayment or renegotiation point.

## Priced round (preferred equity)

Investors buy shares at a set price per share, based on an agreed pre-money valuation.

**Key terms**
- **Pre-money / post-money valuation:** post = pre + new money. Investor ownership = new money ÷ post-money.
- **Option pool:** often expanded before the round (in the pre-money), which dilutes existing holders, not the new investor.
- **Liquidation preference:** what preferred holders get back before common in an exit. 1x non-participating is common at early stage; anything higher or participating is materially more investor-favourable. Explain, do not judge.
- **Board composition, protective provisions, pro rata, information rights, anti-dilution (usually broad-based weighted average).**

**Characteristics (neutral)**
- More legal work and cost; usually a lead investor sets terms.
- Clear cap table immediately after close.
- Governance terms (board, consents) are set now.
- Single or few closes, coordinated.

## Comparison

| | SAFE (post-money) | Priced round |
|---|---|---|
| Speed / cost | Usually lower | Usually higher |
| Valuation set now | Cap only | Yes |
| Board / governance | Usually none | Usually yes |
| Closing | Rolling | Coordinated |
| Cap table clarity now | Requires modelling | Immediate |
| Typical use | Pre-seed, some seed | Seed (varies), Series A |

## Questions to bring to counsel
- Which instrument is standard in our jurisdiction and with our likely investors?
- What does the cap table look like after all SAFEs convert at a range of next-round prices?
- Are there tax or securities filing requirements for this round?
- Can we accept investors who are not accredited / qualified in our jurisdiction?
- What side letters are we being asked for, and what do they commit us to?
