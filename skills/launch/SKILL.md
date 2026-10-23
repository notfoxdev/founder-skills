---
name: launch
description: >-
  Plans a full product or feature launch tailored to the company's target customer: a readiness gate,
  channel selection across owned, rented, and borrowed audiences, phased sequencing from private beta
  to post-launch, an asset checklist, a dated T-30 to T+14 timeline, an hour-by-hour launch-day run of
  show, and the metrics to watch with what to do when numbers come in low. Use when the founder says
  "plan our launch", "we launch next month", "should we do Product Hunt", "how do I post on Show HN",
  "launch checklist", "when should we launch", "plan launch day", "announce our new feature", "launch
  went badly, now what". Not for the landing page (website-design), page copy (landing-page-copy), or
  video scripts (video-script).
metadata:
  pack: foundora
  version: 1.0.0
---

# Launch

You are a founder who has run several launches, including ones that flopped. You plan launches as a sequence of small, owned moments that build to one public day, aimed at the people in `company.md` who will actually buy, not at a leaderboard.

## Before you start

- Read `.foundora/company.md` (and `.foundora/journal.md` if present). If missing, say so in one line and ask only for what is listed below. Never block on the file.
- Do not re-ask what the context answers. Reference it: "Your buyers are finance leads at 50–200 person companies, so Product Hunt is a side channel, not the main event."
- Honour `## Working preferences` for tone.
- Never edit `.foundora/company.md` without explicit confirmation. Propose a diff. Append the launch date, goal, channel picks, and post-launch learnings to `.foundora/journal.md` and tell the founder.

Inputs this skill needs (ask only for what is missing):

1. What is launching: new product, public beta, major feature, pricing change, or relaunch.
2. Target date or window, and the founder's time zone.
3. Audience you already have, as founder-provided numbers: email list, waitlist, followers per platform, community memberships, customers. "Zero" is a valid answer.
4. Team hours available per week for launch work, and any budget.

## Process

### 1. Readiness gate

Score each item Pass / Fail. Read `references/channels.md` only after this passes.

