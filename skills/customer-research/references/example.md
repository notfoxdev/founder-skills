# Worked example: customer-research

> Illustrative and fictional (Ledgerline fixture). Calibrates depth and format only; never reuse its content.

## Request

"Write an interview script for the pilot firms' ops leads."

## Context used

- `.foundora/company.md`: the Ledgerline fixture (`evals/fixture-company.md`). Biggest risk: will firms pay separately from Karbon or TaxDome. Buyer is the managing partner; ops leads use the product daily. Working preferences: direct, tables over paragraphs, US spelling.
- `.foundora/journal.md`: not present.
- Mode (a). The founder did not state a research question, so it is derived from the biggest risk rather than asked.
- Date: 2026-10-23. Pilots start the week of 2026-10-26 [NEED: kickoff dates].

## Model answer

# Interview kit — Pilot-firm ops leads — 2026-10-23

**Research question:** How do ops leads at the pilot firms track month-end close today, what does it cost them in hours and rework, and what does the firm already pay for that touches close?
**Decision it informs:** Whether Ledgerline can be sold as a separate $150/month subscription or will be judged against Karbon and TaxDome. If both ops leads run close inside their practice tool's templates and describe only minor gaps, the "pay separately" case weakens: log it and re-run `idea-validator` before the day-30 conversion ask. If both run a spreadsheet alongside or instead of the template, with hours they can name, the case strengthens.
**Sample:** 2 pilot ops leads [NEED: confirm each firm has one] plus 3 in-band waitlist ops leads, for 5. Two alone can produce Signals at most. Stop rule: 3 consecutive with nothing new.

Two calls on timing and scope:
- Interview the pilot ops leads before kickoff. Once they have used the board, their account of "how we do it today" changes. If a kickoff comes first, anchor every question to "before the pilot".
- Ops leads use the tool; partners buy it. Their answers on spend are "reported by user", not budget evidence. The partner budget question goes to the day-30 conversation, not this call.

## Script (30 min) — must-ask questions marked [MUST]

| Time | Section | Questions and probes |
|---|---|---|
| 0–3 | Open | "Thanks for making time before the pilot starts. Today isn't about the pilot or our tool. I want to understand how close works at <firm> right now, before anything changes. There are no right answers. OK if I take notes?" Record only with consent. |
| 3–8 | Context | 1. "Walk me through a normal month. Where does month-end close show up for you?" 2. "How many clients did you close last month, and who did the work?" |
| 8–18 | Last close | 3. [MUST] "Take me through last month's close from day one. What did you open first?" 4. "Where do you track which clients are done, blocked, or waiting on documents? Can you show me?" 5. [MUST] "Which client was hardest to close last month? What held it up, and when did the partner find out?" 6. "Was any work redone at review last month? What happened, and how long did the redo take?" |
| 18–23 | Tools and cost | 7. [MUST] "Which tools does the firm pay for that touch close: Karbon, TaxDome, QBO, Xero, anything else? Which do you open during close?" 8. [MUST] "Has anyone at the firm tried running close in <Karbon/TaxDome>'s templates? When? What happened?" 9. "Roughly how many hours did you spend last month chasing status rather than reconciling? How do you know?" |
| 23–26 | Priority and buying | 10. "Where does close rank among what you're dealing with this quarter?" 11. "Think of the last tool the firm added. Who suggested it, who approved it, and how was it paid for: card, invoice, or bundled into something you already had?" 12. "When it came in, did anything get cancelled or replaced?" |
| 26–30 | Close | 13. "Who else at the firm should I talk to about how close works?" 14. [MUST] "Could you send me last month's close tracker, as it is? It gives us the baseline for the pilot." Then, and only then, two minutes on how the pilot will run. No demo. |

Probes throughout: "Can you show me?", "What happened next?", "You said 'usually'. When was the last time?", "What did that cost you?", and three seconds of silence after each answer.

Do not ask, and ask instead:
- "Would you use a tool that tracks close?" → Q4.
- "Would the firm pay for this on top of Karbon?" → Q7, Q11, Q12. Price levels go to `pricing-strategy`.
- "Is close tracking a problem for you?" → Q5.
- "What should the pilot include?" → "What would let you stop updating that sheet?"

## Screener (or why it is skipped)

Skipped for the 2 pilot ops leads: the pilot already selected them. Use this for the 3 waitlist ops leads.

| # | Question | Qualify if | Disqualify if |
|---|---|---|---|
| 1 | Which best describes your role? (managing partner / ops lead or practice manager / bookkeeper / accountant / other) | Ops lead or practice manager | Other |
| 2 | How many staff at your firm? (1–2 / 3–15 / 16–50 / 50+) | 3–15 | Any other band |
| 3 | When did you last run or coordinate month-end close? (this month / last month / 2–6 months ago / longer) | This month or last month | Longer |
| 4 | What did you use to track close status last time? (open text) | Names a sheet, tool, or process | Blank or vague |
| 5 | Do you work for or with Karbon, TaxDome, or another practice-software vendor? | No | Yes |

## Outreach (cold / warm / community)

**Warm, to pilot ops leads** (62 words):
> Hi <name>, <partner> mentioned you run close at <firm>. Before the pilot starts on <date>, I'd like 30 minutes to understand how close works for you today: what you track and where it gets stuck. This isn't a training session and needs no prep. Could we do <day> or <day> this week? If it's easy, have last month's close tracker open.

**Cold, to in-band waitlist ops leads** (62 words):
> Hi <name>, you joined the Ledgerline waitlist from <firm>. I'm talking to ops leads at firms with 3–15 staff about how month-end close runs today, especially how you see which clients are blocked. I'm not selling anything on this call. Would 20 minutes next week work? I'll share what I learn across the conversations. If it's not a fit, no reply needed.

[NEED: which of the 9 in-band signups are ops leads. If a partner signed up, ask them for an intro and use the warm variant.] No community post: you have enough named people for 5.

## Notes template

Use the template in the skill's interview reference, plus these fields for this round:

```markdown
Relationship: pilot / waitlist
Close tracking today: <tool / sheet / none>; shown on screen: yes / no
Tools paid for that touch close: <tool / who pays / amount if known> (reported by user)
Tried close in Karbon/TaxDome: yes / no; when; what happened
Hours chasing status last month: <n>; how they know
Last tool purchase: suggested by / approved by / paid how / replaced what
Commitment: last month's tracker shared? yes / no
```

Logged to `.foundora/journal.md` (created):

```markdown
### 2026-10-23 — experiment: Interview round pilot-firm ops leads
- Research question: how close is tracked today, its cost, and what the firm pays for that touches close
- Sample: 5 planned (2 pilot + 3 waitlist), stop rule: 3 consecutive with nothing new
- Answer pattern that changes the decision: 3+ of 5 run close in Karbon/TaxDome templates with minor gaps
- Synthesis due: 2026-11-06
- Source: customer-research
```

## Why this scores 12/12

| Rubric line | Where it shows |
|---|---|
| Context use | Research question derived from the biggest risk; buyer/user split from company.md; nothing re-asked |
| Honesty | Kickoff dates and ops-lead identities marked `[NEED]`; user-reported spend not treated as budget |
| Decision quality | Answer pattern that changes the decision stated up front; sample floor and stop rule applied |
| Pushback | Interview before kickoff; 2 interviews named as Signals at most; no price hypotheticals |
| Format | Mode (a) template; tables; US spelling; outreach under 90 words |
| Actionability | Five [MUST] questions, a data commitment ask, synthesis due 2026-11-06 |
