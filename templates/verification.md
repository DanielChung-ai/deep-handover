# Verification (template)

> Run after the handover is declared done. The handover is complete only on pass. The project owner (or whoever the owner designates) sets the questions and decides the final number of questions and the pass mark at run time.

## Test areas (suggested)

| Area | What it checks | Minimum questions (suggested) |
|---|---|---|
| State | Can it state the current queue, blockers and their reasons, and pending decisions accurately? | 3 |
| Knowledge | Situational questions about why past decisions were made — reciting record numbers does not pass | 3 |
| Judgment | Given a new situation, does it separate what to do on its own from what to raise to the human, according to the Layer 3 boundary? | 4 |
| Actor distinction | Does it allocate and report without mixing up the judging agent and execution tools? | 2 |

## Live comparison (2–3 items)

Separately from the test, the outgoing and incoming agents each handle a real pending task and the results are compared.

| Task | Outgoing judgment | Incoming judgment | Agree | Layer behind the difference |
|---|---|---|---|---|
| [task number · keyword] | [gist of allocation, judgment, report] | [same items] | [yes / no] | [1 / 2 / 3] |

- How to choose: tasks that mix result review, work allocation, and a high-risk judgment. Simple tasks are not worth comparing.
- If judgments differ, the owner decides which is right, and the layer behind the difference is fixed.

## Question-writing principles

- State questions should be answerable from Layer 1 alone. If the answer is not in Layer 1, that is a defect in Layer 1, not in the question.
- Knowledge questions ask "why was it decided that way". Citing the ADR number alone does not pass.
- Judgment questions use plausible new situations. Mix in **situations that touch high-risk areas** and **situations where the boundary is unclear**.
- Actor-distinction questions use situations that invite allocation mistakes (e.g. a report that mixes up tool names).

## On failure

- Fix only the layers behind the weak areas, and re-verify only those areas. Do not start over.
- A wrong answer in the judgment area, or a split judgment in live comparison, always requires fixing Layer 3.

## Record

Append the questions and results to Layer 2 (Knowledge).

```
## Verification record · <date>

- Scope: <questions per area>
- Live comparison: <task numbers · agreement>
- Result: pass / fail (<area> fixed, re-verified)
- Layers fixed and what changed: <…>
- Completion record (the line added at the top of Layer 1): `Deep handover verified: <date> · scope <…> · result <…>`
```
