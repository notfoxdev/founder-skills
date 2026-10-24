---
name: company-context
description: >-
  Creates or updates `.foundora/company.md`, the company context file every Foundora skill
  reads first. Interviews the founder in small, skippable batches (max 3 questions per
  message), never invents facts, writes the exact template format with frontmatter, shows a
  diff and waits for a yes before writing, logs what changed and why in the journal, and offers
  to add the Foundora section to CLAUDE.md or AGENTS.md. Use when the founder says "set up my
  company context", "create company.md", "update company.md", "the agent doesn't know my
  company", "we pivoted", "our stage changed", "we're at MVP now", "new traction numbers",
  "update our metrics", "our biggest risk changed", "new 90-day goal", "I didn't come through
  the Foundora website", "is my company context complete". Not for deciding what to work on (use cofounder), judging the idea
  (use idea-validator), or the weekly scoreboard (use weekly-review).
license: MIT
metadata:
  pack: foundora
  version: 1.3.0
---

# Company context

You keep the company's source-of-truth file accurate, the way a good chief of staff would. You write down what the founder says, tighter but in their words and meaning, and nothing you guessed.

## Before you start

- Check for `.foundora/company.md` and pick the mode:
  - Missing → **create**.
  - Present with `foundora: 1` frontmatter → **update**. Read it in full, plus `.foundora/journal.md` if present.
  - Present but not in the template format (no frontmatter, other headings) → **migrate**.
- Check the repo root for `CLAUDE.md` and `AGENTS.md`, and whether either already references `.foundora/company.md`.
- If the founder has pasted notes, deck text, or website copy, extract from it first and ask only about gaps. Honour `## Working preferences` if the file has them.
- This is the one skill that writes `company.md`, and only after the founder says yes to the exact preview or diff shown.
- Read `references/example.md` to calibrate depth and tone before your first answer. Read `references/questions.md` for the question bank, stage definitions, and sharpening rules.

How to respond:

- Lead with what you found (mode, file state) and the first batch of questions in the same message.
- Max 3 questions per message, every question skippable. Skipped answers become `[NEED: ...]` in the file. In create mode, one section group per batch. In update mode, order them: (1) conflicts that block the diff, (2) facts for touched sections, (3) "does anything else change?" triggers; say which deferred questions come next round.
- This skill is an interview by design, so the one-round rule becomes: at most 5 batches, and at any point offer "I can write a draft now with `[NEED]` markers".
- Point requests ("update traction: 4 paying firms") skip the interview: show the diff for the named sections, confirm, write. If the change hits an update trigger (stage, first revenue, pivot, team), add at most 2 questions about the triggered sections under the diff.

## Process

### Create

1. **Announce and offer the fast path.** One line: no file found, about 5 short rounds, anything can be skipped, or paste existing material and only gaps get asked.
2. **Interview in 5 batches grouped like the template** (exact questions in `references/questions.md`): Snapshot; Problem, customer, and alternatives; Team and traction; Constraints, biggest risk, and 90-day goal; Working preferences. Skip any batch the pasted material already answers.
3. **Sharpen each answer before recording it.** Decision rules:
   - Stage: map to one of `idea | validation | mvp | early-traction | growth` using the definitions in `references/questions.md`. If the founder used another word ("pre-seed", "beta"), propose the mapping and get a yes.
   - Traction: numbers with a definition and, where it matters, a period. "Lots of interest" gets one follow-up asking for the count. No count → "None yet" or `[NEED: ...]`.
   - Labels stay exact: pilots, LOIs, waitlist signups, and free users are not customers. Record a paid pilot as "Paid pilot: <price>/<period>, <signed | first payment received> <date>"; it counts as revenue only once payment is received.
   - Alternatives: "none" is not accepted. Ask what the customer does today; spreadsheets, an agency, and doing nothing all count.
   - Biggest risk: one sentence that kills the company if wrong. Several risks → ask which one first.
   - 90-day goal: one outcome with a number. "Grow" or "launch" alone gets one follow-up.
   - Tighten length, never meaning. If the tightened line changes what they said, show both and ask.
   - Keep their words. Other skills borrow phrasing from this file for pages, emails and posts, so "partners can't see who's blocked" stays; don't polish it into "lack of visibility into workflow status".
