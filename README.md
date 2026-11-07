# Deep Handover

A three-layer handover template for AI-assisted projects, so that **judgment does not break when the working agent changes**.

When a session ends, or the account, model, or AI in charge changes, people usually hand over only the *state*. But what actually gets lost is not the state. It is **why things were decided** and **how far the agent may decide on its own**. This template defines a procedure that carries both across.

## Why

- A typical handover note (a status summary) tells the new agent *what* is in progress, but it does not make the new agent judge by the same standards.
- When the reasons behind decisions disappear, the new agent either reopens settled debates or reverts decisions it should not touch.
- Without a decision boundary, the new agent either asks for confirmation on trivial things or goes ahead on things that must never proceed without confirmation.

## Structure — three layers

| Layer | What it holds | How it is updated |
|---|---|---|
| Layer 1 · State | Current values right now (phase, work in progress, blockers, pending decisions) | **Overwrite** — no history |
| Layer 2 · Knowledge | Decision records (ADR), domain knowledge, pitfalls, knowledge map | **Append only** — never edit a record; when it changes, mark it "superseded" and add a new one |
| Layer 3 · Behavior | Reporting style, judgment patterns, work habits, **the scope of self-directed decisions and its boundary** | Only when the boundary actually changes |

Core rules:

- **Layers reference each other by link only.** Never copy one layer's content into another (copies drift apart when only one side is updated).
- The **decision boundary table** in Layer 3 is the heart of this method: "decided and acted on my own / always confirmed with a human / never do", with real cases.
- A handover is not finished by reading. It is complete only after passing **a test plus live comparison** (steps 5–7 below).

## Procedure

1. Give `instructions.md` (the handover instructions) to the outgoing AI. Fill the `[bracketed]` placeholders for your project.
2. The outgoing agent reads the sources and writes **Layer 3 (Behavior) → Layer 2 (Knowledge) → Layer 1 (State)**, in that order. The way of judging is the core and the easiest thing to lose, so it goes first; state goes stale fastest, so it is written last to be accurate at handover time.
3. Run `templates/checklists.md`: cross-check (no mixing between layers, link-only references), transfer-gap check, and pre-publication check.
4. The incoming agent reads the three layers and raises questions. If an answer is not in the documents, fill that layer.
5. Verification: a test (state, knowledge, judgment boundary, actor distinction) **plus 2–3 live comparisons** (the outgoing and incoming agents each handle the same real task and their judgments are compared).
6. On failure, fix only the layers behind the weak areas and re-verify only those areas.
7. On pass, add a one-line completion record at the top of Layer 1.

## Files

- `instructions.md` — instructions you can hand to the outgoing AI as-is
- `templates/layer1-state.md` — Layer 1 state template (+ example)
- `templates/layer2-knowledge.md` — Layer 2 knowledge template (ADR, pitfalls, knowledge map)
- `templates/layer3-behavior.md` — Layer 3 behavior template (decision boundary, judgment cases, quality bar)
- `templates/verification.md` — verification template (test + live comparison)
- `templates/checklists.md` — cross-check, transfer-gap check, pre-publication check

All examples use a fictional weather app project, "SkyNote".

## Publication principles

- Publish **only the templates**. Keep your project's actual handover outputs (state, decision records, behavior patterns) in a private repository. Real outputs contain internal schedules, decision boundaries, and failure records; they are not public material.
- Never write passwords, credentials, or personally identifiable information anywhere in handover documents.

## Assumption about actors

This template distinguishes the **judging agent** (the AI responsible for planning, decisions, and review) from **execution tools** (the tools or bots that run code). They are separate actors. Never mix how you name them or how you reason about them; this distinction underlies the whole handover. Fill the placeholders in the instructions to match your own tool setup.

## License

CC BY 4.0 — see [LICENSE](LICENSE). Free to use and adapt with attribution.
