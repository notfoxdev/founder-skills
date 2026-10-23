# Market sizing (bottom-up)

> General method guidance, not financial advice. Every count, rate, and price must be founder-provided, a shown calculation, or a public source the founder verifies before the deck goes out.

Investors discount top-down sizing ("$80B market, we take 1%") to zero. Use bottom-up math they can check. A top-down figure from a public report may appear only as a cross-check, labelled with its source for the founder to verify.

## Definitions

- **TAM (total addressable market):** every buyer who could ever use this product category, at a realistic price, per year.
- **SAM (serviceable addressable market):** the part of TAM the current product and business model can serve (segment, geography, language, compliance, channel).
- **SOM (serviceable obtainable market):** what the company can realistically win in a defined period (usually 3–5 years) given its go-to-market capacity.

## The method

Write the math on the slide. Every input gets a source tag.

1. **Define the buyer unit.** The entity that pays: a company of type X with Y employees, a clinic, a household, a creator. One unit per row.
2. **Count the units.** Source options, in order of preference:
   - Public registries or government statistics (business counts by industry code, census data).
   - Industry associations or published directories.
   - Platform counts (number of stores on a platform, listed businesses) from the platform's own disclosures.
   - Founder's own scrape or list, with method described.
   Mark every count "(public source, founder to verify)" unless the founder supplied it.
3. **Set the price per unit per year.** Use the actual price charged, or the tested price, or the price of the current alternative being replaced. Mark `[ASSUMPTION]` if not yet tested. Convert monthly prices to annual (× 12) and say so. If pricing is per seat or per usage unit, multiply by the realistic number of seats or units per buyer, not the maximum.
4. **Multiply.** TAM = units × annual price. For usage or transaction models: units × transactions per year × average transaction value × take rate.
5. **Filter to SAM.** Apply explicit filters the product actually has today: geography, segment size, tech stack, regulation. Show each filter with its percentage and source.
6. **Derive SOM from go-to-market, not a percentage.** SOM = what the sales and marketing capacity can realistically close.
   - Sales-led: reps × deals per rep per year × ACV × years, ramped.
   - Self-serve: reachable audience per channel × conversion × ARPU × retention.
   - Cross-check: SOM as a share of SAM. Heuristic, not a rule: if it exceeds roughly 10% of SAM in 5 years, explain why or revise.
   - Pre-revenue: deals per rep or conversion rates are not yet known. Leave them as `[NEED: ...]` or `[ASSUMPTION]` and say which milestone will replace them with real numbers.
7. **Sanity checks.**
   - Does the SAM support a company at the scale the round implies? A seed investor generally needs a path to a large outcome; if SAM is small, show the expansion path (adjacent segments) rather than inflating it.
   - Is the price consistent with the business model slide?
   - Are the units the same ones named on the problem slide?

## Worked method (structure only; all figures are placeholders)

```
Buyer unit: independent dental clinics with 2–10 chairs
Units (country A):         [N_clinics]           (public source, founder to verify)
Annual price per clinic:   [$P]                  (founder-provided: current list price)
TAM (country A) = N_clinics × $P

SAM filters:
  Uses cloud practice software:   [f1 %]         (public source, founder to verify)
  English-language markets live:  [f2 %]         (founder-provided)
SAM = TAM × f1 × f2

SOM (5 years, sales-led):
  Reps by year 5:                 [R]            [ASSUMPTION]
  Deals per rep per year:         [D]            (founder-provided: current rate)
  ACV:                            [$P]
  Ramped years equivalent:        [Y]            [ASSUMPTION]
SOM = R × D × $P × Y
Check: SOM / SAM = [x %]
```

When filling this in, replace every bracket with a sourced number or leave it as `[NEED: ...]`. Never fill a bracket with a guessed figure presented as fact.

## Slide presentation

- Headline as a claim: "There are [N] clinics paying $[P]/yr for tools we replace: a $[TAM] market."
- Show the multiplication, not just the result.
- Three numbers max (TAM, SAM, SOM), each with its one-line derivation.
- Footnote the sources.

## Common mistakes

- Using a research-firm industry total as TAM for a niche product.
- Counting users instead of buyers.
- SOM as an arbitrary "1–5% of TAM".
- Mixing geographies between steps.
- Pricing in the market slide that differs from the business model slide.
- Including segments the product cannot serve for years.
- Using the total spend of a broader category (all accounting software, all HR software) as TAM for a product that replaces one workflow.
- Mixing monthly and annual prices between rows.
