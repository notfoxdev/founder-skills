# Attribution

Foundora skills are original writing unless listed below. Where a skill adapts an open skill, the adaptation is rewritten in original text, extended for early-stage founders, and wired into the shared `.foundora/company.md` context. Each adapted SKILL.md ends with an attribution line describing the changes.

## Adapted from open skills

| Foundora skill | Source | License | What was adapted | Main changes |
|---|---|---|---|---|
| `website-design` | `frontend-design`, [anthropics/skills](https://github.com/anthropics/skills) | Apache-2.0 | Design-plan-before-build, review against generic defaults, "spend boldness in one place", writing-in-design guidance | Original text; company-context grounding; required palette/type-scale/spacing/wireframe plan; banned-tells list with swap and squint tests; token, Tailwind, a11y and performance guidance; pre-ship checklist; five reference files |
| `landing-page-copy` | `copywriting`, [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) | MIT | Diagnose-first approach, line-level quality gate, AI-tell avoidance | Original text; sourced message brief; section IDs shared with `website-design`; three-headline rationale format; AI-tells reference |
| `launch` | `launch`, [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) | MIT | Owned / rented / borrowed channel framework, phased launch | Original text; B2B vs B2C channel table; scored channel selection; operational blockers; dated T-30 to T+14 timeline; hourly run of show; bad-numbers playbook |
| `pricing-strategy` | `pricing`, [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) | MIT | Pricing model and packaging structure | Original text; value-metric scoring; acquisition-motion rules; early-stage pricing rules; unit-economics check |
| `cold-outreach` | `cold-email`, [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) | MIT | Cold email structure and sequencing | Original text; five use cases; signal verification; personalisation tiers; channel variants; deliverability and compliance basics |
| `human-voice` | `humanizer`, [blader/humanizer](https://github.com/blader/humanizer); `copy-editing`, [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) | MIT | Pattern-based removal of AI writing tells; edit passes | Original text and examples; fact ledger; founder voice from their own samples; voice notes logged to the journal; claims flagged, never softened |
| `competitor-teardown` | `competitors`, `competitor-profiling`, [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) | MIT | Competitor profiles, comparison pages | Original text; two-independent-source rule for "where we win"; dated public pricing only; incumbent next-build reading; fair battlecard; held public pages |
| `seo-content` | `content-strategy`, `seo-audit`, `ai-seo`, `programmatic-seo`, [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) | MIT | Content planning, technical SEO checks, answer-engine guidance | Original text; pages chosen from customer evidence and first-hand experience; no invented volumes; small-number measurement; programmatic SEO gated |
| `onboarding` | `onboarding`, `signup`, [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) | MIT | Activation and signup-flow patterns | Original text; aha moment from users who stayed; step-by-step cut rule; founder-led setup default; small-number test plan |
| `product-analytics` | `analytics`, `ab-testing`, [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) | MIT | Tracking plans, event naming, test sizing | Original text; 6–12 event cap tied to questions; "do we need a tool yet" decision; account identity; privacy basics; coding-agent hand-off |
| `sales-call` | `sales-enablement`, [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) | MIT | Discovery, demo and objection handling material | Original text; four-check qualifying; demo of the stated pain; paid-pilot terms; pipeline-honesty stages |
| `lifecycle-emails` | `emails`, [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) | MIT | Lifecycle sequences | Original text; 3–5 emails with a reason-to-exist test; hand-sent before automated; replies over opens |

The Apache-2.0 license text for the adapted `website-design` material is available at <https://www.apache.org/licenses/LICENSE-2.0>. The MIT notices for marketingskills and humanizer are reproduced in `LICENSE`.

## Methods credited (no text reproduced)

| Skill | Method | Credit |
|---|---|---|
| `idea-validator` | Customer interview rules and commitment classification | Rob Fitzpatrick, *The Mom Test* (2013) |
| `lean-canvas` | Lean Canvas (CC BY-SA) and Value Proposition Canvas lens | Ash Maurya; Alexander Osterwalder / Strategyzer |
| `positioning` | Positioning component order | April Dunford, *Obviously Awesome* |
| `launch` | Simple, Lovable, Complete readiness idea | Jason Cohen |
| `fundraising` | Standard SAFE forms are referenced, not reproduced | Y Combinator |

| `cofounder` | One-way / two-way doors; pre-mortem | Jeff Bezos, 2015 Amazon shareholder letter; Gary Klein, HBR 2007 |
| `positioning` | "For / who / is a / that / Unlike" statement shape | Geoffrey Moore, *Crossing the Chasm* |
| `customer-research` | Jobs, pains, gains; proto-personas | Osterwalder et al., *Value Proposition Design*; Jeff Gothelf, *Lean UX* |
| `mvp-scoper` | MVP and concierge; Wizard of Oz | Eric Ries; J. F. Kelley (1984) |
| `feature-spec` | Appetite, no-gos, rabbit holes; job stories | Ryan Singer, *Shape Up* (2019); Alan Klement |

### Founder advice (1.3.0, no text reproduced)

Decision rules across the pack draw on published founder advice, described in original wording and credited at the end of each SKILL.md:

| Method | Credit | Used in |
|---|---|---|
| Do things that don't scale; the Collison installation | Paul Graham, "Do Things That Don't Scale" (2013) | `mvp-scoper`, `onboarding`, `lifecycle-emails` |
| Weekly growth rate and its rule of thumb | Paul Graham, "Startup = Growth" (2012) | `weekly-review` |
| Default alive or default dead | Paul Graham (2015) | `cofounder`, `weekly-review`, `lean-canvas` |
| Write like you talk; write simply | Paul Graham (2015, 2021) | `human-voice`, `landing-page-copy`, `positioning`, `seo-content`, and others |
| How to get startup ideas | Paul Graham (2012) | `idea-validator` |
| How to raise money | Paul Graham (2013) | `fundraising` |
| Essential startup advice (launch now, 90/10 solution, rarely too early to charge) | Y Combinator | `mvp-scoper`, `pricing-strategy`, `launch`, `sales-call`, `competitor-teardown`, `feature-spec`, `lean-canvas` |
| The YC application questions as a clarity check | Y Combinator | `company-context`, `pitch-deck`, `positioning`, `competitor-teardown` |
| A guide to seed fundraising | Geoff Ralston, Y Combinator | `fundraising` |
| How to plan an MVP | Michael Seibel, YC Startup School | `mvp-scoper`, `feature-spec` |
| How to launch (again and again) | Michael Seibel, YC Startup School | `launch`, `video-script`, `motion-video` |
| Fake progress | Dalton Caldwell and Michael Seibel, YC podcast | `cofounder`, `weekly-review` |
| How to talk to users | Eric Migicovsky, YC Startup School | `customer-research` |
| How to get users and grow | Gustaf Alströmer, YC Startup School | `launch`, `onboarding`, `cold-outreach`, `lifecycle-emails`, `product-analytics` |
| How to set KPIs and goals; how to prioritize your time | Adora Cheung, YC Startup School | `weekly-review`, `cofounder`, `product-analytics` |
| How to evaluate startup ideas; pricing for startups; conversion rates | Kevin Hale, YC Startup School | `idea-validator`, `pricing-strategy`, `lean-canvas`, `landing-page-copy`, `website-design`, `onboarding` |
| How to get and evaluate startup ideas | Jared Friedman, Y Combinator (2022) | `idea-validator`, `competitor-teardown` |
| How to sell | Tyler Bosmeny, YC Startup School | `cold-outreach`, `sales-call` |
| How to sell to enterprises | Pete Koomen, YC Startup School | `sales-call` |
| Analytics for startups | Ilya Volodarsky, YC Startup School | `product-analytics` |
| Pitching legibly | Michael Seibel and Kevin Hale, YC Startup School | `pitch-deck`, `positioning` |
| People-first content; SEO starter guide | Google Search Central | `seo-content` |
| CAN-SPAM compliance guide | US Federal Trade Commission | `lifecycle-emails` |
| Signs of AI writing | WikiProject AI Cleanup (Wikipedia) | `human-voice` |

## Original

`cofounder`, `mvp-scoper`, `customer-research`, `video-script`, `motion-video`, `pitch-deck`, `investor-update`, `fundraising`, `weekly-review`, `idea-validator`, `lean-canvas`, `positioning`, `company-context`, `feature-spec`.
