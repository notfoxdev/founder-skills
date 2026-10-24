# Worked example (illustrative, fictional)

> Uses the fictional Ledgerline fixture (`evals/fixture-company.md`). It calibrates depth, tone and format only. Never copy its content, facts or wording into a real answer.

## Request

"Can you write the emails for our waitlist? 62 people. Pilots start next week and I want the next firms lined up behind them."

## Context used

- company.md: 62 waitlist signups, 9 from firms in the 3–15 staff band; 2 firms start a free 30-day concierge pilot next week; no revenue; 90-day goal is 3 firms paying at least $150/month; CEO ran ops at a 9-person bookkeeping firm for 4 years; Priya is CTO; ledgerline.app is a waitlist page only; tone direct, tables over paragraphs, US spelling.
- No journal, so no aha moment and no voice notes. There is no self-serve product, so activation and trial emails don't apply yet.
- Not known: what the waitlist page promised, when people signed up, whether the 2 pilot firms are among the 9, and how the founder sends email. All go in Open items; no questions asked first.
- The hard part: the obvious move is one email to all 62. That wastes the 9 firms who could become the third paying customer.

## Model answer

# Lifecycle emails — Ledgerline — 2026-10-21

**Plan:** 3 emails now, 1 later. The 9 in-band firms get a personal note typed from your inbox, asking for a 20-minute call, and one follow-up. The other 53 get one honest update with a question that sorts them. First send: the 9 personal notes, this week, before the pilots take over your calendar.
**Cut:** a 5-email welcome drip (nothing to onboard into yet; fails "something new"), a weekly newsletter (no weekly news; fails "cost of silence"), an activation nudge (no self-serve product; no trigger), a pilot announcement to all 62 (it's one line inside email 3, and the public version belongs to `launch`).

Why not one email to everyone: 9 people is well under the by-hand line of about 50, and each of those firms could be worth $150/month. Your 90-day goal needs 3 paying firms and you have 2 free pilots, so even if both convert you need at least one more. Those 9 are where it most likely comes from.

## Email plan
| # | Email | Group (n) | Trigger | One job | Sent how | Timing | Exit when | Reason to exist |
|---|---|---|---|---|---|---|---|---|
| 1 | Personal note | In-band firms (9, minus any pilot firms) | Fits the target, not yet talked to | Book a 20-minute call | By hand, founder inbox | This week | Reply, booked, or no | Pass: your next customer is most likely in this group |
| 2 | Follow-up | Email 1, no reply | 5 working days of silence | Get a one-line answer | Same thread, by hand | Day 5 | Any reply | Pass: smaller ask, new question |
| 3 | Honest update | Other 53 | No email since signup [ASSUMPTION] | Reply with firm size and client count | Sending tool, with footer | Next week | Reply or unsubscribe | Pass: sorts the 53; some may be in-band and unrecorded |
| 4 | Open-to-you note | Everyone left on the list | Pilots end and you can take on new firms | Book setup | Later | ~4–5 weeks out | Booked | Not written now: no trigger yet |

## Drafts
### 1. Personal note — to in-band firms
From: [NEED: founder name] <[NEED: address]@ledgerline.app> | Reply-to: same
Subject options: 1) month-end close at {{firm}} 2) your Ledgerline signup 3) a question about your close

Hi {{first_name}},

You joined the Ledgerline waitlist in {{month}}. I'm [NEED: first name], one of the two people building it. I ran ops at a 9-person bookkeeping firm for four years, so I know close from the inside.

Two firms start a free pilot with us next week. Before we take on more, I'd like to hear how {{firm}} runs month-end close today: who tracks it, and where it slips.

Could you do 20 minutes next week? Reply with a time that suits you, or tell me it's not for you. Either answer helps.

[NEED: first name]

> Why: these 9 are the shortlist for firm number 3. A call teaches you more than a click, and the "not for you" line makes no easy to say.

### 2. Follow-up — same thread, day 5, no reply

