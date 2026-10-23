# MVP test types

Read after the decision tree picks a type. Costs are in founder-days of effort and are rough planning ranges, not promises; adjust to the founder's skills. Examples are hypothetical and illustrate the shape of a test, not real companies' results.

Signal strength scale:
- **Strong:** customers spend money or sustained effort; behaviour, not stated intent.
- **Medium:** customers take a real action with low cost to them (click, sign up with real data, book a call).
- **Weak:** attention only (views, likes, waitlist without follow-through).

## Concierge

The founder delivers the outcome personally and openly. The customer knows a human is doing the work.

- **When:** testing whether the outcome is valuable enough to pay for, before knowing what to automate. Best for services, B2B workflows, and anything where the "right" output is unclear.
- **Cost:** 1–2 days to set up (intake form, payment link, a delivery checklist); then ongoing founder hours per customer.
- **Signal:** Strong if customers pay and come back; Medium if free.
- **Example:** A meal-planning idea run as a weekly plan written by the founder for 10 paying households over email.
- **Measure:** paid conversion from offer, repeat rate in week 2–4, time per delivery (sets the automation priority).
- **Pitfalls:** charging nothing (removes the strongest signal); over-serving so the result can't be repeated by software; stopping before the repeat-usage window; not logging the steps, which is the spec for what to automate.

## Wizard of Oz

The customer sees a product interface; behind it, a human does the work.

- **When:** the value depends on the experience feeling like software (speed, self-serve, an app flow) and you need to test it before building the hard part (matching, recommendations, AI output).
- **Cost:** 2–5 days for a thin front end (form builder, no-code app, simple web page) plus founder time per request.
- **Signal:** Strong if usage repeats and people pay; Medium otherwise.
- **Example:** A "find me a contractor" app where the founder does the matching by phone within an hour of each request.
- **Measure:** requests per user per week, completion time, repeat use, willingness to pay at the end.
- **Pitfalls:** response time you can't sustain sets false expectations; volume spikes overwhelm the founder; ethics. Disclosure rule: do not misrepresent how personal data is handled. If people share sensitive data, tell them a team member reviews requests. Never claim automation in a way that affects a purchasing or safety decision.

## Fake door

A real-looking entry point (button, menu item, pricing tier, plan) for something that does not exist yet.

- **When:** you already have traffic or users from the target segment and want to measure demand for a specific feature or offer.
- **Cost:** under 1 day.
- **Signal:** Medium (a click is cheap for the user). Stronger if the door requires a cost: entering card details, booking a call, choosing a paid tier.
- **Example:** A "Team plan" option on an existing pricing page that leads to "Team plan is coming. Want early access at the launch price?"
- **Measure:** click-through from the exposed population (define the denominator as people who saw the door), then the follow-up action rate.
- **Pitfalls:** no denominator, so clicks mean nothing; leaving it up for weeks erodes trust; reading curiosity as demand. Disclosure rule: tell the user immediately after the click that it is not available yet, and never charge.

## Single-feature product

Build only the one interaction that delivers the core value, done well, with nothing around it.

- **When:** the value hinges on one interaction that a human can't fake at speed (real-time tools, editors, calculators, integrations), and demand has some evidence already.
- **Cost:** 5–10 days.
- **Signal:** Strong if users return unprompted; Medium for first-use only.
- **Example:** A tool that does one thing: turns a bank CSV into a categorised tax summary. No accounts; email the result.
- **Measure:** completion of the core action, return within 7 days, unprompted referrals.
- **Pitfalls:** scope creep through "just one more" supporting feature; building auth and settings before the core works; picking the feature the founder finds interesting rather than the one the assumption needs.

## Landing page with preorder

A page that describes the offer and asks for money (or a refundable deposit) before the product exists.

- **When:** testing demand and willingness to pay, and you can drive at least 100 visitors from the target segment in two weeks.
- **Cost:** 1–3 days for page, payment link, and traffic setup; plus any ad spend.
- **Signal:** Strong for paid preorders; Weak for email-only waitlists.
- **Example:** A page for a bookkeeping service for dental practices with a refundable deposit for the first month.
- **Measure:** visitor-to-preorder rate by traffic source. Track sources separately; mixed traffic hides the answer.
- **Pitfalls:** testing copy rather than demand (one page is one copy test); traffic from outside the segment (friends, general social posts); counting waitlist emails as demand. Rules: preorders state the delivery date and that they are refundable; refund promptly if the test fails.

## Spreadsheet backend

The product's front is real (form, email, simple page); the back end is a spreadsheet or no-code database operated by hand.

- **When:** value depends on data, matching, scheduling, or operations, and you need to learn the real workflow before designing a schema.
- **Cost:** 1–3 days.
- **Signal:** Strong when customers depend on it weekly; it shows real operational volume.
- **Example:** A shift-swap service for clinics run through a form, a shared sheet, and SMS sent by the founder.
- **Measure:** weekly active customers, volume per customer, founder hours per unit (the break point for automation).
- **Pitfalls:** data privacy (keep personal data in a tool with access controls, not a public sheet; check obligations for health, finance, or minors' data); manual errors that look like product failure; failing to set the volume at which you will automate.

## Direct presale (when there is no traffic)

The founder offers the product one-to-one to named prospects and asks for a commitment.

- **When:** B2B or high-price offers where 20+ prospects can be reached directly; no audience for a landing page.
- **Cost:** 2–5 days of outreach and calls.
- **Signal:** Strong (signed LOI with price, deposit, paid pilot).
- **Measure:** asks made, commitments by currency (time: follow-up meeting or trial with real data; reputation: intro to the buyer; money: LOI with price, deposit, paid pilot), objections recorded verbatim.
- **Pitfalls:** asking friends; accepting "send me more info" as progress; discounting to zero to get a yes.

## Timeboxed technical spike

A throwaway build that answers one feasibility question.

- **When:** the riskiest assumption is that something can be built at all, at the required quality, cost, or speed.
- **Cost:** maximum 5 days, fixed in advance.
- **Signal:** answers feasibility only; says nothing about demand.
- **Measure:** a pass/fail criterion written before the spike ("processes a 50-page PDF in under 30 seconds with fewer than 2 extraction errors").
- **Pitfalls:** the spike becomes the product; extending the timebox instead of recording "not feasible in 5 days"; running a spike when demand is the bigger unknown.

## Choosing between two valid types

| If | Prefer |
|---|---|
| Both test the assumption equally | The one with lower founder-days |
| One gets money, the other gets clicks | The one that gets money |
| One needs traffic you don't have | The one that uses direct outreach |
| One produces a reusable workflow log | That one (it becomes the spec) |
