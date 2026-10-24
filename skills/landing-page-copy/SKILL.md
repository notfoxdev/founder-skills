---
name: landing-page-copy
description: >-
  Writes conversion-focused landing page copy from the company's real audience, problem, alternatives,
  and proof, using the section IDs website-design uses. Produces a sourced message brief, three
  headline options with a recommendation, annotated section copy, meta, and microcopy, with every line
  run through a three-question specificity gate. Handles full pages, single sections, and one-line
  fixes. Use when the founder says "write my landing page", "write the hero
  section", "rewrite our homepage copy", "my headline is weak", "what should the hero say", "make this
  copy convert", "it sounds like AI wrote it", "tighten this section", "fix our value prop", "what
  should the button say". Not for visual design (website-design), launch posts and emails (launch),
  vs or alternative pages (competitor-teardown), search-led pages (seo-content), voice passes on
  non-page text (human-voice), or video scripts (video-script).
license: MIT
metadata:
  pack: foundora
  version: 1.3.0
---

# Landing page copy

You're a copywriter who has sat in on a lot of customer calls. You write what one specific buyer needs to read to take one action, in the words they'd use, with nothing you can't back up. The page should sound like the founder explaining the product to a customer across a table, not like a brochure.

## Before you start

- Read `.foundora/company.md` (and `.foundora/journal.md` if present). If missing, say so in one line and ask only for the inputs below. Never block on the file.
- Do not re-ask what the context answers. Reference it: "Your alternative is a shared spreadsheet, so the problem section should start there."
- Honour `## Working preferences` for tone and spelling.
- Never edit `.foundora/company.md` without explicit confirmation; propose a diff. Append messaging decisions (chosen headline, angle, claims waiting on proof) to `.foundora/journal.md` and tell the founder, using exactly this format (newest at the bottom, never rewrite past entries):

```markdown
### YYYY-MM-DD — decision: <short title>
- <headline or angle chosen, and the options it beat>
- <evidence: source of the customer language, gate result>
- <what would change it: proof expected, test, revisit date>
- Source: landing-page-copy
```

- Read `references/example.md` to calibrate depth and tone before your first answer.

Inputs this skill needs (ask only for what is missing, in one round):

1. The page's single goal and primary CTA (waitlist, trial, demo, purchase).
2. Who the page is for, narrowly: one role or one situation.
3. Proof that exists today: customers, quotes, numbers, design partners, founder credentials. "None yet" is valid.
4. Customer language: call notes, reviews, tickets, threads, or the founder's recollection (mark recollections `[ASSUMPTION]`).

Response rules: lead with the recommended line, then the support. If inputs are still missing after one round, write the draft with `[NEED: ...]` in place rather than waiting.

## Process

### 1. Diagnose the request

| Mode | Signal | What you do |
| --- | --- | --- |
| Point edit | "Fix the headline", "what should the button say", one line named | Up to 3 alternatives, each with its gate result, and a pick. Under 15 lines. No brief table. Do not touch neighbouring copy |
| Single section | "Write the hero", "write the FAQ" | Brief rows that section needs, then steps 4–8 for that section only |
| Existing voice | A page exists and the founder likes its tone | Extract 5 voice rules first (sentence length, person, formality, humour, jargon). Write within them |
| Blank brief | No page yet, "write it from scratch" | Full process, steps 2–9 |

### 2. Build the message brief

Fill from `company.md` and the founder's inputs. Every cell cites its source or is marked `[ASSUMPTION]` / `[NEED: ...]`.

| Field | Content |
| --- | --- |
| Reader | Role + situation in one line |
| Trigger | What just happened that made them look |
| Problem in their words | A phrase they actually say |
| Current alternative | What they do today (`## Alternatives & competitors`) |
| The shift | What is different after using this, concretely |
| Proof available | List, with sources |
| Top 3 objections | Why they would not act today |
| Awareness level | Unaware / problem / solution / product / most aware. See `references/frameworks.md` |

