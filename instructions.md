# Deep Handover — Instructions (blank template)

> This is the instruction template you give to the outgoing AI. Fill the `[bracketed]` placeholders for your project.
> The handover outputs you produce (actual state and records) must not go to a public repository — only this template is public.

- Outgoing agent: [the AI / party that has been planning and judging so far]
- Incoming agent: [the AI / party taking over the role]
- Reasoning level: run the entire handover at high reasoning. After verification passes and normal work resumes, return to the usual level.

## 0. Purpose and scope

- Purpose: hand over the project's **state, knowledge, and way of judging** completely, so the incoming agent can resume as the project's planning and judging agent. This is not a read-and-done handover; it is complete only after passing verification (section 5).
- **Actor distinction (the premise of this whole handover)**: [judging agent] is the owner of planning, judgment, review, and approval. [execution tools] carry out instructions. They are **separate actors** and must not be named or reasoned about interchangeably. What is handed over is the judging agent's role; the execution tools appear in the state layer only as "status of tools and execution channels".
- Out of scope: follow-up actions that assume the handover is complete (cleaning up permissions, accounts, etc.). **Passing verification is only the precondition** for settling those actions; carrying them out requires a separate instruction.

## 1. Where to look (sources)

Do not copy content into these instructions or the outputs. Point to locations only; the incoming agent reads them directly.

- [project repository path]
  - [shared rules document] — project-wide rules
  - [planning and rules documents] — current standard for roles and procedures
  - [task document location] — the status line is the live progress; the result section is the history
  - [measurement and verification records]
- [shared context store — background on working style and decision patterns]
- [workspace (worktrees etc.) location] — for checking current state

In the outputs, write a **summary plus a path (link)**, not copied text.

## 2. Order of work

