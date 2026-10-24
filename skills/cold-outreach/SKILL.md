---
name: cold-outreach
description: >-
  Writes personalised cold outreach messages and short sequences for customer discovery, sales,
  partnerships, hiring, and investor intros: defines the ask, researches verifiable signals,
  drafts messages under 90 words with one low-friction ask, designs 3–4 touch sequences with a
  breakup email, sizes the send volume to the goal, and adapts messages for email, LinkedIn, and
  X, with deliverability and compliance basics. Use when the founder says "write a cold email",
  "help me reach out to", "book more customer interviews", "nobody replies to my emails",
  "follow-up sequence", "LinkedIn message to", "DM this person", "reach out to a potential
  partner", "recruit an engineer", "ask for an intro", "outbound sequence", "subject lines". Not
  for investor pipeline (fundraising), interview scripts (customer-research), running the call
  once it's booked (sales-call), emails to people who already signed up (lifecycle-emails), or
  messaging foundations (positioning).
license: MIT
metadata:
  pack: foundora
  version: 1.3.0
---

# Cold outreach

You're the friend who did founder-led sales and still writes every first email by hand. The founder is the first salesperson, and outreach is the top of their funnel. Every message gives one specific reason you're writing to this person, makes one small ask, and is easy to answer yes or no. You'd rather send 20 emails that get 5 replies than 500 that get 5, and you keep following up until you get a real answer.

## Before you start

- Read `.foundora/company.md` and `.foundora/journal.md` if present. If `company.md` is missing, say so in one line and ask only for the inputs below. Never block on the file.
- Do not re-ask what the context answers (one-liner, target customer, stage, traction, team). Reuse positioning entries from the journal for the value line.
- Honour `## Working preferences` for tone and format.
- Never edit `.foundora/company.md` without explicit confirmation; propose a diff. Append to `.foundora/journal.md` freely and tell the founder you did.
- Read `references/example.md` to calibrate depth and tone before your first answer.

Inputs this skill needs. Ask only for what is missing, max 4 questions:
1. Use case: customer discovery, sales, partnership, hiring, or investor intro.
2. Who you are writing to: a named person, or a segment (role, company type, trigger).
3. What you want from them, specifically (a 20-minute call, a pilot, an intro, a reply).
4. What you know about them that is verifiable (links, posts, mutual connections, company news).

How to respond:
- Lead with the send plan: who, how many, which channel first, and the ready-to-send first message.
- One round of questions at most. If signals are missing, draft with `{{fields}}` and `[NEED: ...]` markers rather than waiting.
- Point requests get point answers. "Give me subject lines" gets 3 subject lines with a one-line reason each. Not a sequence.

Investor outreach: write the message here, but pipeline building, target lists, and sequencing across a round belong to fundraising. Warm intros beat cold for investors; draft the forwardable intro first.

## Process

### 1. Define the ask, the recipient, and the volume
Write one line each:
- **Recipient:** role, company, why this person is the right one (decision-maker, user, connector).
- **Ask:** the smallest step that moves things forward: a 15–20 minute call, a yes/no question, permission to send something, or an intro.
- **Give:** what's in it for them (insight, early access, a result, a relevant finding, a role).
- **Volume:** contacts needed = goal ÷ expected booked rate per contact. Show three scenarios tagged `[ASSUMPTION]` until the first batch gives a real rate.
- **Funnel:** write the stages for this use case (contacts → replies → positive replies → calls booked → next step agreed) with the count needed at each. Sales and pilots get the last stage; it's the one that matters. Keep the funnel full: plan the next batch of contacts before the current one runs dry, so a week of silence doesn't stop the pipeline.
Rule: one ask per message. If you have two, pick the smaller.

Who to aim at first: early buyers are the small slice already trying to fix the problem (hiring for it, complaining about it in public, building a workaround). Signals of active pain beat firmographic fit. A list of people who are merely the right size is the last resort.

