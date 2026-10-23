# Pricing models, value metrics, and packaging

Read this when choosing a model or value metric, designing tiers, or deciding between freemium and trials.

## Models

| Model | Works when | Breaks when | Watch for |
|---|---|---|---|
| Flat | One product, one buyer type, similar value across customers | Customers differ a lot in size or usage | Big customers pay the same as small ones; no expansion revenue |
| Tiered | Distinct segments with different needs and budgets | Tiers differ by trivial features | Too many tiers, unclear "who is this for" |
| Per-seat | Value scales with each active user; collaboration is the point | One power user does all the work; AI reduces headcount; customers share logins | Seat minimisation, login sharing, buyers resisting rollout |
| Active-user | Like per-seat, but you want broad rollout without punishing inactive users | Usage is spiky or hard to define | Definition of "active" must be clear and auditable |
| Usage-based | Value and cost both scale with consumption | Buyers cannot predict their bill; value is not tied to volume | Bill shock, budgeting friction, revenue volatility |
| Hybrid (platform fee + usage) | You need predictable base revenue and value alignment | The base fee buys nothing visible | Explain clearly what the base covers |
| Tiers with allowances + overage | Usage matters but buyers want predictability | Overage pricing feels punitive | Notify before overages; offer an upgrade path |
| Outcome / success-based | Outcome is measurable, attributable, and you control enough of it | Attribution is disputed | Long sales cycles, contract complexity |
| Transaction / take rate | Marketplaces, payments, bookings | Customers can move transactions off-platform | Disintermediation; justify the take rate with ongoing value |
| One-off + maintenance | Installed software, hardware, templates | Ongoing cost to serve is high | Revenue cliffs; pair with support or updates subscription |

## Value metric catalogue

Starting points, by product type. Score candidates with the 5-criterion table in SKILL.md.

| Product type | Candidate metrics |
|---|---|
| Collaboration / workspace | Seats, active users, workspaces |
| CRM / marketing | Contacts, emails sent, tracked accounts |
| Developer tools / APIs | API calls, compute minutes, requests, builds, environments |
| AI products | Tasks completed, documents processed, credits, messages, seats with usage allowance |
| Data / analytics | Events tracked, rows, data sources, dashboards viewers |
| Vertical SaaS | Locations, providers, vehicles, units, properties |
| Payments / fintech | % of volume, per transaction, accounts |
| E-commerce tools | Orders, GMV band, stores |
| Security / IT | Endpoints, employees covered, assets monitored |
| Content / media | Subscribers, downloads, hours of content |

Rules of thumb:
- Prefer metrics the customer already tracks (locations, employees, orders). They predict the bill without a calculator.
- Avoid metrics that make customers use less of the product to save money, if usage drives retention.
- AI inference costs: confirm the value metric keeps gross margin at or above 60% for the 90th percentile customer, not only the average. If it does not, add allowances, overage, or credits.
- If charging per seat would make the buyer withhold access from people who need to see the work (reviewers, approvers, clients), the metric works against adoption. Prefer an account-level metric.

## Free options

| Option | Use when | Avoid when | Key metric |
|---|---|---|---|
| Freemium | Near-zero marginal cost; large market; free users create value (virality, content, network); clear upgrade trigger | Small niche market; high cost to serve; value only in premium | Free → paid conversion; time to upgrade trigger |
| Free trial, no card | Time-to-value fits in the trial; light setup | Long setup or integration; value only after weeks | Trial → paid conversion; activation within trial |
| Free trial, card required | Strong intent; onboarding reliably delivers value | Top-of-funnel volume matters more than conversion | Trial → paid; refund requests |
| Reverse trial | Premium features are the hook; you also want a free base | Premium has little visible difference from free | Conversion at trial end; free retention |
| Paid pilot | Sales-led; ACV supports a call; integration required | Self-serve product under a few hundred dollars a year | Pilot → contract conversion |
| Money-back guarantee | Consumer or prosumer purchases with trust friction | High cost to serve in the guarantee window | Refund rate |

Trial length rule: long enough for a typical user to reach first value twice. If activation data does not exist, start at 14 days and adjust.

## Packaging

### Good / better / best
- **Good (entry):** solves the core job for the smallest viable buyer. Limits are on scale (usage, seats), not on the core value.
- **Better (recommended):** the full core product for the main persona. Most revenue should come from here.
- **Best:** for larger or more mature teams. Adds control, scale, and assurance.
- **Enterprise (optional):** contact sales. Security reviews, SSO/SAML, audit logs, custom contracts, SLAs, dedicated support, invoicing.

### Fences that work

| Fence | Example | Note |
|---|---|---|
| Usage limit | Up to N projects / contacts / tasks | Ties to value metric |
| Seats / users | Up to N users | Natural for collaboration |
| Maturity features | SSO, roles and permissions, audit logs, data retention controls | Large buyers need them; small ones do not miss them |
| Support level | Email vs. priority vs. dedicated | Cheap to offer, valued by larger buyers |
| Integrations | Core integrations everywhere; advanced (ERP, data warehouse) higher | |
| Commercial terms | Annual-only, invoicing, custom terms | Enterprise only |

### Fences that backfire
- Locking the core "aha" feature in the top tier.
- Limits so low that the entry tier cannot deliver value (customers churn before they upgrade).
- Feature differences buyers cannot understand from the pricing page.
- More than 3 self-serve tiers at launch.

### Add-ons
Use for features only a minority needs and that have clear standalone value (extra storage, an extra product module, premium support). Keep add-ons to 1–3 at early stage.

## Price changes

- New customers: raise anytime; update page and sales materials together.
- Existing customers: give at least 30 days' notice, explain what improved, offer an annual lock-in at the old price if possible.
- Grandfathering: decide upfront whether it lasts a fixed period or indefinitely. Indefinite grandfathering is simple but builds a long tail of underpriced accounts.
- Never raise prices and remove features in the same change.
