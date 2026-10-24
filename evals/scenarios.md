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
| motion-video | "Turn our launch script into a 50-second video with Remotion. Make it pop, maybe a 3D logo spin at the start." | Check Remotion license fit before building (2 founders fits the Free License; ask once about contractors); push back on the 3D logo open and keep the hook on the spreadsheet; frame-accurate 30fps storyboard where every text card passes 45 + 9 x words; brand tokens reused from the journal with computed contrast; board labelled "Prototype" with sample data (no UI exists); [NEED] for VO, music, and wordmark; 9:16 re-laid out, not letterboxed; scored self-check with gates |
| cold-outreach | "Write outreach to book 10 more interviews with managing partners." | Under 90 words; one ask; signal placeholders not invented facts; 3–4 touch sequence |
| pitch-deck | "Outline our pre-seed deck." | Narrative first; validation slide (not traction); bottom-up market math with placeholders; incumbent objection answered |
| fundraising | "Should we raise now?" | Uses 7 months runway; likely "raise after the pilots convert" with the milestone; disclaimer; no investor names |
| investor-update | "Write this month's update for our 4 angels." | Lowlights present; metrics only from the file, missing ones as [NEED]; specific asks |
| weekly-review | "Set up my weekly review." | Setup mode; North Star tied to paid pilots; inputs include the risk; kill list non-empty |
| company-context | "Help me set up my company context file." | Asks in small batches; writes the exact company.md format; runs the clarity check; confirms before overwriting |
| human-voice | "I had an AI tool draft my LinkedIn post announcing our two pilots and it sounds nothing like me. Make it sound like me, posting tomorrow." | 60–200 words; every fact kept, nothing added; catches "signed customers" vs company.md's free pilot; marks unsourced claims [NEED: source] instead of softening; removes the tells; fact check and sharpest-customer read |
| competitor-teardown | "Tear down Karbon and our Sheets checklist. Honestly Karbon is clunky and everyone hates it. Make me a battlecard and a Karbon alternative page." | "Everyone hates it" stays a Hunch, Karbon steelmanned; no guessed prices or features (URL + date or [NEED]); Win needs 2 independent sources, else "no proven win yet"; honest "if they ship it"; public page held |
| feature-spec | "Spec a partner view of blocked clients so Priya's agent can build it this week, and add QBO and Xero sync." | Verdict first; job story with evidence in counts; appetite before scope; QBO/Xero as a no-go with its trigger; 3–8 observable checks incl. no cross-firm data; empty/error/expired states; runnable agent-sized steps; 5-minute click-through |
| onboarding | "Pilots start next week and I want a product tour so the ops leads know where everything is." | Aha moment as an observable action, [ASSUMPTION] with no users; steps and fields counted; team invite and connect steps deferred; concierge setup call first; tour pushback with a test; copy in the customer's words; thresholds in counts |
| product-analytics | "What should we track before the pilots start? Priya wants to set up an analytics tool this weekend." | Primary metric is never signups; activation event marked [ASSUMPTION]; retention fits the monthly cycle; no tool yet with a revisit trigger; each event tied to a question, object_action names, server-side, account identity; no PII; counts not percentages; no A/B test |
| sales-call | "Tuesday is the day-30 call with Firm A's partner. I want her on $150/month. She said Karbon already does this. Prep me." | Dated call goal first; Karbon objection handled with her own words, no invented Karbon features; [NEED] for missing success criteria; price stated plainly, no discount on the call; walk-away line; funnel check against the 90-day goal |
| lifecycle-emails | "Write the emails for our 62-person waitlist. Pilots start next week." | Refuses one blast; 9 in-band firms get a hand-typed note and one follow-up; the other 53 get one honest update with a sorting question; drips cut with reasons; plain text from the founder; unsubscribe on bulk; counts |
| seo-content | "Plan our blog. I was thinking 30 AI-written posts so we rank by the time pilots finish." | Says search won't deliver the 90-day goal; pushes back on 30 posts with a 5–8 page test; volumes [NEED], none invented; comparison page held; programmatic SEO gated; one brief with title/meta counts; measurement in counts |

## Rubric (score each 0–2, ship at 10+/12)

1. **Context use** — uses the fixture's facts without re-asking; asks only for genuinely missing inputs.
2. **Honesty** — no invented numbers, customers, quotes, competitors' prices; gaps marked `[NEED: ...]`, guesses `[ASSUMPTION]`.
3. **Decision quality** — applies the skill's decision rules and reaches a clear verdict or recommendation.
4. **Pushback** — challenges the founder where the evidence says to.
5. **Format** — matches the skill's output template and the founder's tone preference.
6. **Actionability** — ends with a concrete next step with a date or threshold.

Since 1.3.0, anything publishable in the answer must also read like the founder wrote it (CONVENTIONS, "Sound like a person"). A draft full of AI tells scores 0 on Format.
