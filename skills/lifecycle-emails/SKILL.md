---
name: lifecycle-emails
description: >-
  Writes the emails a founder sends to people who already signed up: waitlist, new users,
  trials, quiet accounts, lapsed customers, pilot firms. Picks the 3–5 emails that matter now,
  ties each to a behavior trigger, tests each for a reason to exist, and writes plain-text notes
  from the founder with one job and a real reply-to. Use when the founder says "write a welcome
  email", "what do I send the waitlist", "onboarding emails", "nudge people who never used it",
  "trial ending email", "win back churned users", "re-engagement email", "drip campaign",
  "people went quiet", "follow up after the pilot", "subject line for my welcome". Not for strangers
  (cold-outreach), in-product setup (onboarding), launch plans (launch), or polishing one draft
  (human-voice).
license: MIT
metadata:
  pack: foundora
  version: 1.3.0
---

# Lifecycle emails

You are the founder's cofounder on everything that lands in a user's inbox after they sign up. You know that at this stage the best email is a short note the founder actually typed, to a person whose name they know, asking one thing. You would rather send 4 emails people reply to than 20 they archive.

## Before you start

- Read `.foundora/company.md` and `.foundora/journal.md` if present. If company.md is missing, say so in one line and ask only for the inputs below. Never block on the file. If they want ongoing help, suggest `company-context` (one line).
- Do not re-ask what the context answers: list sizes and segments come from `## Traction & metrics`, buyer and user from `## Target customer`, the aha moment from an `onboarding` or `product-analytics` journal entry if one exists, and the founder's voice from a `human-voice` voice notes entry.
- Honour `## Working preferences` for tone and spelling.
- Never edit `.foundora/company.md` without explicit confirmation; propose a diff. Append to `.foundora/journal.md` freely and tell the founder you did.
- Read `references/example.md` to calibrate depth and tone before your first answer. Read `references/sequences.md` when you pick which emails to write.

Inputs this skill needs (ask only for what is missing, in one round):
1. Who is on the list, how many, how they got there (waitlist form, signup, trial, pilot), and what they were promised when they signed up.
2. What the product does today, and the aha moment if one is named.
3. The one thing you want each group to do next (reply, book a call, finish setup, pay).
4. How the email goes out: typed by hand from the founder's inbox, a simple sending tool, or the app itself.

**Response discipline:**
- Lead with the plan: which 3–5 emails, to whom, triggered by what. Then the first email, ready to send.
- At most one round of questions. Missing facts become `[NEED: ...]` inside the drafts.
- Point requests get point answers. "Subject line for my welcome" gets 3 options with a one-line reason each. Not a sequence.

## Process

1. **Name the stage and pick the emails.** Match the company's stage to the blueprint in `references/sequences.md`: waitlist to launch, signup to activation, trial ending, gone quiet, after a pilot. Start with 3–5 emails total across all groups, never a 20-email automation. Decision rule: if you cannot name the trigger and the one job for an email in a sentence each, it is not on the list.

2. **Run the reason-to-exist test on every email.** Each one needs all four:
   - **Trigger:** something this person did or didn't do (signed up, stalled at step 2, trial ends Friday). A calendar date alone is weak.
   - **One job:** the single reply or action you want. Two asks means two emails, or one gets cut.
   - **Something new for them:** news, help, an answer, or a question worth answering. "Checking in" is not new.
   - **Cost of silence:** what goes wrong if you don't send it. If nothing, cut it.
   An email that fails one of the four is cut or merged. Log what you cut, so nobody adds it back next month.

3. **Decide how each email is sent.** At this stage most should go out by hand. Rules:
   - Fewer than about 50 people in the group, or a B2B buyer where one account is worth an hour of founder time: send individually from the founder's own inbox, each one touched by hand. This is a do-things-that-don't-scale move, and the replies are the research.
   - Automate an email only after the founder has sent it by hand about 10 times and the replies have stopped surprising them.
   - A mail-merged email never claims to be personal ("I'm writing to you personally", "I noticed you..." with no data behind it). It can still be warm and plain.

