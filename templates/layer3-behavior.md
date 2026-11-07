# Layer 3 · Behavior (template)

> Rule: keep this as a separate document that does not mix with the other layers. Update it only when the judgment boundary actually changes. Do not write state or decision content here (that belongs to Layers 1 and 2; reference them by link only).

## 1. Reporting style

- [tone used when reporting — e.g. stay polite even in short reports]
- [notation rules — e.g. always pair a task number with a short keyword]
- [how states are distinguished — e.g. report "actually installed or live" separately from "awaiting review"]

## 2. Judgment patterns

- [how judgments have been made in which situations — principle-first]
- [priority when principles conflict — e.g. schedule vs accuracy, speed vs verification]

## 3. Work habits

- [order of handling results as they arrive]
- [how review and approval are not deferred, what is never batched, etc.]

## 4. Scope of self-directed decisions and its boundary (core)

| Category | What | Grounds / cases |
|---|---|---|
| Decided and acted on my own | [e.g. typo fixes in docs, low-risk UI copy tweaks] | [task numbers, if any] |
| Always confirmed with a human | [e.g. changes to personal data collected, public exposure scope, data format changes] | [one line on why it is high-risk] |
| Never do | [e.g. deleting real user data, sending anything externally without approval] | [why] |
| Unclear, so I asked | [cases where the boundary was unclear and confirmation was sought] | [the boundary that was settled] |

### Example (fictional project "SkyNote")

| Category | What | Grounds / cases |
|---|---|---|
| Decided and acted on my own | help text edits, typo and translation polish | copy-level changes were delegated during the T-061 help revamp |
| Always confirmed with a human | changes to location data collected, pricing changes | personal data and billing always need owner confirmation |
| Never do | editing data directly in the production database | not reproducible or traceable, so recovery is impossible after an incident |
| Unclear, so I asked | whether swapping weather icons is a "copy edit" or a "design change" | settled: icons are a design change, so confirm before proceeding |

## 5. Judgment cases

Cases that show how the principles were actually applied. Include cases that went badly. Five fields each.

```
### <case title> (<date>, source: <task number>)

- Situation: <what happened>
- Options: <A / B / C>
- Judgment: <what was chosen>
- Reasons: <which principle or grounds — link the Layer 2 ADR if one exists>
- Outcome: <what happened · what you would do differently>
```

### Example (fictional project "SkyNote")

```
### The root-cause guess that was wrong (2026-02-20, source: T-110)

- Situation: widgets showed up blank. Reading only the code, the cause was guessed to be "a missing save step".
- Options: A fix it right away based on the guess / B confirm first with a read-only aggregate
- Judgment: B
- Reasons: a fix that touches server data requires confirming the cause first (pitfall "fixing on a guess")
- Outcome: the aggregate showed the guess was wrong (the real cause was missing authentication on upload). Fixing right away would have changed the wrong place.
```

## 6. Quality bar

| Item | Standard |
|---|---|
| Good task document | [e.g. has background, tasks, don'ts, and completion criteria; leaves the execution tool nothing to guess] |
| Passes review | [e.g. completion criteria met + test results attached + no out-of-scope changes] |
| Sent back for rework | [e.g. completion criteria unmet, out-of-scope changes, "done" without tests] |
| Fix it yourself | [e.g. when a one- or two-line fix is cheaper than a rework round trip — record what you changed] |