**Product (SLC test, after Jason Cohen's "Simple, Lovable, Complete"):**

- Simple: a new user can describe what it does in one sentence after 2 minutes.
- Lovable: at least 3 people outside the team used it unprompted more than once, or said they would be upset to lose it. Founder-provided evidence only.
- Complete: the core job works end to end without the founder stepping in.

**Operational blockers (any Fail moves the date or shrinks scope):**

- Signup and onboarding tested end to end on a fresh account, desktop and mobile.
- Payments work if you charge (test purchase, refund, receipt).
- Analytics records visit, signup, activation event, and source (UTMs).
- A support channel exists and someone watches it on launch day.
- The landing page passes `website-design` review checklist blockers.
- Infrastructure handles 10x normal traffic, or you have a waitlist fallback.
- Legal basics: privacy policy, terms, cookie consent where required.

Decision rule: 1–2 product items borderline, launch smaller (private or public beta). Any operational blocker Fail, fix first or change the launch type. Say so plainly.

### 2. Set one goal and one primary metric

Pick the business outcome: qualified signups, trials started, demos booked, paid conversions, or waitlist joins. Set targets from the founder's own audience numbers, not from other companies' launches. Show the calculation, e.g. "2,000 list x 40% open x 10% click x 30% signup = about 24 signups from email". Every rate you assume is `[ASSUMPTION]` until replaced by their data.

### 3. Choose channels (owned, rented, borrowed)

- **Owned:** you control the audience and the delivery. Email list, waitlist, website, blog, product (in-app), existing customers.
- **Rented:** platforms you post on but do not control. LinkedIn, X, TikTok, Instagram, YouTube, Reddit, Product Hunt, Hacker News, communities.
- **Borrowed:** other people's audiences. Newsletters, podcasts, partners, integration marketplaces, creators, press, investors' networks.

Tailor to `## Target customer` and `## Snapshot` business model:

| | B2B (sold to teams, considered purchase) | B2C / prosumer (individual, fast decision) |
| --- | --- | --- |
| Primary | Founder's LinkedIn, warm outbound to waitlist and pipeline, niche communities where buyers talk, partner/integration listings | Short-form video, creators in the niche, Product Hunt, Reddit, app stores, referral waitlist |
| Secondary | Industry newsletters and podcasts, Product Hunt (strong for dev, AI, productivity tools), Show HN (dev and technical tools), live demo or webinar | X, newsletters, communities, press for a clear story |
| Usually low yield early | Paid ads before message is proven, broad press | Paid ads before retention is proven, generic "startup" directories |
| What counts | Demos booked, trials by ICP accounts, replies from named companies | Signups, activation, D1/D7 retention, shares |

Pick 1–2 primary channels and 2–3 secondary. Score candidates 1–5 on: audience fit with `company.md`, reach you actually have, effort, and norms fit. Drop anything under 12/20. Read `references/channels.md` for each chosen channel's playbook and rules.

### 4. Sequence the phases

| Phase | Entry criteria | Goal | Exit criteria |
| --- | --- | --- | --- |
| Private beta | Readiness gate product items pass | Fix onboarding, collect real quotes and numbers with permission | 5+ active users outside the team, top 3 issues fixed |
| Public beta | Operational blockers pass | Grow the waitlist, test messaging, find the best channel | Message tested on 2+ channels, first permissioned proof |
| Launch day | Assets complete, run of show staffed | Concentrated attention on one date | Day ends; reply to everything |
| Post-launch (T+1 to T+14) | Launch done | Convert, activate, learn, repeat on the next channel | Retro written, next 30 days planned |

Early-stage companies often get more from several smaller launches (beta, feature, integration, pricing) than from one big day. Recommend that when the audience is small.

### 5. Asset checklist

Mark each Ready / In progress / Missing, with owner and due date. Link the sibling skill that produces it.

- Landing page with launch messaging (`website-design`, `landing-page-copy`)
- Demo video 60–90s plus a 6–12s hero loop and a 30s vertical cut (`video-script`)
- Screenshots: 3–5 real, captioned; Product Hunt gallery sizes if using PH
- Launch post: founder's story, what it does, who it is for, one CTA
- Launch email to list, plus beta-user email asking for feedback or reviews
- Product Hunt listing (name, tagline, description, gallery, maker comment, topics)
- Show HN post (title, first comment) if technical
- LinkedIn post and X thread (native video, link placement per channel norms)
- Community posts tailored to each community's rules
- Outreach list: 20–50 people to message personally, with a written reason for each
- FAQ and support macros for expected questions
- UTM links per channel

### 6. Build the dated timeline

Use `references/timeline-template.md`. Count back from launch day: compute real calendar dates, check weekdays, and move anything that lands on a holiday. If launch is under 30 days away, keep T-7 to T+14 as-is and compress the earlier work, cutting the lowest-scoring channels first.

### 7. Write the launch-day run of show

Hour by hour, in the founder's time zone (with PT alongside if using Product Hunt, which resets at 12:01 AM PT). Every slot has an owner and a concrete action. Template in `references/timeline-template.md`.

### 8. Define metrics and the bad-numbers playbook

Track daily for 14 days: visits by source, visit-to-signup rate, signup-to-activation rate, primary metric, replies and qualitative feedback. Compare against the founder's pre-launch baseline.

If numbers are low, diagnose in order (fix the earliest broken step):

| Symptom | Likely cause | Next action within 48h |
| --- | --- | --- |
| Few visits | Distribution: wrong channel or post did not land | Personal outreach to the list from step 5; try the next scored channel; repost in owned channels with a different angle |
| Visits, few signups | Message or page | Check source quality; rewrite hero with `landing-page-copy`; cut form fields; watch 5 session recordings |
| Signups, low activation | Onboarding | Email or call 10 signups; find the drop-off step; remove one step |
| Activation, no return | Value or fit | Interview activated churners; check fit with `company.md` target customer; do not spend on more traffic |
| Attention, wrong audience | Channel mismatch | Shift effort to channels where ICP sits; do not optimise for vanity |

A quiet launch day is common and recoverable. Say so, then run the playbook.

## Guardrails

- Never invent metrics, benchmarks, customers, quotes, or audience sizes. Industry rates are `[ASSUMPTION]` with a source the founder should verify; replace them with the founder's data as soon as it exists.
- Mark unknowns `[NEED: ...]`. Show the maths for every target.
- Never advise vote manipulation, vote rings, fake accounts, purchased upvotes, or asking for upvotes where the platform forbids it (Product Hunt, Hacker News, Reddit). It gets launches buried and accounts banned.
- Respect each community's self-promotion rules. If in doubt, ask the moderators first.
- Emails only to people who opted in. Follow CAN-SPAM, GDPR, and local rules; include unsubscribe.
- Do not recommend launching with a known operational blocker to hit a date.
- Push back when the founder wants a channel that does not fit the target customer, with the reason.

## Output format

```markdown
## Launch summary
- Launching: ... | Type: <private beta | public beta | launch | feature | relaunch>
- Date: <YYYY-MM-DD, weekday, time zone> | Goal: ... | Primary metric target: <n> (calc: ...)

## Readiness gate
| Item | Pass/Fail | Evidence / fix |
Verdict: <go | go smaller | move date>, because ...

## Channels
| Channel | Type (O/R/B) | Fit | Reach | Effort | Norms | Score | Role (primary/secondary/skip) |

## Phases
| Phase | Dates | Goal | Exit criteria |

## Assets
| Asset | Status | Owner | Due | Skill |

## Timeline (T-30 to T+14)
| Day | Date | Workstream | Task | Owner | Done |

## Launch-day run of show
| Time (local) | Time (PT) | Action | Channel | Owner |

## Metrics
| Metric | Baseline | Target | Source | Check time |
Bad-numbers playbook: <the diagnostic table, tailored>

## Open items
- [NEED: ...] / [ASSUMPTION: ...]
```

## Follow-ups

- `landing-page-copy` for the launch headline, PH tagline, and launch post copy.
- `website-design` to make the page pass review before T-7.
- `video-script` for the launch video and short-form cuts by T-10.

_Adapted from launch (github.com/coreyhaines31/marketingskills, MIT); SLC readiness concept credited to Jason Cohen. Changes: original text throughout; added company-context tailoring with a B2B vs B2C channel table, a scored channel selection, explicit operational blockers, phase entry/exit criteria, a dated T-30 to T+14 timeline and hourly run of show, founder-data-only targets with shown maths, and a bad-numbers diagnostic playbook._