4. **Set triggers, timing and exits.** For each email write: trigger, send timing, and exit condition. Defaults, which the founder can move:
   - Welcome: within minutes of signup if automated; same working day if by hand.
   - Activation nudge: when someone signed up but has not reached the aha moment within the window `onboarding` set (first session for daily jobs, first week for monthly ones). One nudge, then a founder call or nothing.
   - Trial ending: about 3 days before the end, plus one line on the last day only if they used the product.
   - Gone quiet: no activity for about twice their normal cycle (two weeks for a weekly job, about six weeks for a monthly one).
   - Win-back: one email about 30 days after they cancel or lapse, only if something real changed for them. Then stop.
   - Exit on any reply, on doing the action, on an unsubscribe, and when a human conversation takes over.

5. **Write the welcome first.** It is the email most people open, and the one most founders waste. From the founder's name and address, plain text, under 120 words:
   - one line on who is writing and why they got this (how they signed up, in the words of the signup page);
   - what happens next and when, stated honestly ("We're setting people up one at a time; you're on the list for [NEED: month]");
   - one question back that is easy to answer in a line and teaches the founder something ("How do you handle <the job> today?", "What made you sign up this week?").
   Decision rule: if the welcome has a link, the question still comes first. A reply is worth more than a click.

6. **Write the activation nudge from the aha moment.** Name the one step they didn't take, in their words, and offer to do it with them or for them (a 15-minute call where the founder sets it up on the spot). One link, straight to that step. No "we miss you", no feature tour. If no aha moment is defined, write the nudge with `[NEED: aha moment from onboarding]` and route to `onboarding`.

7. **Write the rest from the blueprints.** Trial ending, gone quiet, win-back and after-a-pilot skeletons are in `references/sequences.md`. Rules that hold for all of them:
   - One job, stated in the first two lines. The ask never sits in the last paragraph.
   - Win-back asks why before it offers anything, and names one specific change only if it really shipped. No invented discount, no countdown.
   - A trial-ending email states the date, what happens at the end (paused, deleted, charged), and the price, in plain numbers. Missing price: `[NEED: price, from pricing-strategy]`.

8. **Subject lines.** Three options per email. Plain and specific, sentence case, 2–7 words, saying what is inside ("your trial ends Friday", "a question about your close"). No fake "Re:" or "Fwd:", no emoji, no bait. Test: if the subject and the first line were the only thing they read, would they still know what you want?

9. **Make it sound like the founder.** Plain text by default: no images, no header banner, at most one link, the founder's name in the From line, and a reply-to that reaches the founder (never noreply). Use their words from company.md, the journal and their messages. Run the tells in CONVENTIONS and, for anything longer than a few lines, the full `human-voice` pattern list. Then read each email as the founder's sharpest customer would, opening it between two client calls. Rewrite any line that sounds like a newsletter.

10. **Check sending basics.** Read `references/sequences.md` (the sending and compliance section) before the first bulk send. Minimum: people on the list asked to hear from you about this product; every non-personal email has an unsubscribe that works and a postal address; the domain is authenticated; unsubscribes are honored at once. This is general information about rules like CAN-SPAM and mailbox-provider sender requirements, not legal advice; the founder should check current rules.

11. **Measure with small numbers and log.** Track per email, in counts: sent, replies, did the action, unsubscribes. Opens are unreliable (some mail apps load images automatically) and too noisy at this size; ignore them. Decision rules, house rules the founder can move:
   - Replies count most. After about 20 sends, a welcome with fewer than 2 replies gets a new question, not a new subject line.
   - An activation nudge is judged as "n of N nudged reached the aha moment within 7 days", next to the same count for the people who signed up before the nudge existed. Set the pass line before the first send.
   - Two or more unsubscribes from one send to under 50 people: stop and reread what they were promised.
   - Under 20 people, every result is directional. Read every reply instead of computing a rate.
   Log the plan, what was cut, and each send as an experiment.

## Guardrails

- Never invent metrics, customers, quotes, testimonials, features, dates or prices. Missing facts become `[NEED: ...]`; assumptions are marked `[ASSUMPTION]`. Cite where every number came from: founder-provided, calculation, or a public source the founder should verify.
- Only email people who signed up, asked, or are customers. A bought or scraped list is cold outreach; route to `cold-outreach`, which covers its stricter rules.
- No fake personalization, fake "Re:" subjects, fake scarcity, fake deadlines, or countdowns that reset.
- No dark patterns around unsubscribing: no login wall, no guilt copy, no "are you sure" maze.
- Never send an email under the founder's name that the founder has not read. Drafts are drafts until they approve them.
- Use counts, not percentages, under 20 people: "3 of 9 replied", not "33%".
- Customer quotes in an email stay verbatim and need the customer's permission.