1. **Prepare**: read the sources in section 1 and collect the current state. Do not fill unknowns with guesses — mark anything you cannot confirm as "unconfirmed".
2. **Write Layer 3 · Behavior** (3-3). Keep it as a separate document. The way of judging is the heart of the handover and the easiest thing to lose, so it comes first.
3. **Write Layer 2 · Knowledge** (3-2). Reconstruct past decisions, starting with high-risk areas ([your project's high-risk areas, e.g. data integrity, public exposure, personal data]).
4. **Write Layer 1 · State** (3-1). It goes stale fastest, so write it last, with values as of just before the handover.
5. **Checks** (`templates/checklists.md`): cross-check (no mixing between layers, link-only references; section 4), transfer-gap check (assets left in the environment you are leaving), and pre-publication check (no real content mixed into the template you publish).
6. **Incoming-agent onboarding**: the incoming agent reads the three layers and raises questions. Answer them; if an answer is not in the outputs, fill that layer.
7. **Verification** (section 5). On failure, fix only the weak layers and re-verify. Do not start over.
8. **Completion record**: on pass, record it in the format of section 6.

## 3. Outputs — three layers

Keep the outputs in one folder, one document per layer. Templates are in `templates/`.

### 3-1. Layer 1 · State (overwrite)

Only current values. No history (history lives in task records and Layer 2). When state changes, overwrite this layer only.

Include:

- Current phase and next goal (date anything time-bound)
- Work in progress — number + short keyword + status + owner ([judging agent] / [execution tool] / human)
- Queue — waiting order per owner and the next item to start
- Blockers and why — distinguish external conditions per item (quota, waiting for real-device check, waiting for a human decision, etc.)
- Pending decisions — what a human must decide, and high-risk items that need confirmation before execution
- What still needs checking on real devices or in the live environment
- **Return-review task (add when needed)**: if decisions or work were carried out under an interim arrangement during the handover, add an item for the returning judging agent to review all of it and submit a list of proposals to the human. Do not execute review results without approval.

### 3-2. Layer 2 · Knowledge (append only)

- **Decision records (ADR style)**: one record per decision. Never edit a record once written. When a decision changes, mark the old record "superseded" and add a new one.
  - Format: number · date / context / decision / reasons / scope of impact / status (active · superseded) / source (task number · document path)
- **Domain knowledge**: centered on *why things are the way they are* — what you cannot learn from code and documents alone.
- **Pitfalls**: real failures and the rule that prevents them from recurring. Three lines per failure: what happened / why / never again how.
- **Knowledge map**: per topic, "to go deeper, look here". Directions, not summaries.
- Rules: no guessing. Every item has a source (number, document, date).

### 3-3. Layer 3 · Behavior (separate document)

A separate document that does not mix with the other layers.

- **Reporting style**: the actual patterns used when reporting to the human — tone, notation rules, how states are distinguished when reporting.
- **Judgment patterns**: how judgments have been made in which situations; the principles behind them and their priority when they conflict.
- **Work habits**: actual operating habits — the order of handling results as they arrive, not deferring review or approval, etc.
- **Scope of self-directed decisions and its boundary (the heart of this layer)**: write it as a table.
  - Decided and acted on without human confirmation
  - Always confirmed with a human (high-risk areas, etc.)
  - Not done, or decided never to do
  - Cases where the boundary was unclear and you actually asked
- **Judgment cases**: principles alone are hard to apply to new situations. Record real cases where judgment could have gone either way in five fields: situation / options / judgment / reasons / outcome. Include cases that went badly.
- **Quality bar**: what makes a good task document, what counts as passing review, what gets sent back for rework, and when you fix things yourself.

## 4. Layer rules

- Layers reference each other **by link only**. Never copy one layer's content into another (copies drift apart when only one side is updated).
- Layer 1 is overwritten. Layer 2 is append-only. Layer 3 changes only when the judgment boundary actually changes.
- No passwords, credentials, or personally identifiable information in any layer.

## 5. Verification

After the handover is declared done, test the incoming agent on key judgment situations. The handover is complete only on pass.

- Set by: the project owner (or whoever the owner designates). The owner decides the final number of questions and the pass mark at run time.
- Areas (suggested):
  1. **State** — can it state the current queue, blockers and their reasons, and pending decisions accurately?
  2. **Knowledge** — situational questions about why past decisions were made. Reciting record numbers does not pass.
  3. **Judgment** — given a new situation, does it separate what to do on its own from what to raise to the human, according to the boundary? This tests the Layer 3 boundary in particular.
  4. **Actor distinction** — does it allocate and report without mixing up the judging agent and the execution tools?
- Minimum questions per area (suggested): state 3 · knowledge 3 · judgment 4 · actor distinction 2.
- **Live comparison (2–3 items)**: questions can be memorized. Have the outgoing and incoming agents each handle a real pending task (one that mixes result review, work allocation, and a high-risk judgment) and compare their judgment, allocation, and reporting. If they differ, the owner decides which is right, and the layer behind the difference is fixed.
- On failure: fix only the layers behind the weak areas and re-verify only those areas. A wrong answer on boundary judgment, or a split judgment in live comparison, always requires fixing Layer 3.
- Keep the questions and results as a record (appended to the knowledge layer).

## 6. Completion criteria

The handover is complete only when all of the following hold:

- All three layer documents exist, and links between them work
- Onboarding questions from the incoming agent are resolved (none left open)
- Verification test passed, and live comparisons agree (or the differences have been fixed)
- All three checklists are done (especially the transfer-gap check — no assets left behind, or a plan exists for each)
- A one-line completion record at the top of the state layer: `Deep handover verified: <date> · scope <…> · result <…>`

After completion (outside the scope of these instructions; only confirm the preconditions):

- Settling follow-up actions (permissions, accounts, etc.) happens separately, on the premise that verification passed.
- The incoming agent returns to its usual reasoning level when normal work resumes.
- If there was an interim arrangement, the returning judging agent's first task is the return-review task in 3-1.
