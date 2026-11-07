# Layer 1 · State (template)

> Rule: current values only. No history. When state changes, overwrite this document.
> On completion, add one line at the top: `Deep handover verified: <date> · scope <…> · result <…>`

## Current phase

- Phase: [e.g. preparing for launch]
- Next goal and deadline: [e.g. public release next quarter]

## Work in progress

| No. | Keyword | Status | Owner |
|---|---|---|---|
| [T-001] | [short keyword] | [in progress / awaiting review, etc.] | [judging agent / execution tool / human] |

## Queue (next items per owner)

- [owner]: [next item] → [item after that]

## Blockers

| No. | Why blocked | Unblocks when |
|---|---|---|
| [T-00X] | [quota exhausted / waiting for live check / waiting for decision — distinguish] | [condition] |

## Pending decisions

- [what a human must decide — one per item]

## Remaining live checks

- [what still needs checking on real devices or the live service]

## Tools and channels

- [current status of execution tools and automation channels — date anything time-bound, such as quota reset times]

---

## Example (fictional project "SkyNote")

### Current phase

- Phase: preparing for public release
- Next goal and deadline: store review submission in mid-March

### Work in progress

| No. | Keyword | Status | Owner |
|---|---|---|---|
| T-104 | widget weather refresh delay | awaiting review | execution tool A |
| T-105 | privacy policy revision | in progress | judging agent |

### Blockers

| No. | Why blocked | Unblocks when |
|---|---|---|
| T-098 | weather data provider API quota exhausted | quota resets March 1 |

### Pending decisions

- T-105: whether to add "neighborhood-level location" to collected data (personal data — needs confirmation before execution)