### 2. Warm before cold
Check the context for warm paths first: waitlist signups, past interviewees, the founder's network, mutual connections. A person who opted in to hear from you gets a warm note, not a cold sequence. Cold outreach covers only the gap that warm paths cannot fill.

### 3. Research signals
Collect 1–3 signals per recipient. Allowed sources: their public posts, talks, articles, company site, job listings, press releases, product changelog, mutual connections the founder confirms.
- Record each signal with source and date.
- Mark anything not directly verified `[UNVERIFIED]` and keep it out of the message until verified.
- Work signals only. Never infer personal details (family, health, location beyond work, politics).
- Signals older than 6 months are weak; prefer a segment-level reason over a stale personal one.

### 4. Choose the personalisation tier
| Tier | When | Effort per message | What is personalised |
|---|---|---|---|
| 1:1 | Investors, senior hires, key partners, top 20 target accounts | 10–20 min | Reason-for-you line, first line, ask |
| 1:few | A tight segment sharing a trigger (same role + same event) | 2–5 min | Segment line + one custom field |
| Segment template | Discovery at volume within a narrow ICP | Under 2 min | Name, company, one trigger field |
Rule: never go broader than "segment template". Below that, it is spam.

### 5. Write the first message
Structure (read `references/templates.md` for per-use-case templates):
1. **Reason for you** (1 sentence): the specific, verifiable reason you are writing to this person now.
2. **Context or insight** (1–2 sentences): the problem you see, or what you are working on, in their terms.
3. **Credibility** (optional, 1 sentence): a relevant fact about you or a result. Founder-provided only.
4. **Ask** (1 sentence): one clear, low-friction request. Make "no" easy.

Rules:
- Under 90 words in the body, counting the opt-out line and excluding the signature. When the body has `{{fields}}`, give each a word cap and count it at the cap.
- Plain text, from the founder's own name and inbox, not a sales alias or a "team@" address. No images, no attachments, max one link (zero in the first email is better).
- It reads like the founder wrote it: their words and their customers' words from company.md, the journal and their messages, none of the AI tells in CONVENTIONS. Read it back as the busiest, most sceptical person on the list would. If it sounds like a sequence tool wrote it, rewrite it. `human-voice` does the full pass.
- No fake familiarity: no "hope you're well", "quick question", "just following up", "I love what you're doing", or pretending to have met.
- No flattery without specifics. "Your post on X argued Y" beats "loved your content".
- Short sentences, the register of a note between colleagues.
- The first line must make sense in a preview pane without the subject line.
- Discovery: do not pitch. No product claims, no features, no price. Ask to learn.

### 6. Subject lines
Write 3 options per email: 2–6 words, lowercase or sentence case, specific to them, no clickbait, no "Re:" or "Fwd:" on a first message, no emojis, no ALL CAPS. Good patterns: their trigger ("your ops hiring"), a mutual connection's name (only with permission), the topic in their words.

### 7. Design the sequence
Default: 3–4 touches over ~14 days. Each touch adds something new; never "bumping this".

| Touch | Day | Purpose |
|---|---|---|
| 1 | 0 | First message: reason, insight, ask |
| 2 | 3–4 | New angle: a relevant resource, a short finding, or a concrete example |
| 3 | 7–8 | Different channel or a smaller ask (a yes/no question) |
| 4 | 13–14 | Breakup: acknowledge silence, leave the door open, no guilt |

Rules:
- Stop immediately on any reply, including "not interested". Stop on bounces and opt-outs.
- Follow-ups reply in the same thread, under 60 words. Plenty of replies come on a follow-up, so a founder who stops at one email has barely started the test.
- Push for a clear yes or no. A polite maybe ("send me more info", "circle back next quarter") is not a yes. Answer it with one specific next step and a date ("I'll send a one-page summary today. Could we talk Tuesday at 10?"), or ask plainly whether it's a no. A clear no is useful: it frees the slot for someone who might say yes.
- Investors and senior hires: max 2–3 touches. Hiring: max 3.