Hi {{first_name}}, one more try and then I'll leave it. If a call is too much, a one-line answer helps just as much: how do you see which clients are still blocked at month-end?

[NEED: first name]

> Why: a smaller ask, plus a new question in the partners' own words from company.md. No "bumping this".

### 3. Honest update — to the other 53
From: [NEED: founder name], Ledgerline | Reply-to: the founder's inbox, not noreply
Subject options: 1) two firms start Ledgerline next week 2) where Ledgerline is 3) a question from Ledgerline

Hi {{first_name|there}},

You signed up for the Ledgerline waitlist at ledgerline.app. Here's where we are.

Ledgerline is a month-end close checklist for bookkeeping firms with 3 to 15 staff. Two firms start a free 30-day pilot next week. We'll open it to more firms slowly after that, and I'll write when there's room [NEED: realistic month].

Could you reply with how many people work at your firm, and roughly how many clients you close each month? One line is plenty. It tells me whether we're building for you yet.

[NEED: first name]
Ledgerline

You're getting this because you joined the Ledgerline waitlist. Unsubscribe: {{unsubscribe_link}}. [NEED: postal address]

> Why: some of the 53 may be in-band but unrecorded. Anyone who replies with 3–15 staff moves to email 1 the same day.

Voice check: read as a managing partner between two client calls, each email states its point in the first three lines and none sounds like a newsletter. No em dashes, no exclamation marks, no "excited to share".

## Measurement
| Email | Sent | Replies | Did the action | Unsubscribes | Decision rule |
|---|---|---|---|---|---|
| 1 + 2 | 9 [NEED: minus pilot firms] | | Calls booked | | Pass: 3 calls booked within 10 working days. Under 2 replies after the follow-up: phone or LinkedIn them, and check what the waitlist page promised |
| 3 | 53 | | Firm size given | | Every 3–15 staff reply moves to email 1. Unsubscribes outnumbering replies: reread the page's promise before the next send |

These are house rules. With 9 people every result is directional, so read each reply rather than computing a rate.

## Open items
- [NEED: whether the 2 pilot firms are among the 9] If they are, email 1 goes to 7.
- [NEED: role of each in-band signup] Email 1 asks about running close; a bookkeeper who signed up may not be the partner who buys. Ask them who is.
- [NEED: what the waitlist page promised] If it promised early access, email 3 should say plainly when that is.
- [NEED: sending setup] Emails 1–2 from your own inbox. Email 3 needs a tool with an unsubscribe link, plus SPF, DKIM and DMARC on ledgerline.app.
- [NEED: price for firm 3] Decide before these calls whether the next firm pilots at $150/month from day one. `pricing-strategy` can set that up.
- [ASSUMPTION] Nobody on the list has been emailed since signing up.

## Send checklist
- [ ] Founder read every draft
- [ ] Everyone on the list opted in to hear about Ledgerline
- [ ] Reply-to reaches the founder; no noreply address
- [ ] Unsubscribe and postal address on email 3
- [ ] Domain authenticated (SPF, DKIM, DMARC)

Logged to `.foundora/journal.md`:

```markdown
### 2026-10-21 — decision: Waitlist email plan
- Emails: personal note + follow-up to 9 in-band firms (by hand), honest update to the other 53 (tool), open-to-you note when pilots end
- Cut: welcome drip, weekly newsletter, activation nudge, all-list pilot announcement (no trigger or no news)
- Sent how: by hand for in-band; automate nothing until a note has gone out about 10 times
- Revisit: when the pilots end (about 30 days after kickoff)
- Source: lifecycle-emails
```

```markdown
### 2026-10-21 — experiment: Personal note to in-band waitlist firms
- Sent: 9 [NEED: minus pilot firms] this week, by hand; one job: book a 20-minute call
- Pass if: 3 calls booked within 10 working days; prior: none
- Result: fill in as a new entry on 2026-11-04
- Source: lifecycle-emails
```