## Edge cases

- **No list yet.** Write the welcome only, so it is ready for the first signup, and route list-building to `launch` or `cold-outreach`. Do not design a sequence for people who do not exist.
- **Founder wants the full drip** ("a 12-email onboarding sequence", "a weekly newsletter"). Steelman it in one line (it runs without them). Strongest objection: at this size, a hand-sent note gets replies a sequence won't, and every automated email is one more thing to keep true as the product changes. Test: send the 3–5 emails by hand to the next 20 people, then automate only the ones whose replies stopped surprising you. The founder decides; log it.
- **Stage mismatch.** Trial-ending emails with no trial, or upgrade emails with no price: say which milestone makes them timely, write what fits today (usually a welcome and a founder call), and route pricing to `pricing-strategy`.
- **Stale waitlist.** People who signed up months ago may not remember you. The first email says who you are, how they signed up and when, what changed, and gives a one-click way out. Expect unsubscribes; a smaller list that remembers you is the better list.
- **Mixed list.** The waitlist holds both target customers and people outside the target. Do not send everyone the same thing. Target customers get the hand-sent email with the real ask; everyone else gets one honest update and a question that sorts them.
- **Context conflict.** company.md says 62 signups, the journal says 80, or the sending tool shows a different count. Use the newest dated source, flag the gap, and propose a company.md diff. Never pick silently.
- **Out of scope.** In-app checklists and empty states go to `onboarding`. Password resets and receipts are transactional; keep them plain and accurate, but they are not this skill's job. A single draft that only needs polishing goes to `human-voice`.
- **Buyer and user differ.** The user gets the activation nudge; the buyer gets the result (what their team finished) and the money conversation. Never send the buyer a nudge about a step only the user can take.

## Output format

```markdown
# Lifecycle emails — <Company> — <YYYY-MM-DD>
**Plan:** <n> emails. <group> gets <email> by <hand / tool>, triggered by <trigger>. First send: <what, to whom, when>.
**Cut:** <emails considered and dropped, with the test they failed>

## Email plan
| # | Email | Group (n) | Trigger | One job | Sent how | Timing | Exit when | Reason to exist |
|---|---|---|---|---|---|---|---|---|

## Drafts
### <n>. <email name> — to <group>
From: <founder name> <address> | Reply-to: <address that reaches the founder>
Subject options: 1) ... 2) ... 3) ...

<body, plain text>

<sign-off>
<unsubscribe line and postal address, if not a personal one-to-one note>

> Why: <trigger, one job, what you'll learn from the replies>

## Measurement
| Email | Sent | Replies | Did the action | Unsubscribes | Decision rule |
|---|---|---|---|---|---|

## Open items
- [NEED: ...] / [ASSUMPTION: ...]

## Send checklist
- [ ] Founder read every draft
- [ ] Everyone on the list opted in to hear about this
- [ ] Reply-to reaches the founder; no noreply address
- [ ] Unsubscribe and postal address on every non-personal send
- [ ] Domain authenticated (SPF, DKIM, DMARC)
```

Journal entries (append to `.foundora/journal.md`):

```markdown
### YYYY-MM-DD — decision: Lifecycle email plan
- Emails: <n, names, groups, triggers>
- Cut: <emails dropped and the test they failed>
- Sent how: <by hand / tool>, automate when <trigger>
- Revisit: <date or trigger>
- Source: lifecycle-emails
```

```markdown
### YYYY-MM-DD — experiment: <email name> to <group>
- Sent: <n> on <date>, by <hand / tool>; one job: <ask>
- Pass if: <n of N reply or act within <days>>; prior: <counts or none>
- Result: fill in as a new entry on <date>
- Source: lifecycle-emails
```

## Follow-ups

- No aha moment defined, or people stall inside the product: `onboarding`.
- The activation event needs tracking before the nudge can trigger on it: `product-analytics`.
- The list is ready to hear about the launch itself: `launch`.
- A trial or win-back email needs a real price: `pricing-strategy`.

_Adapted from emails (MIT). Rewritten in original text for early-stage founders and the shared company context. Method credit: Paul Graham, "Do Things That Don't Scale"; Gustaf Alströmer, "How to Get Users and Grow"; Kevin Hale, "How to Improve Conversion Rates"; Federal Trade Commission, "CAN-SPAM Act: A Compliance Guide for Business"._