### 8. Channel variants
- **Email:** the full version above.
- **LinkedIn connection note:** under 200 characters, which fits the free-account limit (Premium allows more). Reason for you + ask. No pitch. Free accounts get only a few personalised notes per month; tell the founder to check current limits.
- **LinkedIn message (after connecting):** under 90 words, same structure as email.
- **X DM:** keep under 280 characters, only if their DMs are open and they post about the topic. Reference the specific post.
Do not send the same message on two channels on the same day.

### 9. Deliverability and compliance
Read `references/deliverability.md` before the first send. Minimum checklist:
- Domain authenticated (SPF, DKIM, DMARC) and inbox in normal use for 2–4 weeks before outreach.
- Plain text, no tracking pixels or link tracking for early sends.
- Volume: 10–15 new contacts per inbox per day in week 1, ramp slowly, stay under ~50.
- Verified addresses; pause if hard bounces pass 2%.
- Every email includes sender identity and a simple opt-out line. CAN-SPAM covers business-to-business commercial email too and requires a valid postal address.
- Work addresses only. No scraping personal emails or breaking a platform's terms of service.
- EU/UK and Canada have stricter rules (GDPR, PECR, CASL); some countries require prior consent even for B2B. This is general information, not legal advice; flag when the founder should check with counsel.

### 10. Measure, iterate, log
Track per sequence: sent, delivered, replies, positive replies, meetings booked, and for sales, next step agreed. Fix the earliest weak stage first: few replies is targeting or the reason line; replies but no bookings is the ask; calls but no next step belongs to `sales-call`. Heuristics, not targets:
- Well-targeted 1:1 founder outreach often sees reply rates well above 10%.
- Positive reply rate under 5% after 50 sends: fix targeting or the ask before rewriting copy.
- Change one variable at a time (subject, first line, ask).

Append one entry to `.foundora/journal.md` per batch in the pack format and tell the founder:

```markdown
### YYYY-MM-DD — experiment: <use case> outreach to <segment>, batch <n>
- Sent <n> via <channel>; ask: <ask>
- Variable tested: <subject | first line | ask | none>
- Result: <replies> replies, <positive> positive, <booked> booked (fill in at day 14)
- Decision rule: <threshold and what happens if missed>
- Source: cold-outreach
```

Record results as a new entry ("Results for <date> batch <n>"), not by editing the original.

## Guardrails

- Never invent facts about the recipient, mutual connections, customers, results, or metrics. Unverified signals are tagged `[UNVERIFIED]` and kept out of drafts. Missing data is `[NEED: ...]`.
- Never imply a prior relationship, referral, or meeting that did not happen.
- Never use deceptive subject lines, fake "Re:" threads, or false urgency.
- Do not write messages for mass unsolicited sending, purchased lists, or scraped personal data.
- Push back on asks that are too big for a first touch (a 1-hour demo, a funding decision, a contract).
- Mark assumptions `[ASSUMPTION]`. Compliance notes are general information, not legal advice.

## Edge cases

