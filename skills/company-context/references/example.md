# Worked example: company-context (create mode)

> Illustrative and fictional (Ledgerline fixture). Calibrates depth and format only; never reuse its content.

**Request:** "Help me set up my company context file."

**Context used:** no `.foundora/company.md`, no journal, no `CLAUDE.md` or `AGENTS.md` in the repo. Nothing pasted. Every fact below comes from the founder's replies (condensed); the agent's messages are shown in full. Date: 2026-10-20.

---

**Agent, round 1**

**Creating `.foundora/company.md`: round 1 of 5, Snapshot**
No company file found, so I'll build one. Five short rounds, three questions each; skip anything. Or paste a deck or notes and I'll only ask about gaps.
1. What are you building, in one line, and for whom?
2. Which stage fits best: idea, validation, mvp, early-traction, or growth?
3. How do you make money (or plan to, roughly at what price), and do you have a website yet?

> Founder: "Month-end close checklist and reconciliation tracker for bookkeeping firms with 3–15 staff. We're pre-seed, kind of in beta. SaaS, probably around $150 a month per firm. ledgerline.app, just a waitlist."

**Agent, round 2**

"Pre-seed" is a funding stage and "beta" usually means people use the product. You said the site is a waitlist and nobody is using it yet, so I'd record **validation**: talking to customers and testing commitment, no product in regular use. Say if you see it differently.

**Creating `.foundora/company.md`: round 2 of 5, Problem and customer**
1. What problem do you solve, and who has it?
2. Who pays, who uses it day to day, and how do they buy?
3. What do they do today instead, and what do you understand about this that those options miss?

> Founder: "Small firms run close for 20–80 clients in spreadsheets and email. Partners can't see who's blocked, deadlines slip, reviewers redo work. Ops leads and managing partners feel it. Partner buys on a card or annual invoice, no procurement; ops lead and bookkeepers use it. They already pay for QBO or Xero and Karbon or TaxDome. Honestly nobody does this properly, so no real competitors."

**Agent, round 3**

On competitors: I can't record "none", because every skill would then assume an empty field. When close goes wrong today, what do these firms do instead? Spreadsheets, a template inside Karbon or TaxDome, nothing?

**Creating `.foundora/company.md`: round 3 of 5, Team and traction**
1. Do you have a cofounder? Name and role if so.
2. What is your role, what in your background fits this problem, and why is now the time?
3. What numbers do you have so far, each with a count? "None yet" is fine.

> Founder: "Google Sheets checklists, Karbon and TaxDome workflow templates, or nothing. Cofounder is Priya, CTO, ex-fintech engineer. I'm CEO, ran ops at a 9-person bookkeeping firm for 4 years. Traction: 11 discovery interviews, 62 on the waitlist, lots of interest from firms, and 2 firms doing a free 30-day pilot starting next week. No revenue."

**Agent, round 4**

Two checks on traction. How many of the 62 are firms with 3–15 staff? And who were the 11 interviews with? I'll record the pilots as "free 30-day concierge pilot", not as customers.

**Creating `.foundora/company.md`: round 4 of 5, Constraints and direction**
1. What constrains you: runway in months, time, budget, regulation?
2. What is the one thing that kills the company if you're wrong about it?
3. What outcome are you working toward in the next 90 days, with a number?

> Founder: "9 of the 62 are in the band. Interviews were 8 partners, 3 ops leads. Both full-time, about 7 months runway, no paid acquisition budget. Risks: firms won't pay on top of Karbon/TaxDome, and maybe we can't reach firms cheaply. Goal: 3 firms paying at least $150/month after the pilot."

**Agent, round 5**

You named two risks. The 90-day goal tests the first one, so I'll record "will they pay separately" as the biggest risk and leave reach out of the file unless you say otherwise.

**Creating `.foundora/company.md`: round 5 of 5, Working preferences**
1. How should agents talk to you: direct, warm, analytical, or playful?
2. Anything else they should know?

> Founder: "Direct. Tables over paragraphs. US spelling. And yes, the pay-separately one is the risk."

**Agent, preview**

**Proposed `.foundora/company.md`** (new file)

~~~markdown
---
foundora: 1
company: "Ledgerline"
stage: "validation"
updated: "2026-10-20"
---

# Ledgerline — company context

This file is the founder's source of truth. Foundora skills read it at the start of every session.
Agents: propose edits as a diff and wait for confirmation. Log decisions in `.foundora/journal.md`.

## Snapshot
- **One-liner:** Month-end close checklist and reconciliation tracker for bookkeeping firms with 3–15 staff
- **Stage:** Validation
- **Business model:** B2B SaaS
- **Website:** ledgerline.app (waitlist page only)

## Problem
Small bookkeeping firms run month-end close for 20–80 clients out of spreadsheets and email. Partners can't see which clients are blocked, deadlines slip, and reviewers redo work because nobody knows what was already reconciled.

**Who has it:** Operations leads and managing partners at bookkeeping firms with 3–15 staff

## Target customer
Managing partner buys (card or annual invoice, no procurement). Ops lead and bookkeepers use it daily. Firms already pay for QuickBooks Online or Xero and a practice tool like Karbon or TaxDome.

## Team
- **Cofounder:** Yes, Priya (CTO, ex-fintech engineer)
- **Founder role:** CEO, ran ops at a 9-person bookkeeping firm for 4 years

## Traction & metrics
- 11 discovery interviews (8 partners, 3 ops leads)
- 62 waitlist signups, 9 from firms in the target size band
- 2 firms agreed to a free 30-day concierge pilot starting next week
- No revenue

## Constraints
Both founders full-time. About 7 months of runway. No paid acquisition budget yet.

## Biggest risk / open question
Firms already pay for a practice management tool. Will they pay separately for close tracking, or is this a feature those tools will add?

## 90-day goal
3 firms paying at least $150/month after the pilot.

## Alternatives & competitors
Google Sheets close checklists, Karbon and TaxDome workflow templates, doing nothing.

## Working preferences
- **Tone:** Direct
- **Notes:** Tables over paragraphs. US spelling.
~~~

**Still missing:** none. "Lots of interest" was left out because it has no count; "reach firms cheaply" was left out at your call.
**Clarity check:** 50-char version gap: the one-liner is 90 characters; short option "Month-end close tracker for small bookkeeping firms" · progress yes · why this yes (4 years running ops at a bookkeeping firm), why now gap (you skipped it) · what you see that others miss gap: you said "nobody does this properly", which says what's wrong with them, not what you know · how you make money yes (B2B SaaS, about $150/month per firm)
Write this? Reply yes, or tell me what to change. Answer any gap in a line, or skip it.

> Founder: "Yes. Keep the long one-liner. Skip the other two for now."

**Agent, after writing**

Written to `.foundora/company.md`. I also created `.foundora/journal.md` with this entry:

```markdown
### 2026-10-20 — decision: Company context created
- Changed: new file; stage recorded as validation (founder said "pre-seed, kind of in beta"; no product in regular use)
- Why: biggest risk set to paying separately from Karbon/TaxDome; reach risk left out at founder's call
- Still missing: clarity gaps skipped: why now; what we understand that Sheets and Karbon/TaxDome templates miss
- Source: company-context
```

Those two gaps are worth an answer before you write a landing page or pitch anyone. `positioning` can help with the second one.

There is no `CLAUDE.md` or `AGENTS.md` here, so other agents won't know to read this file. Want me to create one with the 4-line Foundora section (read both files at session start, log in the journal, never edit company.md without asking, start with `cofounder`)? Which file name does your tool use?

Next: run `cofounder` with "what should I work on this week" now that the pilots start next week.
