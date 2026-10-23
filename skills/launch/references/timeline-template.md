# Timeline template

Read this in steps 6 and 7. Replace `T` with the launch date, compute every real date, and check weekdays. Remove rows for channels you are not using. Add owners; a row without an owner does not happen.

## Choosing the date

- B2B: Tuesday to Thursday, avoiding public holidays, end of quarter, and major industry events where buyers are away (heuristic).
- B2C: depends on the channel; weekends can work for consumer apps and lower-competition Product Hunt days (heuristic).
- Avoid dates that clash with large tech events if your audience follows them.
- The founder must be available all day and the next two days.

## T-30 to T+14

| Day | Date | Workstream | Task | Owner | Done |
| --- | --- | --- | --- | --- | --- |
| T-30 | | Plan | Confirm launch type, goal, primary metric and target with shown maths | | |
| T-30 | | Plan | Run readiness gate; list blockers with fix dates | | |
| T-30 | | Channels | Score channels; pick primary and secondary | | |
| T-28 | | Product | Fix top 3 private beta issues | | |
| T-28 | | Measurement | Analytics events and UTMs set up and tested | | |
| T-25 | | Proof | Ask beta users for permission to quote; collect real numbers | | |
| T-25 | | Borrowed | Pitch newsletters, podcasts, partners (3–4 weeks lead) | | |
| T-21 | | Borrowed | Submit integration marketplace listings | | |
| T-21 | | Copy | Draft landing page copy (`landing-page-copy`) | | |
| T-21 | | Rented | Start participating in chosen communities and on PH if not already | | |
| T-18 | | Video | Script launch video and cutdowns (`video-script`) | | |
| T-14 | | Design | Landing page built (`website-design`) | | |
| T-14 | | Rented | PH listing drafted: tagline, description, gallery, maker comment | | |
| T-14 | | Video | Record screen and on-camera footage | | |
| T-14 | | Pre-launch | Teaser posts begin on primary rented channel | | |
| T-14 | | Pre-launch | Submit to pre-launch directories if relevant | | |
| T-10 | | Video | Edit launch video, hero loop, 30s vertical, GIF | | |
| T-10 | | Outreach | Build personal outreach list (20–50 names, reason for each) | | |
| T-7 | | QA | Landing page passes review checklist blockers | | |
| T-7 | | QA | Fresh-account signup, onboarding, payment test on desktop and mobile | | |
| T-7 | | Copy | Launch post, email, LinkedIn post, X thread, community posts drafted | | |
| T-7 | | Rented | Show HN title and first comment drafted (if technical) | | |
| T-5 | | Owned | Launch email built, tested on 3 clients, scheduled or ready | | |
| T-5 | | Support | FAQ and support macros written; support owner confirmed | | |
| T-3 | | Rented | PH launch scheduled; re-read PH and HN guidelines | | |
| T-3 | | Outreach | Give heads-up to supporters (feedback ask, not upvote ask) | | |
| T-2 | | Infra | Load check; error alerts on; status page or fallback ready | | |
| T-1 | | Final | Freeze deploys; final link check of every UTM; run of show confirmed | | |
| T-1 | | Final | Sleep. Launch day is long | | |
| T | | Launch | Run of show (below) | | |
| T+1 | | Follow-up | Reply to every comment, email, DM still open | | |
| T+1 | | Metrics | Day-1 numbers vs target; run bad-numbers playbook if needed | | |
| T+2 | | Owned | Follow-up email to non-clickers with a new angle | | |
| T+3 | | Users | Contact 10 new signups (call or email) about onboarding | | |
| T+3 | | Rented | Second post on primary channel: learnings, demo, or first results | | |
| T+5 | | Proof | Ask happy new users for permissioned quotes or reviews | | |
| T+7 | | Metrics | Week-1 review: funnel by source, activation, qualitative themes | | |
| T+7 | | Next | Pick next channel or mini-launch from the scoring sheet | | |
| T+10 | | Borrowed | Newsletter or podcast placements go out; share them | | |
| T+14 | | Retro | Write retro: what worked, what did not, numbers vs target; log to journal | | |
| T+14 | | Next | Plan the next 30 days (next launch moment) | | |

If launch is fewer than 30 days away: keep every row from T-7 onward, then fit earlier rows into the time left, dropping the lowest-scoring channels' rows first. State what was cut.

## Launch-day run of show

Example for a launch using Product Hunt (PT) with a founder in another time zone. Fill both columns with real times. If not using PH, start at the founder's 08:00 and keep the same sequence.

| Time (local) | Time (PT) | Action | Channel | Owner |
| --- | --- | --- | --- | --- |
| | 00:01 | Listing goes live; post maker comment immediately | Product Hunt | |
| | 00:10 | Publish launch post on own site; verify all links and UTMs | Website | |
| | 00:20 | Message the first ring of supporters: "We launched, I would value your feedback" | DMs | |
| | 05:00–06:00 | Send launch email to beta users and waitlist | Email | |
| | 06:00 | LinkedIn post from founder profile (B2B primary) | LinkedIn | |
| | 06:30 | X thread with native video; pin it | X | |
| | 07:00 | Show HN post (if technical), then stay on it 4–6 hours | Hacker News | |
| | 07:30 | Community posts per each community's rules | Communities | |
| | 08:00–12:00 | Reply to every comment within 30 minutes; log bugs and feature requests | All | |
| | 09:00 | Personal outreach to 20–50 names on the list | Email / DMs | |
| | 10:00 | First numbers check: visits by source, signups, errors | Analytics | |
| | 12:00 | Midday update post with something new (a GIF, a question answered, a fix shipped) | Primary rented | |
| | 14:00 | Second numbers check; adjust: double down on the source that converts | Analytics | |
| | 15:00 | Short-form video post | TikTok / Reels / Shorts | |
| | 17:00 | Reply sweep across all channels; thank people specifically | All | |
| | 20:00 | Final numbers of the day; note top questions and objections | Analytics | |
| | 21:00 | Write tomorrow's follow-ups; log the day in `.foundora/journal.md` | Journal | |

Rules for the day:
- One person owns replies at all times; one person owns bugs. In a solo team, alternate in blocks and say so.
- Ship small fixes live if safe; mention them in replies ("Fixed, thanks").
- Do not post the same message in every channel at once. Stagger and tailor.
- No upvote asks on PH, HN, or Reddit.

## Metrics table

| Metric | Baseline (pre-launch) | Target | Source | Check |
| --- | --- | --- | --- | --- |
| Visits by source | | | Analytics + UTMs | 10:00, 14:00, 20:00 on T; daily after |
| Visit-to-signup rate | | | Analytics | Daily |
| Signup-to-activation rate | | | Product events | Daily |
| Primary metric | | | | Daily |
| Replies / qualitative themes | | | Inbox, comments | Daily |
| Errors and support tickets | | | Error tracking, support inbox | Hourly on T |

## Retro template (T+14)

```markdown
## Launch retro: <name>, <date>
- Goal and target: ... | Result: ... (source)
- Best channel by primary metric: ... | Worst: ...
- What worked: ...
- What did not: ...
- Biggest surprise from users: ...
- Top 3 objections heard: ...
- Decision: <next channel / next mini-launch / fix before more traffic>
```