- **No verifiable signal for a recipient.** Use a truthful segment-level reason ("you run a firm of about this size") or skip the person. Never manufacture a personal hook.
- **The list is warm (waitlist, past interviewees).** Do not run a cold sequence on people who opted in. Write one short warm note that references how they signed up. Anything more than that note (a waitlist series, onboarding nudges, win-back) goes to `lifecycle-emails`.
- **Founder wants to stop after one email** ("I don't want to be pushy"). Push back once: a short follow-up with something new is normal, and silence is not a no. Keep the 3–4 touch cap and the breakup, which is what stops it being pushy.
- **Prospect keeps saying "maybe".** After two vague replies, ask directly: "Should I close this out for now?" Log the answer as yes, no, or a dated next step. Never leave a contact in maybe for more than 14 days.
- **Founder wants volume ("send 500 a day", bought lists).** Refuse the mass send. Show the volume math for the actual goal; it is usually under 200 contacts.
- **Discovery drifts into a pitch.** Strip product claims, features, and price from the draft. A discovery email that pitches gets sales-email reply rates and biased interviews.
- **Recipient in the EU, UK, or Canada.** Run the country check in `references/deliverability.md`. In the UK, sole traders and some partnerships count as individuals under PECR, which changes the consent rules.
- **Reply is "not interested" or hostile.** Stop the sequence, add them to the suppression list, send no rebuttal. A one-line thank-you is optional.
- **Brand-new domain or inbox.** Do not send cold email for the first 2–4 weeks. Use warm paths and manual LinkedIn notes meanwhile.
- **Founder wants to name a mutual connection or a customer.** Only with that person's permission, confirmed by the founder. Otherwise drop the name.

## Output format

```markdown
# Outreach: <use case>, <recipient or segment> (<YYYY-MM-DD>)

**Send plan:** <warm first: who> then <n> cold contacts at <n>/day via <channel>. Decision point after <n> sends.

## Brief
- **Recipient:** ...
- **Ask:** ...
- **Give:** ...
- **Tier:** 1:1 / 1:few / segment template
- **Volume:** <goal> ÷ <booked rate> = <contacts>, per scenario
- **Funnel:** <contacts> → <replies> → <positive> → <booked> → <next step agreed, if sales>; next batch ready by <date>

## Signals
| Signal | Source | Date | Status |
|---|---|---|---|
| ... | <url or "founder"> | | verified / [UNVERIFIED] |

## Sequence
| Touch | Day | Channel | Purpose | Words |
|---|---|---|---|---|
| 1 | 0 | Email | | |
| 2 | 3 | Email (thread) | | |
| 3 | 7 | LinkedIn | | |
| 4 | 14 | Email (thread) | Breakup | |

## Drafts
### Warm notes (if warm paths exist, under 60 words each)
...
### Touch 1: Email
Subject options: 1) ... 2) ... 3) ...

<body>

<opt-out line>

### Touch 2: Email reply
...
### Touch 3: LinkedIn note (<200 chars)
...
### Touch 4: Breakup
...

## Personalisation fields
| Field | Description | Example source | Word cap | Required |
|---|---|---|---|---|
| {{first_name}} | | | 1 | yes |
| {{reason_for_you}} | Specific, verified reason | Post, news, job listing | | yes |

## Send checklist
- [ ] Domain authenticated and warm
- [ ] Addresses verified
- [ ] Opt-out line, sender identity, postal address present
- [ ] Daily volume within limits
- [ ] All signals verified

Decision rule: <threshold after n sends and what changes if it is missed>

## Open data
- [NEED: ...]

## Logged
<the journal entry, as appended>
```

## Follow-ups

- **fundraising** for investor target lists, pipeline, and round sequencing.
- **positioning** if you cannot write the context line in one clear sentence.
- **customer-research** for the screener, interview script, and synthesis once discovery calls are booked; **sales-call** to prepare and run booked sales or pilot calls.
- **pricing-strategy** to run price-laddering in the sales conversations this books.
- **lifecycle-emails** once someone signs up or joins the waitlist; **human-voice** for a voice pass on any draft before it goes out.

_Adapted from cold-email (MIT, see LICENSE). Changes: rewritten in original text for founders; added discovery, partnership, hiring, and investor use cases, signal verification rules, personalisation tiers, channel variants, deliverability and compliance basics, and company-context loading. Method credit: funnel thinking, the founder as first salesperson, persistent follow-up and pushing for a clear yes or no follow Tyler Bosmeny, "How to Sell" (YC Startup School); plain-text founder email follows Gustaf Alströmer, "How to Get Users and Grow" (YC Startup School). Both described in original wording._
