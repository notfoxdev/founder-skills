# Worked example (illustrative, fictional)

> Uses the fictional Ledgerline fixture (`evals/fixture-company.md`). It calibrates depth, format and tone only. Never copy its aha moment, steps, numbers or screen copy into a real answer.

## Request

"Priya finished the signup flow and the pilots start next week. I want to add a product tour so the ops leads know where everything is. The flow: Start pilot button on the site, signup form (name, email, password, firm name, firm size, role, phone), verify email, firm setup (fiscal year end, time zone, logo), invite at least one teammate to continue, connect QBO or Xero (small skip link), then an empty board with an Add client button that opens a form per client (client name, assignee, close due date, checklist template). Once clients are in, you tick off close steps."

## Context used

- `.foundora/company.md`: the Ledgerline fixture. Validation stage, 2 firms starting a free 30-day concierge pilot next week, no revenue. The partner buys; the ops lead and bookkeepers use it daily. Firms close 20–80 clients a month. The problem in the founder's words: partners can't see which clients are blocked. Working preferences: direct, tables, US spelling.
- `.foundora/journal.md`: not present. Nobody has used the product yet, so there are no stayers and the aha moment is a hypothesis.
- Date: Friday 2026-10-23. Kickoff dates `[NEED]`. October close runs in early November `[ASSUMPTION]`, so a board set up next week meets its first real close within days. That timing is good; don't lose it.
- No question asked first. The founder typed the whole path.

## Model answer

# Onboarding — Ledgerline — 2026-10-23
**Aha moment:** the ops lead sees every client in October's close on one board and ticks the first step done; the partner opens it and can tell which clients are blocked without asking anyone. Within the first week, before October close ends. Evidence: [ASSUMPTION] from the problem in company.md and your 4 years running close; confirm with the first 5 people who stay.
**Today:** 10 steps, 11 required fields plus 4 per client, 1 wait, 3 decisions. **New path:** 4 steps for the firm. You do the client load.
**Biggest change:** a 45-minute setup call with their own clients already on the board, before anyone logs in alone. The team invite moves to after the first tick.

Hold the tour. The best case for it: ops leads are busy and won't hunt for buttons. The problem is that it would explain an empty board, and nothing on an empty board is theirs to recognise. The setup call already is the tour, done on their own clients, with you there to answer questions. Test: ship without it. If 2 or more of the people you watch during the pilot miss the same control after the empty-state fix, add one hint at that control. Your call. I'll log whichever you pick.

## Step map (today)
| # | Step | What the user does | Before aha? | Reason it must come first | Verdict |
|---|---|---|---|---|---|
| 1 | Start pilot button | Click | Yes | The way in | Keep |
| 2 | Signup form | 7 fields | Yes | Email and password only. You already know name, firm, size and role from the pilot; phone is never used | Cut 5, keep email + password |
| 3 | Verify email | Wait, find the email, click | Yes | None until they invite someone | Defer |
| 4 | Firm setup | Fiscal year end, time zone, logo | Yes | Time zone sets due dates. Monthly close doesn't need fiscal year end; logo has no reason | Founder pre-fills time zone, defer the rest |
| 5 | Invite a teammate (required) | Type an email to continue | Yes | None. The ops lead's aha is solo | Defer to after the first tick |
| 6 | Connect QBO or Xero | Decide, approve access or skip | Yes | None. Status can be ticked by hand for 2 firms | Cut from onboarding |
| 7 | Empty board | Read, click Add client | Yes | Clients must be on the board | Replace with a pre-loaded board |
| 8 | Add client form | 4 fields, one page per client | Yes | Same | Founder does it |
| 9 | Repeat step 8 | 20–80 times | Yes | Same | Founder does it |
| 10 | Tick the first close step | Click | Aha | | Keep |

Totals: 10 steps; 11 fields before the first client (7 signup + 3 firm setup + 1 invite), then 4 per client, so 80 fields at 20 clients and 320 at 80 (4 x 20, 4 x 80); 1 wait (verification, plus an approval if they connect QBO or Xero); 3 decisions (connect or skip, which template, who to invite). Timed walk: [NEED: sign up fresh with a timer before Monday].

## Cut list
| Step | Verdict | Where it goes instead | What brings it back |
|---|---|---|---|
| Name, firm name, size, role, phone | Cut | You fill firm name before the call; the rest you know | Self-serve signups from outside the pilots: add firm name only |
| Email verification | Defer | Before the first invite | n/a |
| Fiscal year end, logo | Defer | Settings, after first close | A firm asks for it |
| Time zone | Pre-fill | You set it before the call | n/a |
| Team invite | Defer | A prompt right after the first tick | n/a, it stays after the aha |
| QBO / Xero connect | Cut | Settings, later | 2+ firms ask for it by name, or manual ticking becomes why people stop |
| Add client form | Founder does it | You paste their close sheet in the day before | Self-serve signups: a paste-from-spreadsheet import |

