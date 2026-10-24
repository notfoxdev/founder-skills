# Changelog

## 1.3.0 — 2026-10-23

Eight new skills, and every existing skill rewritten to sound more like a person and to lean on hard-won founder advice. The pack is now 26 skills.

**New skills**
- `human-voice`: paste anything you're about to post or send and get it back in your own voice. Every fact, number and name is kept, nothing is made up, and claims you can't back up are flagged before a customer calls them out. Share 2–3 things you wrote yourself and every skill reuses your voice notes.
- `competitor-teardown`: a fair, deep look at the one to three alternatives your buyers actually use, including the spreadsheet and doing nothing. Only calls something a win when two separate sources back it, and gives you a sales battlecard and a comparison page that would survive the competitor reading it.
- `feature-spec`: turns a feature idea into a spec you can review in two minutes and your coding agent can build without guessing: the job, a time box, what's deliberately out, numbered checks for done, and agent-sized build steps. Also trims a bloated PRD and turns a bug into a fix spec.
- `onboarding`: finds the moment your product clicks for new users from what the people who stayed actually did, cuts every step that doesn't need to come first, and tells you when setting customers up yourself beats building anything.
- `product-analytics`: the few numbers that matter with a handful of users, whether you need a tool yet, and a tracking plan of 12 events at most that your coding agent can wire up.
- `sales-call`: a one-page prep for every call, a demo that follows the pain the buyer just described, honest answers to the usual objections, and a close on one dated next step. Keeps your pipeline honest: no next meeting, no deal.
- `lifecycle-emails`: the 3–5 emails that matter at your stage instead of a 20-email drip, each sent from you, with one ask and replies coming straight back to you.
- `seo-content`: the handful of pages your buyers search for, written from your own experience, with a short technical checklist and no invented keyword numbers.

**Every skill**
- Sounds like a person. A new "Sound like a person" convention: plain words, your own phrasing from `company.md` and the journal, no AI tells, and a read-back as your sharpest customer would read it before anything goes out.
- Sharper decision rules built from widely taught founder advice: launch early and often, do things that don't scale, talk to users about the last time it happened, charge from day one, and know whether you're default alive.
- Version 1.3.0, routing updated for the new siblings.

**Highlights by skill**
- `cofounder`: flags busy work that no customer would notice, keeps building and talking to users in the top three, asks the default-alive question when runway is short, and routes to all 25 siblings.
- `weekly-review`: weekly growth of your main metric with a small-number caveat, users talked to as a standing row, and a monthly default-alive check.
- `idea-validator`: rates the problem itself (popular, growing, urgent, expensive, mandatory, frequent) and checks for four patterns that sink ideas before any code is written.
- `customer-research`: a fixed five-question interview spine about the last time the problem happened.
- `company-context`: a five-question clarity check before writing, without changing the file format.
- `mvp-scoper`: a one-line 90/10 version, concierge by default, and a fixed time box where scope gives way.
- `positioning`: a 50-character version and a legibility test.
- `pricing-strategy` and `lean-canvas`: an underpricing check and paid pilots by default.
- `launch`: the first launch is a plain email from you to a hand-picked group, with the next launches planned up front and retention before reach.
- `cold-outreach`: funnel counts at every stage and a push for a clear yes or no.
- `fundraising`: raise for the next milestone, investors in parallel, fast yes or no.
- `pitch-deck`, `investor-update`, `landing-page-copy`, `website-design`, `video-script`, `motion-video`: clarity checks, less friction, and words that sound like the founder.

## 1.2.0 — 2026-10-23

**New skill**
- `motion-video`: designs and builds motion-graphics videos in code (launch videos, teasers, feature clips, cutdowns, silent hero loops). Remotion license check before any build, a frame-accurate 30fps storyboard with a reading-time guard, brand motion tokens (easing, springs, durations in frames), scene components re-laid out per aspect, ffmpeg delivery recipes, and a 20-point self-check with truthfulness and accessibility gates. A license-free path (HTML/CSS captured with Playwright) is included.

**website-design**
- Content inventory before layout: sections exist only if they hold real content.
- 22 named AI-default tells (T1 to T22) with what to do instead, a code scan, and icon discipline built on a deletion test.
- Exact craft defaults: grid, 4px baseline, spacing scale, computed type scale with `clamp()`, tinted neutral ramps, the one-accent rule, motion durations and easing.
- Required pre-ship critique: 8 blockers, 9 named audits (squint, swap, tell scan, icon, contrast, mobile 375, keyboard, performance, content) and a 30-point scorecard with a ship threshold.

**video-script**
- Launch playbook: six concepts chosen by stage and audience, with second-by-second beats at 30, 60 and 90 seconds.
- Production mode (live capture, motion, hybrid), banned openers, exact word-budget math, text hold and size rules, 9:16 safe zones, and a 14-point self-check.
- Storyboard hand-off contract consumed by `motion-video`.

**Install prompt**
- The generated install prompt pins the `skills` CLI version and only allows the install and list commands; anything else in a draft (links, scripts, extra commands) sends it back to the standard prompt.

## 1.1.0 — 2026-10-23

**New skill**
- `company-context`: creates, updates and migrates `.foundora/company.md` through short interviews, shows a diff before every write, logs changes to the journal, and wires `CLAUDE.md` / `AGENTS.md`.

**Every skill**
- Spec compliance (agentskills.io): `license` field, `metadata.version: 1.1.0`, descriptions under 1024 characters, SKILL.md under 500 lines.
- New `## Edge cases` section: the situations where following the process literally goes wrong (no data, founder pushback, stage mismatch, out-of-scope requests) and what to do instead.
- Worked example in `references/example.md` for every skill, built on one fictional fixture company (`evals/fixture-company.md`) so depth, tone and format are calibrated.
- Response discipline: lead with the answer, one round of questions at most, draft with `[NEED: ...]` instead of stalling, short answers to point requests.
- One journal entry format across the pack.
- Vague rules turned into decision rules with thresholds (verdict rules, readiness math, price-raise steps, word budgets, sample floors).

**Accuracy fixes**
- Post-money SAFE mechanics and dilution math; round-size formula now applies the buffer to burn.
- Lean canvas and pricing share one set of unit-economics formulas; annual-to-monthly churn uses the compounding formula.
- Cold outreach: LinkedIn note limits, CAN-SPAM scope, Gmail/Yahoo bulk-sender rules, PECR sole-trader rule (framed as general information).
- Show HN and Product Hunt rules aligned with current guidelines and marked "verify current".
- Video word budgets now match their own formula.
- Positioning statement credited to Geoffrey Moore; one-way/two-way doors and pre-mortem credited.

**Behavioural eval fixes** (from running cofounder, pricing-strategy, website-design and company-context against the fixture)
- cofounder: derives candidates when the founder lists none; Next action line in the first reply; journal created if missing.
- pricing-strategy: founding offer instead of a tier table under 10 paying customers; goal prices count as level-0 evidence; concierge cost-to-serve edge case; LTV at two churn assumptions when churn is unknown.
- website-design: plan mode no longer pads with an empty critique; "page is not the bottleneck" scope-down; stack detection outside the site repo; no staged revisions.
- company-context: question ordering in update mode; paid-pilot labelling; trigger questions on point updates.

**Evals**
- `evals/scenarios.md`: one request per skill, "a strong answer must" criteria, and a 12-point rubric (ship at 10+).

## 1.0.0 — 2026-10-23

Initial pack: 16 skills.
