# Worked example: cold-outreach

> Illustrative and fictional (Ledgerline fixture). Calibrates depth and format only; never reuse its content.

## Request

"Write outreach to book 10 more interviews with managing partners."

## Context used

`.foundora/company.md` is the Ledgerline fixture (`evals/fixture-company.md`): 11 interviews so far (8 partners, 3 ops leads), 62 waitlist signups with 9 in the target size band, 2 pilot firms, CEO ran ops at a 9-person bookkeeping firm for 4 years, no paid budget. No journal, so there is no positioning line to reuse. This is discovery, so the drafts pitch nothing. No named recipients and no signals yet, so every personal hook is a `{{field}}` with a word cap and stays `[UNVERIFIED]` until checked. No questions asked.

## Model answer

# Outreach: customer discovery, managing partners at 3–15 staff bookkeeping firms (2026-10-21)

**Send plan:** warm first: ask the 8 partners you already interviewed for one intro each, and invite the in-band waitlist firms that are not in a pilot. Then about 100 cold contacts (base case) by email at 15–25 a day. Decision point after 50 sends.

Don't open with cold email. You already have warm paths that should cover part of the 10, and a waitlist signup who gets a cold sequence feels spammed.

## Brief
- **Recipient:** managing partners at bookkeeping firms with 3–15 staff closing books for 20–80 clients. They buy; their view of close status is the research question.
- **Ask:** a 15-minute call next week.
- **Give:** a chance to shape the tool, and a short summary of how other firms run close, if they want it.
- **Tier:** segment template, one trigger field.
- **Volume:** 10 interviews ÷ booked rate per contact `[ASSUMPTION]`. Pessimistic 5% = 200 contacts (about 10 sending days). Base 10% = 100 (about 6 days: 5 × 15 + 1 × 25). Optimistic 20% = 50 (about 4 days). Warm bookings reduce these one for one.

## Signals
| Signal | Source | Date | Status |
|---|---|---|---|
| Firm job post for a bookkeeper or ops role | Job board listing | {{date}} | [UNVERIFIED] until opened |
| Partner's post about month-end close in a bookkeeping community | Community post URL | {{date}} | [UNVERIFIED] |
| Firm size from its team page (segment-level fallback) | Firm website | {{date}} | [UNVERIFIED] |

No signal older than 6 months. If none is found, use the segment-level line ("you run a firm of about {{n}} people") or skip the firm.

## Sequence
| Touch | Day | Channel | Purpose | Words |
|---|---|---|---|---|
| 1 | 0 | Email | Reason, who you are, one ask | 64 fixed + 20 cap = 84 max |
| 2 | 4 | Email (thread) | New angle: one founder-provided pattern from the 11 interviews | 37 fixed + 15 cap = 52 max |
| 3 | 8 | LinkedIn | Different channel, smaller ask (connect) | Under 200 characters |
| 4 | 14 | Email (thread) | Breakup | 25 |

## Drafts
### Warm A: past partner interviewees (8)
> Hi {{first_name}}, thanks again for talking me through your close process. I'm doing 10 more conversations with managing partners. Is there one partner at another firm you think I should talk to? A name is plenty; I'll mention you only if you say that's fine.

### Warm B: in-band waitlist firms not in a pilot
> Hi {{first_name}}, you joined the Ledgerline waitlist in {{month}}. I'm talking to managing partners about how they run month-end close. Would 15 minutes next week work? No demo, just questions.

### Touch 1: Email
Subject options: 1) month-end close at {{company}} 2) how you track close status 3) question about your month-end close

> Hi {{first_name}},
>
> {{reason_for_you}}.
>
> I ran operations at a 9-person bookkeeping firm for four years. I'm now researching how firms your size run month-end close, especially how partners see which clients are blocked.
>
> I'm not selling anything. Would you give me 15 minutes next week to walk me through how you track it today?
>
> If this isn't relevant, just say so and I won't follow up.
>
> {{sender}}, Ledgerline
> {{postal_address}}

### Touch 2: Email reply
> {{first_name}}, one thing from 11 interviews with bookkeeping partners and ops leads so far: {{pattern_from_interviews}}. I'm trying to learn whether that holds for firms like {{company}}. Even a one-line reply on how you track close status would help.

### Touch 3: LinkedIn note (<200 chars)
> Hi {{first_name}}, I ran ops at a 9-person bookkeeping firm and I'm researching how partners track month-end close. Open to connecting?

### Touch 4: Breakup
> I'll stop here, {{first_name}}. If month-end close becomes something you want to fix, I'd still like to hear how {{company}} runs it. Thanks either way.

## Personalisation fields
| Field | Description | Example source | Word cap | Required |
|---|---|---|---|---|
| {{first_name}} | Partner's first name | Firm team page | 1 | yes |
| {{reason_for_you}} | Specific, verified reason this partner, now | Job post, community post, team page | 20 | yes |
| {{company}} | Firm name | Firm website | 4 | yes |
| {{pattern_from_interviews}} | One real pattern from your 11 interview notes, no names | Founder's notes | 15 | touch 2 only |
| {{month}} | Month they joined the waitlist | Waitlist export | 1 | warm B only |
| {{postal_address}} | Valid postal address for the sender | Founder | n/a | yes |

## Send checklist
- [ ] Domain authenticated (SPF, DKIM, DMARC) and the sending inbox in normal use for 2–4 weeks
- [ ] Addresses verified; pause if hard bounces pass 2%
- [ ] Opt-out line, sender identity, postal address present
- [ ] 15 new contacts a day in week 1, up to 25 in week 2
- [ ] Every {{reason_for_you}} verified, none older than 6 months
- [ ] Stop on any reply; suppress opt-outs across all tools

Decision rule: after 50 cold sends, fewer than 3 positive replies (under 5%) means fix targeting or the reason line before sending more. Change one variable at a time.

## Open data
- [NEED: whether the 2 pilot firms are among the 9 in-band waitlist firms]
- [NEED: role of each in-band waitlist signup; warm B goes only to partners]
- [NEED: one pattern from the 11 interview notes for touch 2]
- [NEED: recipient countries; anyone outside the US gets the country check in deliverability.md]
- [NEED: is the ledgerline.app sending inbox warm?]

## Logged
```markdown
### 2026-10-21 — experiment: Discovery outreach to managing partners, batch 1
- Sent: warm asks to 8 past interviewees and in-band waitlist partners, then 50 cold emails; ask: 15-minute call
- Variable tested: none (baseline)
- Result: fill in at day 14 as a new entry
- Decision rule: under 3 positive replies after 50 cold sends means fix targeting before batch 2; goal is 10 booked by 2026-11-18
- Source: cold-outreach
```
