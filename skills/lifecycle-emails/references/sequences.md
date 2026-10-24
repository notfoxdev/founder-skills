# Sequence blueprints

Five small sequences that cover almost everything a company with a waitlist or its first 20 customers needs to send. Pick the one that matches the stage, take 1–3 of its emails, and write them in the founder's words. The skeletons use `<placeholders>`; nothing in them is real company data. Timings are house defaults the founder can move, not benchmarks.

Every blueprint follows the same rules: one job per email, the job in the first two lines, plain text from a person, a reply-to that reaches the founder, and an exit the moment someone replies or acts.

## 1. Waitlist to launch

**When:** people signed up on a page before the product was ready. They agreed to hear about this product, nothing more.

| Email | Trigger | One job | Timing | Exit when |
|---|---|---|---|---|
| Welcome | Joined the waitlist | Get a one-line reply that sorts them (who they are, how they do the job today) | Same day | They reply |
| Hand-picked invite | Fits the target customer and the founder can take them on | Book a call or a setup slot | When there is room, by hand | Booked, or declined |
| Honest update | 4–8 weeks since the last email, with real news | Re-confirm interest, sort with one question | Only when something changed | Reply or unsubscribe |
| Launch note | The thing they signed up for is open to them | Start using it (one link) | Launch day | They sign up |

Skeleton, welcome:

```
Subject: you're on the <product> list

Hi <first name>,

I'm <founder>, and I'm building <product> for <who, in the page's words>. Thanks for signing up.

We're letting people in a few at a time, starting <[NEED: month]>. Before then, one question: how do you <do the job> today?

A one-line reply is plenty. I read every one.

<founder first name>
```

Traps:
- Treating the whole list the same. Split target customers from everyone else first.
- Sending an "update" with no news. If nothing changed, don't send.
- A waitlist that is months old: say who you are and how they signed up in the first line, and make leaving easy.

## 2. Signup to activation

**When:** people can sign up and use the product, and some stop before the aha moment. Coordinate with `onboarding`: email covers the gap between sessions, it doesn't repeat the screens.

| Email | Trigger | One job | Timing | Exit when |
|---|---|---|---|---|
| Welcome | Account created | Reply with what they want to get done, or take the first step | Within minutes (automated) or same day (by hand) | Reply or first step done |
| Activation nudge | No aha moment within the window | Finish the one missing step, or book 15 minutes to do it together | End of the window | Aha reached |
| Founder check-in | Reached the aha moment | One question about what nearly stopped them | 1–3 days after | Reply |

Skeleton, activation nudge:

```
Subject: your <thing> is half set up

Hi <first name>,

You added <what they did> on <day> but haven't <the missing step> yet. That's the part where <what they get, in their words>.

If it's fiddly, I can do it with you in 15 minutes: <one booking link>. Or reply with <what you need from them> and I'll set it up for you.

<founder first name>
```

Traps:
- Nudging on a calendar ("day 3 tips") instead of on what they did.
- Listing five features. Name the one step.
- Offering a call and then not being free. Only offer what the founder will do this week.

## 3. Trial ending

**When:** a free trial or a free pilot has an end date and a price after it.

| Email | Trigger | One job | Timing | Exit when |
|---|---|---|---|---|
| Heads-up | Trial ends in about 3 days | Decide: continue, ask a question, or let it lapse | 3 days before | Paid, replied, or declined |
| Last day | Trial ends today, and they used it | Continue with one click | Morning of the last day | Paid or declined |
| After it ends | Lapsed without paying | Tell the founder why (one line) | 2–3 days after | Reply |

What the heads-up must say, in plain numbers: the end date, what happens at the end (paused, deleted, charged), the price and billing period, and how to keep going. Missing price: `[NEED: price, from pricing-strategy]`. If they barely used it, skip the last-day email and send the founder's "what got in the way?" note instead.

Traps:
- A surprise charge. Say it before it happens.
- Urgency that isn't real ("only today"). The real deadline is enough.

## 4. Gone quiet, and win-back

**When:** an active user stopped (gone quiet), or a customer cancelled or lapsed (win-back).

| Email | Trigger | One job | Timing | Exit when |
|---|---|---|---|---|
| Gone quiet | No activity for about twice their normal cycle | Find out what changed (one-line reply) | Once | Reply or return |
| Win-back | About 30 days after cancelling or lapsing, and something real changed for them | Try the change, or tell the founder why they left | Once | Reply, return, or no reply: stop |

Skeleton, gone quiet:

```
Subject: did <product> stop being useful?

Hi <first name>,

You were in <product> most <weeks / months> until <date>, then nothing. No problem if it's not useful any more, but I'd like to know what changed. Was it <the most likely reason>, or something else?

<founder first name>
```

Rules for win-back: ask why before offering anything. Mention a change only if it shipped and it touches their reason for leaving. One email, two at most, then mark them as lost and stop. No invented discount, no "we miss you".

## 5. After a pilot

**When:** a pilot or design-partner period ends. This is the email that turns a free pilot into a paying customer or a clear no.

| Email | Trigger | One job | Timing | Exit when |
|---|---|---|---|---|
| Wrap-up and ask | Pilot ends in about 5 working days | Book the decision call | Before the end, not after | Booked |
| Result summary | After the decision call | Confirm what they agreed and the next step in writing | Same day | Confirmed |
| No-decision follow-up | No reply to the wrap-up after about 5 working days | Get a yes or a no | Once | Any answer |

The wrap-up states what happened in the pilot in their numbers (only numbers the founder has measured), the price after the pilot, and asks for a 20-minute call to decide. A polite "maybe later" is a no for planning purposes; log it as one. Price comes from `pricing-strategy`; results come from the founder's pilot notes, never from estimates.

## Sending and compliance basics

General information to orient the founder, not legal advice. Rules change; the founder should check the current versions for the countries their recipients are in.

- **Consent scope.** A waitlist signup agreed to hear about this product. Don't add them to an unrelated newsletter, sell or share the list, or email them about a different company.
- **United States (CAN-SPAM, commercial email).** Accurate From and routing information; a subject line that doesn't mislead; a valid postal address; a clear way to opt out that keeps working for at least 30 days after sending; opt-outs honored within 10 business days, without asking for more than an email address. Purely transactional messages (receipts, password resets) are treated differently, but a sales pitch inside a receipt can change that.
- **Mailbox-provider sender rules.** Since 2024, Google and Yahoo have required authentication (SPF or DKIM) from all senders, and bulk senders also need SPF, DKIM and DMARC, one-click unsubscribe on marketing mail, and a low spam-complaint rate (Google cites 0.3% as a ceiling). A founder sending a few hundred emails is well under the bulk threshold, but set up all three records anyway.
- **EU, UK, Canada.** Consent rules for marketing email are stricter (GDPR with ePrivacy rules, PECR in the UK, CASL in Canada). A waitlist with a clear signup purpose is usually the strongest position; keep a record of where and when each person signed up. When in doubt: `[NEED: check with counsel for <country>]`. `cold-outreach` covers the country rules in more depth.
- **Unsubscribe.** One click or one reply. Honor it at once, across every tool that sends. Keep a suppression list.
- **Personal one-to-one notes** typed from the founder's inbox can carry a simple line ("If you'd rather I didn't email, just say so") instead of a footer; anything sent in bulk gets the full footer.

## Small-number scoreboard

Track per email, in counts: sent, replies, did the action, unsubscribes. Ignore opens. Read every reply and tag it with one word (interested, confused, not a fit, wrong person). With fewer than 20 sends, the tags matter more than any rate.
