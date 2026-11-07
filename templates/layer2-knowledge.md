# Layer 2 · Knowledge (template)

> Rule: append only. Never edit a record once written. When a decision changes, mark the old record "superseded" and add a new one. Every item has a source. Never fill with guesses.

## 1. Decision records (ADR)

One decision per record. Copy the template below.

```
## ADR-<no.> · <date> · <decision title>

- Context: <why this decision was needed>
- Decision: <what was decided>
- Reasons: <grounds>
- Scope of impact: <what it affects>
- Status: active / superseded (→ ADR-<no.>)
- Source: <task number · document path>
```

### Example (fictional project "SkyNote")

```
## ADR-003 · 2026-02-14 · Switch weather data provider from A to B

- Context: Provider A's API kept responding slowly in the early morning, so widget refreshes failed repeatedly.
- Decision: Make B the primary provider; keep A only as a fallback during outages.
- Reasons: Under the same conditions B's latency is about 1/5 of A's, and its free quota is 3× our usage.
- Scope of impact: server collection module, widget refresh interval setting.
- Status: active
- Source: T-087 · docs/measurements/provider-comparison-2026-02.md
```

## 2. Domain knowledge

Write *why things are the way they are* — what you cannot learn from code and documents alone. Short entries per topic, linked to the ADRs and documents behind them.

```
## <topic>

- <key fact and its reason>
- Deeper: <path> (linked from the knowledge map)
```

## 3. Pitfalls

Only failures that actually happened. Three lines each.

```
## <failure title> (<date>, source: <task number>)

- What happened: <one line>
- Why: <cause in one line>
- Never again: <prevention rule in one line>
```

### Example (fictional)

```
## Widget refresh stopped and went unnoticed for two days (2026-01-20, source: T-052)

- What happened: the collection server died with no alert; we learned of it from a user report two days later.
- Why: collection failures were not reported to any channel.
- Never again: send collection failures to the alert channel immediately, and check the last collection time in the morning check.
```

## 4. Knowledge map

Per topic, "to go deeper, look here". Directions, not summaries.

| Topic | Where to look | Note |
|---|---|---|
| [topic] | [document or folder path] | [one-line guide] |
