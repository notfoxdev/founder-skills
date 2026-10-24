# Worked example (illustrative, fictional)

> Uses the fictional Ledgerline fixture (`evals/fixture-company.md`). It calibrates depth, tone and format only. Never copy its content into a real answer.

## Request

"Both pilot partners emailed me last week asking which clients are stuck. Spec a partner view of blocked clients so Priya's agent can build it this week. And add QBO and Xero sync so the statuses update themselves."

## Context used

- `company.md`: Ledgerline, validation stage, 2 free 30-day concierge pilots, firms run close for 20–80 clients, the managing partner buys, biggest risk is whether firms pay separately from Karbon or TaxDome, 90-day goal is 3 firms paying at least $150/month. Working preferences: direct, tables over paragraphs, US spelling.
- `journal.md`: `mvp-scoper` 2026-10-23 experiment (paid concierge pilot, decide by 2026-11-27) and decision (QBO and Xero deferred; revisit when 2+ paying firms cite manual updates as a reason to cancel, or manual work passes 10 founder-hours a week). `product-analytics` 2026-10-23 decision (4 server-side events; the partner-side signal stays in the pilot sheet until there's a partner screen).
- Repo (illustrative for this example): the small pilot board app Priya built. TypeScript web app, Postgres tables `firms`, `clients`, `close_steps` (status, blocked_reason, owner, due_date), an `events` table with a server-side `track()` helper, magic-link login for you and the firms' ops leads (partners have none), an existing test runner.
- Date: Monday 2026-11-02, week 2 of the pilots. No question asked first: the builder and the week are in the request, so the appetite can be set now.

## Model answer

# Spec: Partner view of blocked clients — Ledgerline — 2026-11-02
**Verdict:** Build the partner view this week. QBO and Xero sync stays out.
**Job:** When a client's close gets stuck, the managing partner wants to see which clients are blocked and why without emailing anyone, so they can chase the right person before the deadline slips.
**Evidence:** 2 of 2 pilot partners emailed in week 1 asking which clients are stuck. The partner is the person who says yes or no on day 31, so this serves the 90-day goal and gives the biggest risk a fairer test: they judge the product they'd pay for, not your Friday email.
**Appetite:** 3 builder-days (Priya plus her agent), Monday to Wednesday. If it runs long, cut the phone layout polish first, never the access checks.

## The 90/10 version
One read-only page per firm, opened from a hard-to-guess link you send to the partner. It lists only blocked clients from the `close_steps` table you already update, oldest due date first, with the reason and who owns the next step. Options considered: partner logins with roles (days of auth work for 2 people) and a richer Friday email (no build, but still a weekly snapshot, and they asked mid-week). The link gets the job done for a fraction of either.

## No-gos
| Not doing | Why | Brings it back |
|---|---|---|
| QBO and Xero sync | Logged 2026-10-23: deferred because it tests whether we can build it, and the open question is whether firms pay. No firm pays yet, so the "2+ paying firms" trigger can't have fired. The hours trigger is unknown: [NEED: last week's founder-hours from the pilot sheet]. At 10+, the first thing to automate is the most time-consuming manual step, which may not be the sync | Either trigger in the 2026-10-23 entry fires |
| Partner logins, roles, permissions | 2 partners; a revocable link per firm covers it | A paying firm asks for staff access |
| Editing from the partner view | The partner reads; the ops lead and you update | Both partners ask to unblock from the page |
| Alerts or notifications | The page has to prove useful first | A partner opens it 3+ times in a week unprompted |
| Unblocked clients, charts, history | The job is "who's stuck right now" | Partners ask to see progress across all clients |

Rabbit holes, decided: due dates are calendar dates, no time zone math; sort is due date ascending, ties by client name; one token per firm, stored hashed, revoked by generating a new one; no pagination, since the biggest firm in your band has about 80 clients.

