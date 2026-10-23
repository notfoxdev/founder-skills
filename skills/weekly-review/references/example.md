# Worked example: weekly-review (setup mode)

> Illustrative and fictional (Ledgerline fixture). Calibrates depth and format only; never reuse its content.

**Request:** "Set up my weekly review."

**Context used:** `company.md` (Ledgerline, validation stage, B2B SaaS, 11 interviews, 62 waitlist signups with 9 in band, 2 free 30-day pilots starting the week of 2026-10-26, no revenue, about 7 months runway, biggest risk: will firms pay separately from Karbon or TaxDome, 90-day goal: 3 firms paying at least $150/month). No scoreboard in the journal, so this is setup mode. Answer dated Tuesday 2026-10-20.

---

# Weekly review setup: Ledgerline

**North Star:** Firms committed to pay: firms that have paid, or agreed in writing, to continue at $150/month or more. Baseline: 0.
**Why this one:** it is your 90-day goal and your biggest risk in one number. It will read 0 until the pilots reach day 30 (about 2026-11-25). That is expected; the inputs below move weekly and tell you early whether it will.

| Candidate | Customer value | Weekly | Movable in weeks | Leads to revenue | Closest to risk | Pick |
|---|---|---|---|---|---|---|
| Firms committed to pay ≥ $150/month | Yes | Yes | Yes, within 6 weeks | Directly | Yes: tests paying separately | Yes |
| Pilot firms using Ledgerline every close day | Yes | Yes | Yes | Indirectly | Partly: use without payment can coexist with "Karbon is enough" | No, becomes an input |
| Discovery interviews per week | No | Yes | Yes | No | No: you have 11 already; more talk does not test payment | No |
| Waitlist signups | No | Yes | Yes | Weakly | No: 53 of 62 are outside your band | No, goes on the kill list |

## Inputs
| Input | Definition | Source / owner | Baseline | Tests the risk? |
|---|---|---|---|---|
| Pilot close coverage | % of each pilot firm's month-end clients tracked in Ledgerline this week | Concierge log / [NEED: owner] | n/a until 2026-10-26 | Indirectly: no use, no conversion |
| Paid-commitment asks | Firms asked this week for a written $150/month commitment, with the answer (yes / no / objection type) | CRM notes / [NEED: owner] | 0 | Yes, directly |
| "Our practice tool covers this" objections | Conversations this week where a firm says Karbon or TaxDome already does the job | Call notes / [NEED: owner] | [NEED: how many of the 11 interviews said this] | Yes, the incumbent-feature risk |
| Third-pilot conversations | Calls held with firms of 3–15 staff about a pilot (9 in-band waitlist firms first) | Calendar / [NEED: owner] | 0 | No: serves the 90-day goal |

Quality check: all four can change this week, have a plausible link to the North Star, are counted the same way weekly, and would change a decision (for example, 2+ "covers this" objections in a week means rewriting the pilot offer before day 30).

Pushback: you have 2 pilots and a goal of 3 paying firms. Even a perfect pilot result misses the goal. That is why the fourth input exists and why priority 2 below is not optional.

## First week's priorities (max 3)
1. Both pilot firms agree in writing, by Friday 2026-10-23, what happens on day 31: continue at $150/month or stop. Serves: biggest risk.
2. 3 of the 9 in-band waitlist firms booked for a third-pilot call by Friday 2026-10-23. Serves: 90-day goal.
3. Both pilot firms' client lists loaded and close dates set before Monday 2026-10-26. Serves: biggest risk (no use, no test).

## Kill list
- Tracking total waitlist signups: why, 53 of 62 are outside the 3–15 staff band, so the number rewards growth from the wrong buyers. Frees: one vanity number off the scoreboard.
- Follow-ups to the 53 out-of-band signups until 3 firms pay: why, none of them can become one of the 3 paying firms in your band. Frees: [NEED: hours a week this takes now].
- [NEED: one recurring meeting or task from last week that served neither the risk nor the goal]. Tell me what filled your calendar and I will pick it.

**Review slot:** Fridays, 20 minutes, after the week's pilot sessions [ASSUMPTION: move it if Friday clashes with pilot close days]. First full weekly review: Friday 2026-10-30.

## What the first weekly review will check (2026-10-30)
| Signal | Threshold | If missed |
|---|---|---|
| Pilot close coverage | Both firms tracking at least half their clients in week 1 | Priority 1 next week: fix onboarding before asking for payment |
| "Practice tool covers this" objections | 2 or more in one week | Rewrite the day-31 offer around what the templates miss, before 2026-11-25 |
| Third-pilot conversations | 3 held | Add a second source beyond the 9 waitlist firms: [NEED: which network or community] |

These thresholds are proposals [ASSUMPTION], not benchmarks. Confirm or change them; each one is set to trigger a different action.

Before next Friday, send me: an owner for each input, and the count of "Karbon already does this" answers in your 11 interviews. Both are [NEED] above.

Logged to `.foundora/journal.md`:

```markdown
### 2026-10-20 — review: Weekly review setup
- North Star: firms committed to pay ≥ $150/month, baseline 0 (90-day goal: 3)
- Inputs: pilot close coverage; paid-commitment asks; "practice tool covers this" objections; third-pilot conversations
- Priorities: 1. day-31 terms agreed with both pilots 2. 3 third-pilot calls booked 3. pilot client lists loaded
- Killed: waitlist total as a metric; follow-ups to 53 out-of-band signups; next review: 2026-10-30
- Source: weekly-review
```
