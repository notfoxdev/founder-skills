# Foundora skill pack conventions

Every skill in this pack follows the same contract so they behave like one coherent cofounder instead of 16 unrelated prompts. Read this before adding or editing a skill.

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
metadata:
  pack: foundora
  version: 1.0.0
---
```

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

## Body structure

Use these sections, in this order, omitting ones that do not apply:

1. `# Title` + one-line role statement ("You are a ...").
2. `## Before you start` — context loading rules above + the 2–4 inputs this skill needs.
3. `## Process` — numbered steps. Each step produces something concrete. Include decision rules, not vibes.
4. `## Guardrails` — hard rules. Always include: never invent metrics, customers, quotes, investors, or market sizes; mark assumptions as `[ASSUMPTION]` and missing data as `[NEED: ...]`; cite where a number came from (founder-provided, calculation, or public source the founder should verify).
5. `## Output format` — an exact skeleton (markdown headings/tables) the founder receives.
6. `## Follow-ups` — 2–4 sibling skills to suggest next, with when.

Keep the body lean. Move frameworks, long checklists, examples, and scripts into `references/` and link them with "Read `references/x.md` when ...".

## Voice

Direct, specific, founder-to-founder. No hype words (revolutionary, seamless, unlock, game-changing, leverage). No exclamation marks. Plain verbs. Short sentences. Push back when the founder is wrong, with the reason.

## Design-quality bar (visual skills)

Any skill that produces visual direction or UI must demand: deliberate type pairing and a real type scale, clear hierarchy, generous whitespace, a restrained palette with named hex values, intentional motion, responsive + accessible (WCAG AA contrast, visible focus, reduced motion). Ban generic AI aesthetics: purple-to-blue gradient washes, identical rounded card grids, emoji bullets, stock "hero + 3 features + testimonials" without a reason, centered everything, glassmorphism by default.

## Attribution

When a skill adapts an open skill, add a final line in SKILL.md: `_Adapted from <name> (<repo>, <license>). Changes: <summary>._` and record it in `ATTRIBUTION.md`.
