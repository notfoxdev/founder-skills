# Foundora founder skills

Seventeen agent skills that turn Claude Code, Codex, Cursor, or any [Agent Skills](https://agentskills.io)-compatible coding agent into a cofounder that already knows your company.

## Install

```bash
npx skills add notfoxdev/founder-skills
```

Non-interactive, for one agent (what the Foundora install prompt runs):

```bash
npx skills add notfoxdev/founder-skills --skill '*' -a claude-code -y   # or -a codex / -a cursor
```

Add `-g` to install for every project on your machine. Requires Node.js 22.20+.

This repository is private: installing requires Git or GitHub CLI credentials with read access to it.

## Load your company context

Every skill reads `.foundora/company.md` first, so it never re-asks what you already told it. Foundora generates this file for you at the end of onboarding, along with a prompt that writes it into your repo and points `CLAUDE.md` / `AGENTS.md` at it. No onboarding? Ask your agent to "set up my company context" and the `company-context` skill interviews you and writes it. Or copy [`templates/company.md`](templates/company.md) and fill it in by hand.

The agent keeps a running decision log in `.foundora/journal.md`.

## Skills

| Skill | Use it to |
|---|---|
| `cofounder` | Start here. Context-aware sounding board, prioritisation, decisions, weekly check-ins |
| `idea-validator` | Pressure-test an idea to a BUILD / KILL / PIVOT verdict; Mom Test interviews and analysis |
| `lean-canvas` | One-page business model, value proposition fit, unit economics |
| `customer-research` | Interview kits, synthesis, evidence-based personas, alternatives scan |
| `mvp-scoper` | Cheapest test of the riskiest assumption; ruthless feature triage |
| `positioning` | Alternatives → unique value → category → messaging hierarchy |
| `website-design` | Distinctive, production-quality landing pages and sites, designed and built |
| `landing-page-copy` | Conversion copy that drops into the `website-design` section layout |
| `pricing-strategy` | Value metric, model, tiers, willingness-to-pay research, price tests |
| `launch` | Readiness gate, channel plan, T-30 → T+14 timeline, launch-day run of show |
| `video-script` | Launch, demo, and short-form scripts with timed VISUAL / AUDIO tables |
| `cold-outreach` | Short, verifiable, personalised outreach sequences |
| `pitch-deck` | Narrative-first seed decks and slide-by-slide critique |
| `fundraising` | Readiness, round sizing, investor pipeline, meeting prep, close |
| `investor-update` | Honest monthly updates with consistent metrics |
| `weekly-review` | North Star scoreboard, three priorities, kill list, 90-day resets |
| `company-context` | Create or update `.foundora/company.md` when you pivot, change stage, or get new numbers |

## Principles

- Context first: read `.foundora/company.md`, ask only for what is missing.
- Never invent metrics, customers, quotes, investors, or market sizes. Gaps are marked `[NEED: ...]`, guesses `[ASSUMPTION]`.
- Every skill ends with an exact output format and the next skill to run.
- Visual skills hold a high design bar and ban generic AI aesthetics.
- Every skill ships a worked example and an edge-case section, and is regression-tested with [`evals/scenarios.md`](evals/scenarios.md).

See [CONVENTIONS.md](CONVENTIONS.md) for authoring rules, [CHANGELOG.md](CHANGELOG.md) for what changed, and [ATTRIBUTION.md](ATTRIBUTION.md) for adapted sources.