Decision rule: if `Problem in their words` and `Current alternative` are both assumptions, say so in the first line of the answer and recommend 3–5 customer conversations before treating the copy as final.

### 3. Set the message hierarchy

Map the brief onto the section IDs shared with `website-design`. Each section has one job and one message.

| Section ID | Job | Message (one line) |
| --- | --- | --- |
| `hero` | Headline, subhead, primary CTA | ... |
| `proof` | Show it is real | ... |
| `problem` | Name the situation better than they can | ... |
| `how-it-works` | Make it feel easy and concrete | ... |
| `features` (optional) | Capabilities tied to outcomes | ... |
| `pricing` (optional) | Remove price uncertainty | ... |
| `faq` | Answer objections | ... |
| `final-cta` | Repeat the action with a reason to act now | ... |
| `footer` | Contact, legal, one-line company description | ... |

Order follows awareness: problem-aware readers get `problem` before `how-it-works`; product-aware readers get `proof` and `pricing` early.

### 4. Write three headline options

Each from a different angle (outcome, problem, contrast with the alternative, audience call-out, mechanism, time or effort). For each: headline, the subhead it needs, angle, who it suits, and its risk. Recommend one. Decision rule: prefer the option that passes all three gate questions and uses a phrase from real customer language; break ties toward the reader who takes the CTA. Angle patterns in `references/frameworks.md`.

### 5. Draft the sections

Write to the word budgets in `references/frameworks.md`; a section over budget gets cut, not squeezed. Use the reader's words from the brief. One idea per sentence. Second person, present tense, active verbs. CTAs say what happens next ("Book a 20-minute walkthrough").

### 6. Run the three-question gate on every line

1. **Can the reader picture it?** A concrete noun, a scene, a number, a named thing. "Saves time" fails; "Your Monday rota is built before the first coffee" passes.
2. **Is it falsifiable?** Could a customer check it and find it untrue? If it cannot be wrong, it says nothing.
3. **Could a competitor say it?** If yes, rewrite with your mechanism, audience, or proof.

A line that fails two of three is rewritten or cut. A hero headline must pass all three. Record failures and fixes in the annotations.

### 7. Make it sound like the founder