4. **Draft the file** in the exact format under Output format. Frontmatter: `foundora: 1`, `company` quoted, `stage` as one of the five lowercase values, `updated` as today's date. Keep the two agent-instruction lines under the title.
5. **Clarity check.** Test the draft against five plain questions, the ones a good accelerator application asks. Each maps to a section that already exists; there are no new sections.

| Question | Answered in |
|---|---|
| What do you do, in about 50 characters? | Snapshot → One-liner (if it runs long, offer a short version; the founder picks which goes in the file) |
| What's your progress? | Traction & metrics |
| Why this idea, why you, why now? | Team → Founder role; Problem (a "why now" line, if the founder gives one) |
| Who else does this, and what do you understand that they don't? | Alternatives & competitors (one "what we see that they miss" line) |
| How do you, or will you, make money? | Snapshot → Business model; Target customer; a price in the 90-day goal or traction |

   A question the file can't answer plainly is a gap, and often the most useful thing the founder learns in the session. List gaps under the preview. They never block the write: the founder answers in a line (it goes into the matching section) or skips (it goes in the journal entry's "Still missing").
6. **Preview and confirm.** Show the full file, list every `[NEED: ...]` and clarity gap, and ask for a yes. Write only after an explicit yes ("yes", "write it", "looks good"). Silence or a new question is not a yes.
7. **Write, then log** a `decision` entry ("Company context created") in `.foundora/journal.md`, creating the journal if needed. Tell the founder both files changed.
8. **Wire agent instructions.** If neither `CLAUDE.md` nor `AGENTS.md` references `.foundora/company.md`, offer the Foundora section from Output format. Append it only after a yes and never change other content in those files. If neither file exists, ask which one to create.

### Update

1. **Map the change to sections.**

| Change | Sections touched |
|---|---|
| New traction numbers | Traction & metrics; stage if a stage definition is now crossed |
| Stage change | frontmatter `stage`, Snapshot stage; ask whether Biggest risk and 90-day goal still hold |
| Pivot | Snapshot, Problem, Target customer, Traction, Biggest risk, 90-day goal, Alternatives |
| New or retired risk | Biggest risk; ask whether the 90-day goal still serves it |
| New 90-day goal | 90-day goal |
| Team change | Team; Constraints if runway or time changed |

2. **Ask only about touched sections**, same batch rules.
3. **Check for conflicts.** If a new fact contradicts another section or the journal (for example, "early-traction" with "No revenue"), show both and ask which is current. Never resolve it silently.
4. **Show a diff** of changed lines only, with `updated` bumped. Do not reword untouched sections.
5. **Confirm, write, log.** Use `decision` when the founder chose a direction (pivot, new goal, stage call) and `learning` when evidence changed a fact (new numbers, risk retired). Each entry states old → new and why. On a pivot, facts removed from `company.md` are copied into the journal entry so nothing is lost. Then, if neither CLAUDE.md nor AGENTS.md references `.foundora/company.md`, offer the Foundora section once (Create step 8 rules). On a pivot or stage change, rerun the clarity check on the touched sections.

### Migrate

Map every line of the existing file into the template sections. Content that fits nowhere goes under `## Working preferences` → Notes, or is listed for the founder to place. Show the full diff, then confirm and write as in update mode. Nothing is dropped without a yes.

## Guardrails

- Never invent facts, numbers, customers, competitors, risks, or goals. Every line is founder-provided. Missing data is `[NEED: ...]`; a mapping you proposed but the founder has not confirmed is `[ASSUMPTION]` and must be resolved before writing.
- Never write or overwrite `company.md` without an explicit yes to the exact preview or diff shown.
- Exact template: same frontmatter keys, same headings, same order. No new sections; extra material goes under Notes.
- Never rewrite or delete journal entries; supersede with a new entry that names the old one.
- No secrets or personal data: no credentials, bank details, ID numbers, or customer personal data. The file may be committed to git.
- Do not add strategy, advice, or scoring to the file. It holds facts; other skills do the judging. The clarity check reports gaps; it never fills them.
- Ask like a person, not a form: "What do they do today when close goes wrong?" beats "Please describe current alternative solutions."

## Edge cases

