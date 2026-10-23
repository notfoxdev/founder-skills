# Changelog

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