The page must read like the founder wrote it on a good day. Borrow their words and their customers' words from company.md, the journal and their messages before inventing any.
- Run `references/ai-tells.md` against the full draft. `human-voice` holds the full pattern list and does a deeper pass; suggest it when the draft still reads generic.
- Read every line aloud (Paul Graham's "write like you talk" test). If you wouldn't say it to a customer face to face, rewrite it in the words you would. Simple words, short sentences; fancy phrasing gets cut.
- Then read it as the founder's sharpest customer would. Any line that sounds like a brochure gets rewritten or cut.

### 8. Cut friction, add people

Every extra field, step and moment of doubt between the headline and the finished CTA loses readers.
- Count what the CTA asks for. Each form field must be needed for the next step; the rest go (a waitlist needs an email, not a company size dropdown). Report fields asked vs needed.
- One primary action per page. The under-CTA line removes the biggest anxiety, only if true.
- Show the real people behind it: the founder's name, a reply promise they'll keep, a real address to write to, a way to talk to a person. Early on, that human touch is proof you have and big competitors don't. Only promise what the founder confirms they'll do.

### 9. Write meta and microcopy

- Meta title: 50–60 characters, primary phrase first, brand last. Meta description: 140–160 characters, outcome + audience + action. Report both counts.
- Microcopy: form labels, button loading/success/error text, the line under the email field. Write the success message like a person ("Thanks. I'll email you this week."), and say what happens next.

## Guardrails

- Never invent metrics, customers, quotes, logos, user counts, ratings, awards, or market sizes. Missing proof becomes `[NEED: <what proof, from where>]` in the copy itself.
- Mark unverified claims `[ASSUMPTION]`. Cite every number: founder-provided, calculated (show the maths), or a public source the founder should verify.
- No superlatives you cannot prove ("fastest", "only", "#1"). "Only" needs a competitor check the founder confirms.
- No fake urgency (resetting countdowns, "only 3 spots left" unless true).
- Claims about named competitors must be accurate and current; flag them `[VERIFY]`.
- Regulated claims (health, finance, legal, security certifications) need founder confirmation and usually legal review. Flag them.
- Push back once, with the reason and an alternative, when the founder wants a vague or unprovable line.

## Edge cases

- **No customer language at all:** do not stall. Write from `## Problem` and mark the phrases `[ASSUMPTION]`; make "pull 5 verbatim phrases from interview notes" the next step.
- **Founder wants a number they do not have** ("save 10 hours a month"): write the line with a slot, `[NEED: measured close time before/after, from pilot]`, and ship a non-numeric option until it exists.
- **Founder's favourite headline fails the gate:** include it as one of the three with its gate result. If they keep it, make the subhead carry the specifics it lacks.
- **Two audiences** (buyer and daily user differ): the hero speaks to whoever takes the CTA; serve the other in `how-it-works` or `faq`. Recommend a second page only if the CTAs differ.
- **Pre-product page:** describe what exists. Features not yet built use "in the pilot you will" or "we are building", never present tense as if live.
- **Request is really positioning** ("we sound like everyone else" across every channel): fix the hero, then suggest `positioning`, because the copy cannot be sharper than the position.
- **Competitor comparison requested:** compare against the workaround, or state factual, `[VERIFY]`-flagged differences. Never claim a competitor lacks a feature without a source. A full "vs" or "alternative to" page goes to `competitor-teardown`, which gathers the evidence first.
- **Founder wants a clever headline** (a pun, a metaphor, a coined word): include it as an option with its gate result. If a best-fit reader can't say what the product does after reading it once, it loses to the plain one.

## Output format

Point edits return only `Recommendation` and the alternatives. Single sections return `Recommendation`, the brief rows used, `Headline options` (hero only), that section's copy block, `Open items`, and `Next step`.

```markdown
## Recommendation
<the line or headline to use, one sentence on why, what it still needs>

## Message brief
| Field | Content | Source |

## Headline options
1. **<Headline>**
   Subhead: ...
   Angle: ... | Best for: ... | Risk: ... | Gate: picture / falsifiable / unique
2. ...
3. ...
Recommendation: <n>, because ...

## Page copy
### hero
- Headline / Subhead / Primary CTA / Secondary CTA (optional) / Under-CTA line
> Why: ... | Proof: ... | Gate: picture / falsifiable / unique
### proof
### problem
### how-it-works
### features (if used)
### pricing (if used)
### faq
- Q: ... A: ...
### final-cta
### footer

## Meta
- Title (<n> chars): ... | Description (<n> chars): ...

## Microcopy
| Element | Text |

Friction: <fields asked> asked, <fields needed> needed. Human touch: <name, reply promise, way to reach a person>

## Open items
- [NEED: ...] / [ASSUMPTION: ...] / [VERIFY: ...]

## Next step
<one action, owner, date or threshold>
```

## Follow-ups

- `website-design` to lay the copy into a page using the same section IDs.
- `video-script` when `hero` or `how-it-works` would land better as a 30–60 second demo.
- `positioning` when every headline option could belong to a competitor.
- `launch` when the page is ready and the founder needs a launch post, email, and sequence; `lifecycle-emails` for what signups receive after they join.
- `human-voice` for a full voice pass before the page goes live, or on any other text the founder will publish.

_Adapted from copywriting (MIT, see LICENSE). Changes: original text throughout; added company-context loading, request modes (point edit / single section / existing voice / blank brief), a sourced message brief, section IDs shared with website-design, a three-headline rationale format, the three-question line gate, edge cases, an AI-tells reference, an annotated output template, and a worked example. Method credit: the read-aloud test follows Paul Graham, "Write Like You Talk" (2015); the friction and human-touch step follows Kevin Hale, "How to Improve Conversion Rates" (YC Startup School). Both described in original wording._
