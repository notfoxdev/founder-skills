# Worked example (illustrative, fictional)

> Uses the fictional Ledgerline fixture (`evals/fixture-company.md`). It calibrates depth, tone and format only. Never copy its content into a real answer.

## Request

"What should we actually track before the pilots start? Priya wants to set up an analytics tool this weekend."

## Context used

- `company.md`: Ledgerline, validation stage, B2B SaaS, 2 free 30-day concierge pilots starting next week, no revenue, managing partner buys, ops lead and bookkeepers do the work, biggest risk is paying separately from Karbon or TaxDome, 90-day goal is 3 firms paying at least $150/month. Working preferences: direct, tables, US spelling.
- `journal.md`: `weekly-review` 2026-10-20 setup (North Star: firms committed to pay $150+/month, baseline 0; inputs include pilot close coverage). `mvp-scoper` 2026-10-23 experiment (paid concierge pilot; value threshold compares clients past their close deadline with the month before, baseline [NEED] at kickoff) and the trigger "ops leads update the board unprompted 3+ days a week in week 2". No `onboarding` entry, so no logged aha moment.
- Repo (illustrative for this example): Priya's pilot board app. TypeScript, Postgres tables `firms`, `clients`, `close_steps`; you and the ops leads update steps there. No analytics code yet.
- Date: Friday 2026-10-23. No question asked first: users, accounts and the upcoming decisions are all in the files.

## Model answer

# Measurement plan — Ledgerline — 2026-10-23
**Primary metric:** firms committed to pay $150+/month, weekly, from the pilot sheet. Same as your weekly-review North Star; no tool can count it, because it lives in emails and the payment link.
**Activation:** a pilot firm has all its month-end clients loaded and its ops lead marks at least one close step done themselves, within the first close cycle. Evidence: [ASSUMPTION]. No firm has used it yet; confirm with both pilots.
**Retention signal:** the firm's ops lead updates steps on 3 or more close days a week. That's the trigger you already logged. The real retention read is the second close cycle, which lands after day 30, so treat in-pilot use as an early signal only.
**Tool decision:** the pilot sheet plus 4 server-side events written to your own Postgres. No analytics tool yet. Revisit at 20 active firms, the first self-serve signup, or a weekly question that takes 30+ minutes of SQL.

On Priya's tool: the strong case is that it builds good habits early and costs little to set up. The objection is that 2 firms of 3–15 staff each can't produce a number you couldn't get by asking them, and a tool adds a second place holding data about your customers' clients. The events table keeps the same names and properties, so moving to a tool later means changing one function, not every call site.

## Questions this answers
| # | Question | Decision it feeds | Answered by |
|---|---|---|---|
| 1 | Are ops leads updating the board themselves, or is it all you? | Reminders come back (mvp-scoper trigger) or concierge continues | `close_step_completed` by `actor_role` |
| 2 | Which clients get blocked, why, and for how long? | Which manual step to automate first; what to show partners | `client_blocked`, `client_unblocked` |
| 3 | Did fewer clients miss their close deadline than last month? | The mvp-scoper value threshold | `client_close_completed.days_past_due` vs kickoff baseline [NEED] |
| 4 | How many founder-hours does each firm take? | The 10-hours-a-week break point | Pilot sheet |
| 5 | Is the partner reading the Friday summary? | Whether the buyer sees the value before day 31 | Pilot sheet (replies and questions) |
| 6 | What does each firm say on day 31, and which objections come up? | The North Star and the biggest risk | Pilot sheet |

## Tracking plan (4 events)
| Event | Q# | Trigger (exact moment) | Properties | Server / client | Called from |
|---|---|---|---|---|---|
| `close_step_completed` | 1 | A step's status is saved as done | `client_id`, `step_type`, `actor_role`, `days_to_due` | Server | step status update handler |
| `client_blocked` | 2 | A step is saved as blocked | `client_id`, `step_type`, `reason_category` | Server | same handler |
| `client_unblocked` | 2 | A blocked step is saved as anything else | `client_id`, `step_type`, `hours_blocked` | Server | same handler |
| `client_close_completed` | 3 | The last step for a client's month is done | `client_id`, `days_past_due` (0 if on time) | Server | same handler, after the step write |

Identity: `user_id` per person with access, `account_id` = the firm. `actor_role` is founder, ops_lead, bookkeeper or partner. When you do the concierge work for a firm it's real activity with `actor_role: founder`, not internal. `is_internal` is true only for the demo firm you and Priya test on.
`reason_category`: waiting_on_client_docs, missing_bank_feed, reviewer_question, other [ASSUMPTION: built from your own close checklist; change it after week 1]. The typed reason stays in `close_steps`.
Not tracking now: page views, logins, clicks, session replay (nothing to watch that you won't see on the call), signup funnel (no self-serve signup), waitlist sources (weekly-review already killed that number). A partner screen doesn't exist yet; when one is built, its open event becomes number 5.

## Privacy
- Events carry IDs and categories only: no client names, no amounts, no typed reasons. Your customers' clients are their confidential business.
- No browser tracking, so no cookie banner question for now. The pilot agreement should say what you store and that you can delete it [NEED: does the current pilot agreement cover data handling?]. General information; check what applies to you.

## Reading it with small numbers
Both firms start the same week, so there's one cohort of 2. Every result reads "both", "1 of 2" or "neither", and mvp-scoper already marked the pilot directional. No A/B test: you can't split 2 firms. Read each firm's week line by line in the sheet every Friday instead.

## Verification
- [ ] Before Monday's kickoff, on the demo firm: complete one step, block another and unblock it, then finish that client's remaining steps. Expect one `close_step_completed` per step done and exactly one each of the other three, all with the demo firm's `account_id` and `is_internal` true.
- [ ] Save the same step twice and reload the page. Still one row per real change.
- [ ] Search the rows for client names and "@". None.
- [ ] Friday 2026-10-30: the query's counts per firm match what you saw on your calls. Any gap gets fixed before the weekly review uses them.

## Hand-off for the coding agent
Add one `track()` helper in the server data layer next to the `close_steps` access code, with the 4 names as a closed type. It fills `user_id`, `account_id`, `is_internal` and the timestamp, inserts into a new `events` table, and never throws. Call it in the step status update handler after the write commits, one call per event above. One test per event asserting a single row on the happy path. Then one saved query that groups the week's events by firm and `actor_role`; you paste its output into the sheet before each Friday review.

Pilot sheet columns, one row per firm per week: clients loaded vs total [NEED: each firm's client count at kickoff], steps done by the ops lead vs by you, clients blocked at Friday, closes past due, your hours, partner replies or questions, day-31 status and objections.

Logged to `.foundora/journal.md`:

```markdown
### 2026-10-23 — decision: Measurement plan
- Primary metric: firms committed to pay $150+/month (weekly-review North Star), baseline 0
- Activation: all clients loaded + ops lead marks a step done themselves in the first close cycle ([ASSUMPTION]); retention: ops lead updates on 3+ close days a week
- Tool: pilot sheet + 4 server-side events in our own Postgres (close_step_completed, client_blocked, client_unblocked, client_close_completed); no analytics tool
- Revisit: 20 active firms, first self-serve signup, or a weekly question taking 30+ minutes of SQL
- Source: product-analytics
```
