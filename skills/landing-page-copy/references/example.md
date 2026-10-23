# Worked example: landing-page-copy

> Illustrative and fictional (Ledgerline fixture). Calibrates depth and format only; never reuse its content.

**Request:** "Write the hero section."

**Context used:** `evals/fixture-company.md` as `.foundora/company.md`. Single-section mode, so only the brief rows the hero needs. The page goal is the existing waitlist (ledgerline.app). No interview transcripts are in context: the problem phrases come from the founder's `## Problem` summary of 11 interviews, so they are cited as a summary, not as verbatim quotes. Hard parts shown: an option that fails the gate, a rejected time-saved angle, a competitor-uniqueness claim flagged `[VERIFY]`.

---

## Recommendation
Use option 1, "See which clients are blocked, down to the reconciliation." It names the partner's visibility problem from your interviews, a partner can check it in one look, and the reconciliation detail is what a generic workflow template does not claim. Before it ships: `[NEED: 3 verbatim interview phrases]` to confirm "blocked" is the partners' word, and `[VERIFY]` the reconciliation claim against current Karbon and TaxDome templates.

## Message brief
| Field | Content | Source |
| --- | --- | --- |
| Reader | Managing partner at a 3–15 person bookkeeping firm running month-end close for 20–80 clients | `company.md` Problem, Target customer |
| Trigger | A close deadline slipped, or a reviewer redid work, this month | `[ASSUMPTION]` from Problem |
| Problem in their words | "can't see which clients are blocked"; "reviewers redo work" | `company.md` Problem (founder summary), `[NEED: verbatim phrases]` |
| Current alternative | Google Sheets close checklists, Karbon or TaxDome workflow templates, doing nothing | `company.md` Alternatives |
| The shift | One board: every client's close, who is blocked on what, what is already reconciled | `company.md` Snapshot, Problem |
| Proof available | Founder ran ops at a 9-person bookkeeping firm for 4 years; 2 firms start a 30-day pilot next week | `company.md` Team, Traction |
| Top objection | "We already pay for Karbon or TaxDome" | `company.md` Biggest risk |
| Awareness | Problem-aware: partners feel close slipping; few have looked for a separate tool | `[ASSUMPTION]` |

## Headline options
1. **See which clients are blocked, down to the reconciliation.**
   Subhead: Ledgerline is a month-end close checklist for bookkeeping firms of 3 to 15 people. Every client, every reconciliation, and who is waiting on what, on one board. (27 words)
   Angle: problem to outcome | Best for: partners who feel the visibility gap | Risk: "down to the reconciliation" is ops-lead language; partners may skim it | Gate: picture yes / falsifiable yes / unique yes `[VERIFY]`
2. **Run month-end close without the shared spreadsheet.**
   Subhead: One checklist per client, ticked as each account is reconciled, so the partner sees status without asking. (17 words)
   Angle: contrast with the alternative | Best for: firms still on Sheets | Risk: firms on Karbon templates do not feel spreadsheet pain | Gate: picture yes / falsifiable yes / unique no (any close tool can say it)
3. **Month-end close tracking for bookkeeping firms of 3 to 15.**
   Subhead: Built by a former ops lead of a 9-person firm, for partners who run close for 20 to 80 clients. (20 words)
   Angle: audience call-out | Best for: partners who distrust tools built for large firms | Risk: names a category, not a scene | Gate: picture no / falsifiable yes / unique yes

Recommendation: 1, because it is the only option that passes all three questions and it uses the problem the founder heard most. Option 3's subhead is strong proof; reuse it in `proof`.

Not offered: a time-saved angle ("Close 3 days sooner"). There is no measured time saving yet, and a partner would ask where the number came from. After the pilots it becomes "Close [NEED: median days saved across pilot firms, measured before and after] days sooner".

## Page copy
### hero
- Headline: See which clients are blocked, down to the reconciliation.
- Subhead: Ledgerline is a month-end close checklist for bookkeeping firms of 3 to 15 people. Every client, every reconciliation, and who is waiting on what, on one board.
- Primary CTA: Join the waitlist
- Secondary CTA (text link): Or talk to [NEED: founder first name] for 20 minutes
- Under-CTA line: We reply to every signup personally. `[NEED: founder confirms they will]`
> Why: the partner buys, so the headline answers the partner's question; the secondary CTA serves the 90-day goal of 3 paying firms, which a waitlist alone will not reach. | Proof: problem from `company.md`, founder background held for `proof`. | Gate: headline 3/3, subhead 3/3, CTA n/a.

Gate fixes made while drafting:

| Draft line | Failed | Rewrite |
| --- | --- | --- |
| "Ledgerline helps your firm stay on top of month-end close." | picture, unique; "helps" is a tell | "Every client, every reconciliation, and who is waiting on what, on one board." |
| "Close with confidence." | all three | Cut |
| "Works alongside Karbon and TaxDome." | falsifiable but unverified: implies an integration that does not exist | Moved to `faq` as `[NEED: honest answer on using both]` |

AI-tells pass: no banned phrases, no em dashes, no exclamation marks, sentence case throughout.

## Microcopy
| Element | Text |
| --- | --- |
| Email label | Work email |
| Placeholder | you@yourfirm.com |
| Button, loading | Adding you... |
| Success | You are on the list. [NEED: what happens next, and when] |
| Error | That did not go through. Check the address and try again. |

## Open items
- [NEED: 3 verbatim phrases from the 11 interviews about blocked clients]
- [NEED: founder first name for the secondary CTA; confirm the reply promise]
- [VERIFY: Karbon and TaxDome close templates do not track individual reconciliations]
- [ASSUMPTION: partners are problem-aware but not searching for a tool]

## Next step
At pilot kickoff (week of 2026-10-26, `[ASSUMPTION]` on the exact date), show both pilot partners options 1 and 3 with no explanation and ask which describes their month. Same pick: ship it. Split: ship option 1, then email the 9 in-band waitlist firms the same question by 2026-11-06 and go with the majority.

Logged to `.foundora/journal.md`:

```markdown
### 2026-10-20 — decision: Hero headline direction
- Chose "See which clients are blocked, down to the reconciliation." over a spreadsheet-contrast and an audience call-out option
- Only option passing all 3 gate questions; problem phrase from founder summary, not yet verbatim
- Revisit after pilot kickoff test (week of 2026-10-26); add time-saved line only once pilots measure it
- Source: landing-page-copy
```
