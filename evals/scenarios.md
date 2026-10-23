# Eval scenarios

One realistic request per skill, run against `fixture-company.md` (Ledgerline). Use these to regression-test the pack after edits: load the skill, give the agent the fixture as `.foundora/company.md`, send the request, and grade the answer with the rubric below.

| Skill | Request | A strong answer must |
|---|---|---|
| cofounder | "Be my cofounder. What should I work on this week?" | Give the 3-line brief from the file; tie the week to the pilot starting and the "will they pay separately" risk; ask exactly one question; end with one binary win |
| idea-validator | "Tear this idea apart and give me a verdict." | Score H1–H7 with caps; PROVISIONAL or KEEP TESTING (11 interviews, no commitments involving money); name the incumbent-feature risk; cheapest money test |
| lean-canvas | "Fill in my lean canvas and tell me if the economics can work." | One segment; price as [ASSUMPTION]; scenarios not a single LTV; riskiest block = revenue/willingness to pay or channel, with a test |
| customer-research | "Write an interview script for the pilot firms' ops leads." | Research question tied to paying separately; no pitching before the end; past-behavior questions about current tool spend |
| mvp-scoper | "We're about to build integrations with QBO and Xero. Scope the MVP." | Push back: integrations don't test the riskiest assumption; concierge pilot + paid conversion threshold derived from the 90-day goal |
| positioning | "How do we position against Karbon and TaxDome?" | Alternatives include spreadsheets and doing nothing; big-fish-small-pond reasoning; swap test applied; [NEED: proof] where missing |
| website-design | "Design our waitlist landing page." | Material world from bookkeeping (ledgers, tick marks, close calendars), named hex palette with contrast, type scale, one signature moment, banned tells avoided, [NEED] for proof |
| landing-page-copy | "Write the hero section." | 3 headline options with angles; no invented customers or metrics; passes the three-question gate |
| pricing-strategy | "What should we charge?" | Value metric candidates scored (clients closed per month vs seats); charge the pilots; test plan with thresholds; no invented competitor prices |
| launch | "Plan our launch for when the pilots convert." | Readiness gate first; B2B channels (founder LinkedIn, bookkeeping communities, practice-tool marketplaces); targets from their own 62-person waitlist |
| video-script | "Write a 60-second demo video script." | Hook in 2s on the messy spreadsheet; word budget respected; captions-first; no fake customers |
| cold-outreach | "Write outreach to book 10 more interviews with managing partners." | Under 90 words; one ask; signal placeholders not invented facts; 3–4 touch sequence |
| pitch-deck | "Outline our pre-seed deck." | Narrative first; validation slide (not traction); bottom-up market math with placeholders; incumbent objection answered |
| fundraising | "Should we raise now?" | Uses 7 months runway; likely "raise after the pilots convert" with the milestone; disclaimer; no investor names |
| investor-update | "Write this month's update for our 4 angels." | Lowlights present; metrics only from the file, missing ones as [NEED]; specific asks |
| weekly-review | "Set up my weekly review." | Setup mode; North Star tied to paid pilots; inputs include the risk; kill list non-empty |
| company-context | "Help me set up my company context file." | Asks in small batches; writes the exact company.md format; confirms before overwriting |

## Rubric (score each 0–2, ship at 10+/12)

1. **Context use** — uses the fixture's facts without re-asking; asks only for genuinely missing inputs.
2. **Honesty** — no invented numbers, customers, quotes, competitors' prices; gaps marked `[NEED: ...]`, guesses `[ASSUMPTION]`.
3. **Decision quality** — applies the skill's decision rules and reaches a clear verdict or recommendation.
4. **Pushback** — challenges the founder where the evidence says to.
5. **Format** — matches the skill's output template and the founder's tone preference.
6. **Actionability** — ends with a concrete next step with a date or threshold.
