# Tracking plan: template, naming, starter sets, verification

Load this when writing or auditing a tracking plan. The starter sets are menus to pick from, not lists to install. Every event you keep still needs a question the founder will ask this month.

## Template

| Event | Q# | Trigger (exact moment) | Properties | Server / client | Called from | Owner |
|---|---|---|---|---|---|---|
| `client_blocked` | 2 | A close step's status is saved as blocked | `client_id`, `step_type`, `reason_category` | Server | step status update handler | Priya |

Write the trigger as the moment the thing is true, not the click that asks for it: "after the invoice row is saved with status sent", not "user clicks Send".

## Naming rules

- `object_action`, past tense, snake_case: `report_exported`, `teammate_invited`, `payment_failed`.
- The object is a noun from the product's own vocabulary (the word customers use), not a UI element: `client_blocked`, not `red_button_clicked`.
- One name per meaning, forever. If the meaning changes, it's a new event.
- Variation goes in properties: `step_completed` with `step_type`, not `bank_rec_step_completed` and `payroll_step_completed`.
- Property names are snake_case nouns; values are lowercase fixed categories where possible (`actor_role: "ops_lead"`).
- Booleans read as questions: `is_internal`, `is_first`.
- Durations and counts carry the unit: `hours_blocked`, `days_past_due`.

## Property rules

- Every event, set by the helper: `user_id`, `account_id`, `is_internal`, timestamp.
- Add the role (`actor_role`) when the buyer and the people doing the work differ.
- IDs and categories only. Never names, emails, phone numbers, addresses, free text, file contents, or the customer's own client or patient data.
- If a property would be free text (a reason, a note), replace it with a fixed `*_category` list and keep the text in the product database where access is controlled.
- Keep it to what a question needs. Three good properties beat ten.

## B2B starter set (pick 6–10)

| Event | Question it usually answers |
|---|---|
| `account_created` | How many new accounts started this week, by source? |
| `user_invited` / `user_joined` | Do accounts bring in teammates, and how fast? |
| `<data>_imported` | Did they get their own data in? Where do imports fail? |
| `<core_object>_created` | Is the account doing the core job at all? |
| `<core_action>_completed` | Activation and retention: the value moment, repeated |
| `<output>_shared` / `<output>_exported` | Does the result reach the buyer or the customer's customer? |
| `<blocker>_hit` (e.g. `client_blocked`) | Where does the job get stuck? |
| `trial_started` / `subscription_started` / `subscription_cancelled` | Revenue: who pays, who leaves, with `plan` and `reason_category` |
| `payment_failed` | Is revenue leaking for reasons nobody chose? |

## B2C starter set (pick 6–10)

| Event | Question it usually answers |
|---|---|
| `account_created` | New users per week, by source |
| `onboarding_step_completed` (with `step`) | Where do new users stop before the aha moment? |
| `<core_action>_completed` | Activation, and weekly active users who got value |
| `<content>_created` / `<content>_saved` | Are they putting something of their own in? |
| `<item>_shared` / `invite_sent` | Does it spread person to person? |
| `notification_opened` | Do reminders bring people back, or just annoy them? |
| `subscription_started` / `subscription_cancelled` | Revenue and churn, with `plan` and `reason_category` |

Skip at this stage unless a question needs it: generic `button_clicked`, `page_viewed` for every screen, scroll depth, `feature_used` with dozens of values, search queries (often personal), settings changes.

## Weekly cohort table (counts)

| Signup week | Accounts | Activated in week 1 | Active week 2 | Active week 3 | Active week 4 |
|---|---|---|---|---|---|
| 2026-W44 (illustrative row) | 3 | 2 | 2 | 1 | not yet |

Read across a row for one cohort; down a column to compare cohorts. Write "2 of 3", never "67%". Until there are several cohorts of 10+, the table is a list of names in disguise: read the accounts.

## Helper sketch (stack-neutral, adapt to the repo)

```ts
// One file, server-side. Allowed names are a closed list.
const EVENTS = ["client_blocked", "client_unblocked", "close_step_completed"] as const;
type EventName = (typeof EVENTS)[number];

export async function track(event: EventName, ctx: { userId: string; accountId: string; isInternal: boolean }, props: Record<string, string | number | boolean> = {}) {
  try {
    await writeEvent({ event, user_id: ctx.userId, account_id: ctx.accountId, is_internal: ctx.isInternal, props, at: new Date() });
  } catch (err) {
    logWarning("track failed", { event }); // never throw: tracking must not break the action
  }
}
```

Call it after the write succeeds, inside the same handler. `writeEvent` inserts into your own `events` table now and can forward to an analytics tool later without changing any call site.

A weekly query, same idea in any SQL database:

```sql
select account_id, props->>'actor_role' as role, count(*) as steps
from events
where event = 'close_step_completed' and not is_internal
  and at >= date_trunc('week', now())
group by 1, 2 order by 1, 2;
```

## Verification checklist

- [ ] Each event fired by hand in a test account, and exactly one row or hit appears.
- [ ] Refresh, back button and double-click don't create duplicates.
- [ ] `user_id` and `account_id` are present and match the right records.
- [ ] Properties have the expected values and types; no empty strings standing in for missing.
- [ ] No names, emails or free text anywhere in the payload (search a day's rows for "@").
- [ ] Test and internal accounts carry `is_internal = true` and are excluded from every query.
- [ ] A failed tracking call doesn't break the user's action (turn the events write off and try).
- [ ] Each event has a test that asserts it fires once on the happy path.
- [ ] After the first real week: counts match what the founder knows happened, account by account.
- [ ] The privacy policy (and, for B2B, the customer agreement) says what is collected.
