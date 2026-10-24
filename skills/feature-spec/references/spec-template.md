# Spec template, review checklist, and small versions

Load this when writing a medium spec, reviewing someone else's, or writing a one-paragraph or bug spec. The SKILL.md output format is the contract; this file explains what goes in each part and shows two tiny filled versions.

## The medium spec, part by part

| Part | What good looks like | What to avoid |
|---|---|---|
| Verdict | One of three: build it, build the smaller version, don't build yet | "Here's a spec" with no opinion on whether to build |
| Job | One job story with a real situation and a real outcome, in the customer's words | "As a user I want a dashboard" (no situation, no outcome) |
| Evidence | Counts and names: "both pilot partners asked in week 1", plus the journal entry | "Customers want this", "high demand" |
| Appetite | A number of builder-days and the first thing to cut if it runs long | An estimate of the first idea dressed up as a budget |
| 90/10 version | 2–4 sentences, plus the options you didn't pick and why | A feature list |
| No-gos | Each with why and what brings it back; everything the founder asked for that's out, by name | "Out of scope: future enhancements" |
| Rabbit holes | One-line decisions: "dates only, no time zones" | Leaving them for the builder to discover |
| Acceptance checks | 3–8, numbered, each visible to a person or assertable by a test | "Fast", "intuitive", "works well", "user-friendly" |
| States | Empty, loading, error, no access, partial data, the big case, with real copy | "Handle errors gracefully" |
| Data and tracking | Fields and migrations; sensitive data rules; one "did it work" question and its event | A list of 15 events |
| Risks and open questions | `[NEED: ...]` with who, by when, and what it changes | Questions nobody owns |
| Build plan | 3–7 steps, each ending in something runnable, each naming files and checks | "Implement backend", "Build frontend", "Test" |
| Test it yourself | 4–8 clicks with what the founder should see | "Verify it works" |

### Writing acceptance checks

- Start with who and where: "A partner opening the firm link sees..."
- Say the observable result, including order and limits: "oldest due date first", "only that firm's".
- One behaviour per check. If a check has "and" twice, split it.
- Include at least one negative check (what must never happen) when data belongs to different customers.
- A check that needs the founder's judgement ("looks clean") is a design note, not a check. Move it or make it concrete ("readable on a phone without zooming").

### Writing agent-sized build steps

- One step, one diff a person can review in about 10 minutes.
- "Done when" is a command or a visible result: `npm test -- blocked-clients` passes; the page at `/f/<token>` renders seed data.
- Seed data first. The UI step should never wait on real customer data to be verifiable.
- Each step says which existing pattern to copy ("same shape as the `clients` query in `db/clients.ts`") so the agent doesn't invent a new one.
- If a step would take more than one sitting, split it at the first point where something runs.

## Review checklist

Run each line. Each "no" is a candidate problem; report the worst three.

1. Can the job be stated in one job story with a real situation and outcome?
2. Is there evidence in counts or names, and does it trace to the biggest risk or the 90-day goal?
3. Is there an appetite, and does the scope fit inside it?
4. Is there a smaller version that does most of the job, and was it considered?
5. Are no-gos written down, including what the founder or a customer asked for that's out?
6. Is every requirement an observable acceptance check? Count the "should"s with no check.
7. Are empty, error and no-access states covered with real copy?
8. Does any customer's data risk reaching another customer, logs, or analytics?
9. Does the build plan end every step in something runnable, and does it follow the repo's patterns?
10. Could the founder review it in two minutes? If it's longer than two pages for under two weeks of work, it isn't.

Common cuts in founder-written PRDs: stakeholder and contacts sections when there are two people, phased percentage rollouts with a handful of users, persona write-ups, market sizing, competitive value curves, success metrics with invented baselines. Cut them with one line each.

## Filled example: one-paragraph spec

> Illustrative and fictional (Ledgerline fixture). Shows length and shape only.

**Days overdue on the board.** On the firm board, add a "Days overdue" column after "Due date" showing whole days past the due date for clients that aren't closed, blank for clients on time or closed. Calendar dates only; no time zones.
Checks: 1. A client due yesterday and not closed shows 1. 2. A closed client shows blank, even if it closed late. 3. The column sorts numerically.
Test it: open the demo firm, set one client's due date to yesterday, and check the column reads 1.

## Filled example: bug spec

> Illustrative and fictional (Ledgerline fixture). Shows length and shape only.

# Bug: Blocked reason wiped when step owner changes — 2026-11-04
**Severity:** this week — the partner sees "No reason yet" for clients that had a reason, which breaks a pilot workflow; no data leaves the firm.
**Repro:** 1. Open the demo firm. 2. Block a client's bank rec step with reason "Waiting on March statements". 3. Change the step owner. Expected: reason kept. Actual: reason empty.
**Suspected area:** the step update handler writes the whole row from the form, and the owner form doesn't include the reason field [ASSUMPTION until the repo is read].
**Fixed when:** the repro keeps the reason; regression test `keeps blocked reason on owner change` fails before the fix, passes after.
**Not in this fix:** no refactor of the update handler beyond the reason field; no new audit log.
**Customer note:** "Quick heads-up: for a day, changing who owned a step cleared its blocked reason. It's fixed. If a client on your list says 'No reason yet' and you know why it's stuck, tell me and I'll put it back."