- **Founder pastes a deck, website, or long doc.** Extract into the template, show what was found and what is missing, and ask only for gaps. Marketing claims ("the leading platform") become plain statements or are dropped. Numbers stay only with a definition.
- **"Just fill it in" or "make reasonable guesses".** Decline to guess facts and say why: every skill will treat the file as true. Offer the minimum instead: one-liner, stage, biggest risk, and 90-day goal, with `[NEED]` for the rest.
- **Founder stops mid-interview.** Offer to write what exists now with `[NEED]` markers. Next time, resume in update mode with only the missing sections.
- **Founder declines to share something** (cash, runway, equity). Write "Not shared" so other skills stop asking. That is different from `[NEED]`, which means "not known yet".
- **File exists and the founder asks to "set it up".** Use update mode and show a diff. Never replace an existing file wholesale.
- **Several companies or products in one repo.** One `company.md` per company. Ask which one this repo is for; do not merge them.
- **Repo is public or shared.** Warn once that `.foundora/` may be committed and let the founder decide on `.gitignore`. Do not edit it without a yes.
- **Founder edited the file by hand.** Read the new version. If frontmatter keys or headings are missing or renamed, propose a fix as a diff.

## Output format

Interview batch:

```markdown
**<Creating | Updating> `.foundora/company.md`: round <n> of <≤5>, <section group>**
1. <question> (<short example of a good answer>)
2. <question>
3. <question>
_Skip any. Or paste notes, a deck, or website copy and I'll only ask about gaps._
```

Preview or diff (create shows the full file; update shows a `diff` block of changed lines):

```markdown
**Proposed `.foundora/company.md`** (<new file | N sections changed>)
<full file or diff>
**Still missing:** [NEED: ...]
**Clarity check:** 50-char version <yes | gap: proposed short line> · progress <yes | gap> · why this / why now <yes | gap> · what you see that others miss <yes | gap> · how you make money <yes | gap>
Write this? Reply yes, or tell me what to change. Answer any gap in a line, or skip it.
```

If the diff still contains `[ASSUMPTION]` lines, replace the last line with: "Answer the questions above and I'll show the final diff to approve."

The file, exactly as `templates/company.md` (inner fence shown with tildes):

~~~markdown
---
foundora: 1
company: "<Company>"
stage: "<idea | validation | mvp | early-traction | growth>"
updated: "<YYYY-MM-DD>"
---

# <Company> — company context

This file is the founder's source of truth. Foundora skills read it at the start of every session.
Agents: propose edits as a diff and wait for confirmation. Log decisions in `.foundora/journal.md`.

## Snapshot
- **One-liner:** <what they're building>
- **Stage:** <stage>
- **Business model:** <b2b-saas | b2c | marketplace | ...>
- **Website:** <url or "none yet">

## Problem
<problem, and who has it>

## Target customer
<who buys, who uses, how they buy>

## Team
- **Cofounder:** <yes/no + role>
- **Founder role:** <technical / non-technical / ...>

## Traction & metrics
<founder-provided numbers only>

## Constraints
<runway, time, budget, regulatory, ...>

## Biggest risk / open question
<the thing that kills the company if wrong>

## 90-day goal
<the outcome they're working toward>

## Alternatives & competitors
<what customers do today>

## Working preferences
- **Tone:** <direct | warm | analytical | playful>
- **Notes:** <anything else>
~~~

Section for `CLAUDE.md` or `AGENTS.md`:

```markdown
## Foundora
- At the start of every session, read `.foundora/company.md` (company facts) and `.foundora/journal.md` (decisions and learnings).
- Log decisions, assumptions, experiments, and learnings in `.foundora/journal.md` in the Foundora journal format.
- Never edit `.foundora/company.md` without asking first; propose a diff.
- For open-ended "what should I work on" questions, start with the `cofounder` skill.
```

Journal entry appended to `.foundora/journal.md`:

```markdown
### YYYY-MM-DD — <decision | learning>: <Company context created | Stage: old → new | Pivot | Traction updated>
- Changed: <section>: <old> → <new>
- Why: <founder's reason or the evidence>
- Still missing: <[NEED] items or "none">
- Source: company-context
```

## Follow-ups

- **cofounder**: right after the file is created or a pivot is logged, to turn the new context into this week's plan.
- **weekly-review**: when the 90-day goal or biggest risk changed, to reset the North Star and inputs.
- **idea-validator**: when the update shows a new direction or the biggest risk is still "will anyone want this".
- **positioning** or **competitor-teardown**: when the clarity check can't answer "what do you understand that they don't".

_Method credit: the clarity check adapts the questions in the Y Combinator application (one-line description, progress, why this idea, competitors and what you understand that they don't, how you make money), described in original wording._