## Acceptance checks
1. Opening a firm's link shows that firm's blocked clients only: client, blocked step, reason, owner of the next step, due date.
2. Clients are ordered by due date, oldest first. Past-due rows say "Overdue" in text, not only in color.
3. A client shows up on the next page load after a step is set to blocked, and drops off once no step is blocked.
4. A link for one firm never shows another firm's clients, including when the token is edited by hand.
5. A wrong or revoked link shows the expired message, and the response contains no client data.
6. The page is readable on a phone without zooming [ASSUMPTION: partners check it between meetings].

## States
| State | What the partner sees |
|---|---|
| Empty | "Nothing's blocked right now. Any client that gets stuck will show up here." |
| Blocked, no reason entered | Reason column: "No reason yet. Ask <owner>." |
| Loading | Firm name and column headers, rows filling in |
| Error | "We couldn't load your clients. Try again in a minute, or reply to my last email." |
| Wrong or revoked link | "This link has expired. Ask [NEED: your first name] for a new one." |
| Big firm (about 80 clients, many blocked) | One scrolling list, headers stay visible |

## Data and tracking
- Data: new table `firm_view_links` (firm_id, token_hash, created_at, revoked_at). No new client fields. The page shows client names the firm already gave you for the pilot; no amounts, no account numbers, nothing from QBO or Xero.
- Did it work: does each partner open the page between Friday summaries without being asked? Answered by one server-side event, `partner_view_opened` (firm_id, link_id; no names or emails). Hand it to `product-analytics` to add to the tracking plan as the fifth event.

## Risks and open questions
- [NEED: last week's founder-hours] — you, today. If it's 10+, a trigger in the 2026-10-23 decision fires and we pick the first automation together.
- [NEED: do the partners forward links to staff?] — ask both when you send the link. Read-only access for staff is fine, but it changes who the expired message is talking to.
- Risk: a forwarded link shows client names outside the firm. Mitigation: revoke in one click; the email with the link says it's for their firm only.

## Build plan
| # | Step for the agent | Touches / pattern to copy | Done when (runnable) | Checks |
|---|---|---|---|---|
| 1 | Migration for `firm_view_links`; functions to create, revoke, and look up a firm by token (hash compared, never stored raw) | migrations folder; existing `firms` data access | Migration runs; unit tests: valid token finds the firm, revoked or edited token finds nothing | 4, 5 |
| 2 | Query for one firm's blocked clients, sorted | existing `close_steps` queries | Test with seed data (2 firms, blocked and unblocked rows) returns only the first firm's blocked rows, in order | 1, 2, 3 |
| 3 | Public read-only page at `/f/<token>`, outside the login wrapper | existing board table component | Page renders seed data locally; a wrong token gets the expired page and no client data in the response | 1, 2, 5 |
| 4 | Empty, no-reason, error and expired states with the copy above; phone layout | existing empty-state pattern | Each state shows with seed data at phone width | 6 |
| 5 | "Copy partner link" and "Revoke link" on the founder's firm page | founder admin page | You can create, copy and revoke; the old link shows expired | 5 |
| 6 | `partner_view_opened` on page load | existing `track()` helper | One `events` row per open, with firm_id and link_id only | — |

## Test it yourself in 5 minutes
1. On a pilot firm's admin page, click "Copy partner link" and open it in a private window. You should see only that firm's blocked clients, oldest due date first.
2. Block one client's step on the board and reload the link. It appears. Unblock it and reload. It's gone.
3. Change one character in the link. You should see the expired message and no client names.
4. Click "Revoke link" and reload the old link. Expired.
5. Open the new link on your phone. Readable without zooming.
6. Check the `events` table. One `partner_view_opened` row per open.

Logged to `.foundora/journal.md`:

```markdown
### 2026-11-02 — decision: Partner view of blocked clients specced
- Job: partner sees which clients are blocked and why without emailing; evidence: 2 of 2 pilot partners asked in week 1
- Appetite: 3 builder-days; 90/10 call: read-only page per firm behind a revocable link, no logins
- No-gos: QBO/Xero sync (2026-10-23 triggers still apply), partner logins, editing, alerts
- Open: last week's founder-hours [NEED]; revisit: end of pilot week 3 (2026-11-13)
- Source: feature-spec
```
