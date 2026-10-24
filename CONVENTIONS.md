# Foundora skill pack conventions

Every skill in this pack follows the same contract so they behave like one coherent cofounder instead of a pile of unrelated prompts. Read this before adding or editing a skill.

## Layout

```
skill-pack/
  skills/
    <skill-name>/
      SKILL.md            # required. Frontmatter + lean body (aim for 80–220 lines)
      references/*.md     # optional. Deep material loaded only when needed (progressive disclosure)
      templates/*.md      # optional. Output skeletons the skill fills in
```

`npx skills add <source>` discovers every `skills/<name>/SKILL.md` and installs them as one pack.

## Frontmatter

```yaml
---
name: kebab-case-name            # must equal the folder name
description: >-
  One dense paragraph (60–120 words): what the skill does, then "Use when the founder says ..."
  with 8–15 quoted trigger phrases real founders type, then "Not for ..." pointing to sibling
  skills so the agent routes correctly.
license: MIT                     # Apache-2.0 for website-design (adapted material)
metadata:
  pack: foundora
  version: 1.3.0                 # bump the minor version when a skill's behaviour changes
---
```

Spec limits (agentskills.io): `name` ≤ 64 chars, lowercase/digits/hyphens, equals folder; `description` ≤ 1024 chars; SKILL.md under 500 lines (this pack targets 120–260); references one level deep.

Descriptions are the routing layer. Be concrete, use founder vocabulary ("is this idea any good", "kill or keep", "write my investor update"), and name sibling skills for neighbouring jobs.

## Company context (shared memory)

All skills read the founder's context before asking anything:

1. `.foundora/company.md` — written by the Foundora install prompt. Founder-owned facts: snapshot, problem, customer, stage, team, traction, constraints, biggest risk, 90-day goal, alternatives, working preferences.
2. `.foundora/journal.md` — agent-maintained running log: decisions, assumptions under test, experiments, learnings. Create it on first write.

Rules every skill states in a "Before you start" section:

- Read `.foundora/company.md` (and `.foundora/journal.md` if present). If missing, say so in one line and ask only for the 2–4 facts this skill needs. Never block on the file.
- Do not re-ask anything the context already answers. Reference it ("Since you're at MVP stage with 3 design partners...").
- Honour `## Working preferences` for tone.
- Never edit `.foundora/company.md` without explicit confirmation. Propose a diff instead. Append to `.foundora/journal.md` freely (dated, one entry per decision/learning) and tell the founder you did.
- If `company.md` is missing entirely and the founder wants ongoing help, suggest `company-context` to create it (one line, not a blocker).

### Journal entry format (identical in every skill)

```markdown
### YYYY-MM-DD — <decision | assumption | experiment | learning | review>: <short title>
- <2–5 skill-specific bullets: what, evidence, thresholds, next step / revisit date>
- Source: <skill-name>
```

Newest entries go at the bottom. Never rewrite or delete past entries; supersede them with a new entry that names the old one.

## Body structure

Use these sections, in this order, omitting ones that do not apply:

1. `# Title` + one-line role statement ("You are a ...").
2. `## Before you start` — context loading rules above + the 2–4 inputs this skill needs.
3. `## Process` — numbered steps. Each step produces something concrete. Include decision rules, not vibes.
4. `## Guardrails` — hard rules. Always include: never invent metrics, customers, quotes, investors, or market sizes; mark assumptions as `[ASSUMPTION]` and missing data as `[NEED: ...]`; cite where a number came from (founder-provided, calculation, or public source the founder should verify).
5. `## Edge cases` — 4–8 bullets: the situations where following the process literally gives a bad result (no data at all, conflicting context, founder pushes back, request is out of scope, stage mismatch) and exactly what to do instead.
6. `## Output format` — an exact skeleton (markdown headings/tables) the founder receives.
7. `## Follow-ups` — 2–4 sibling skills to suggest next, with when.

Keep the body lean. Move frameworks, long checklists, examples, and scripts into `references/` and link them with "Read `references/x.md` when ...".

### Worked example (required)

Every skill ships `references/example.md`: one realistic request, the relevant context, and a complete model answer in the skill's output format, built on the fictional company in `evals/fixture-company.md` (Ledgerline). The SKILL.md links it with "Read `references/example.md` to calibrate depth and tone before your first answer." Rules:

- Clearly labelled as illustrative and fictional at the top.
- Numbers in the example come only from the fixture or are shown calculations.
- Show the skill doing the hard part well: a pushback, a `[NEED: ...]`, a decision rule applied. Not a happy path where everything is known.
- Never copy the example's content into a real answer; it calibrates depth and format only. Say this in the example's header.

## Response discipline

- Lead with the answer or verdict, then the support.
- Ask at most one round of questions before producing something useful; if inputs are missing, produce a draft with `[NEED: ...]` markers instead of stalling.
- Match length to the ask: a point request ("fix this headline") gets a short answer, not the full template.

## Voice

Direct, specific, founder-to-founder. No hype words (revolutionary, seamless, unlock, game-changing, leverage). No exclamation marks. Plain verbs. Short sentences. Push back when the founder is wrong, with the reason.

### Sound like a person

The skills talk to a founder the way a sharp friend who has done the job would: warm, plain, and on their side, without flattery. Anything a skill writes for the founder to publish (posts, emails, pages, scripts, updates) has to read like the founder wrote it on a good day.

- Write the way people talk. Contractions are fine. "We" and "you", not "the user" and "stakeholders".
- Say the specific thing. "Two firms said they'd pay $150" beats "strong early signal".
- Vary sentence length. A short line after a long one is how people actually write.
- Use the founder's own words from `company.md`, the journal and their messages. Borrow their phrasing before inventing yours.
- Leave out the AI tells: "it's not X, it's Y" contrasts, forced lists of three, tidy one-line closers, staged openers ("Here's the thing:"), stacked em dashes, bold labels on every line, "delve", "elevate", "robust", "in today's fast-paced world".
- If a sentence would fit any company, rewrite it until it only fits this one, or cut it.
- Before handing over publishable text, read it as the founder's sharpest customer would. If a line sounds like a brochure, rewrite it. `human-voice` holds the full pattern list.

## Design-quality bar (visual skills)

Any skill that produces visual direction or UI must demand: deliberate type pairing and a real type scale, clear hierarchy, generous whitespace, a restrained palette with named hex values, intentional motion, responsive + accessible (WCAG AA contrast, visible focus, reduced motion). Ban generic AI aesthetics: purple-to-blue gradient washes, identical rounded card grids, emoji bullets, stock "hero + 3 features + testimonials" without a reason, centered everything, glassmorphism by default.

## Attribution

When a skill adapts an open skill, add a final line in SKILL.md: `_Adapted from <name> (<repo>, <license>). Changes: <summary>._` and record it in `ATTRIBUTION.md`.