## New path
| # | Step | Who does it | Time | Aha reached? |
|---|---|---|---|---|
| 0 | Firm sends last month's close sheet; you paste it in and set the time zone | You | [NEED: time it on the first firm] | |
| 1 | Welcome email from you with one link | You | | |
| 2 | Sign in with email and password | Ops lead | [NEED: timed] | |
| 3 | Setup call on their own board; they tick the first step by minute 15 | Ops lead, you | 45 min | Ops lead's |
| 4 | Invite the partner from the prompt; partner opens the board | Ops lead, partner | | Partner's |

Founder-led setup: yes. 2 accounts is far under 20, the aha needs their own client list, and loading 20–80 clients through a form takes far longer than 15 minutes. It stops when the same stall shows up in 3 calls or setup passes 5 founder-hours a week. Neither will happen with 2 firms; the trigger matters once you add firms. Client data: send each firm one paragraph on what you'll see and where it's stored, and keep the boards out of anything you share publicly.

## Screen copy
### 1. Welcome email (from you)
- Headline (subject): Your October close board is ready
- Body: "Hi <name>, I loaded your clients from the close sheet you sent. Anything you'd marked done is done, the rest is open. On our call <day> you'll tick off the first one yourself. If anything looks wrong, reply here. It comes straight to me."
- Button: Open your close board

### 2. Sign in
- Headline: Sign in to <firm>'s close board
- Body: Use the email you gave us for the pilot.
- Button: Sign in
- Likely error: "That email isn't on a pilot board yet. Reply to my welcome email and I'll add it today."

### 3. Board, first view
- Headline: October close, <n> clients
- Body: Blocked clients are at the top. Tick a step when it's done and everyone on the board sees it.
- Empty state (a client with no steps): "No steps for <client> yet. Add the first one, like 'Bank rec: operating account'." Button: Add a step

### 4. Invite prompt, after the first tick
- Headline: Want <partner> to see this?
- Body: They'll see which clients are blocked without having to ask you.
- Button: Invite <partner>. Secondary: Not now

Read as a partner on day 3 of close: each line says what's on the screen or what happens next, in the words from your problem statement. Nothing here would fit another product.

## Test plan
| Change | Who gets it | Metric (n of N reach aha within window) | Baseline | Pass if | Fail if | How we'll see it | Decide by |
|---|---|---|---|---|---|---|---|
| Pre-loaded board, setup call, no tour, invite after first tick | Both pilot firms | Ops leads who tick a step on their own, outside the call, within 7 days; partners who open the board in the same week | None: first users | 2 of 2 on both | 0 of 2 on either | Board activity, plus a 5-minute check-in on day 7 | 7 days after the second kickoff [NEED: date] |
Diagnosis: watch every first solo session you can get across both firms, with consent, aiming for 5 [NEED: how many staff per firm will log in]. Talk to anyone who stops ticking for 3 working days during close. 2 firms is directional only; 1 of 2 means talk to the firm that didn't, before changing anything.

## Handoffs
- `product-analytics`: "first close step ticked" becomes the activation event.
- `lifecycle-emails`: a day-3 note from you if the ops lead hasn't ticked anything on their own.
- `feature-spec`: paste-from-spreadsheet import and the after-first-tick invite prompt, so the setup call stops being the only way in.

Logged to `.foundora/journal.md` (created):

```markdown
### 2026-10-23 — decision: Aha moment and onboarding cuts
- Aha moment: ops lead ticks the first close step on a board of their own clients; partner sees blocked clients unasked. Evidence [ASSUMPTION], no users yet
- Cut or deferred: 5 signup fields, verification, fiscal year end, logo, team invite, QBO/Xero connect; kept with reason: email, password, time zone (pre-filled)
- Founder-led setup: yes, stops at 3 repeated stalls or 5 founder-hours a week
- Product tour: not built; revisit if 2+ watched users miss the same control
- Source: onboarding
```

```markdown
### 2026-10-23 — experiment: Pre-loaded board with setup call
- Change: pre-loaded board, 45-minute setup call, invite after first tick, for both pilot firms
- Metric: ops leads ticking on their own and partners opening the board within 7 days, baseline none
- Pass if: 2 of 2 on both  Fail if: 0 of 2 on either  Directional: yes
- Decide by: 7 days after the second kickoff [NEED: date]
- Source: onboarding
```
