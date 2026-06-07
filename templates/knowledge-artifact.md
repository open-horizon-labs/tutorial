# Knowledge Artifact Template

Choose the smallest artifact that changes future behavior.

## Metis

Use when you learned a situated pattern.

Write to `.oh/metis/<slug>.md`:

```markdown
---
id: <slug>
title: "<title>"
outcome: <related-outcome-id>
---

## Observation

What did we expect?

## Reality

What actually happened?

## Consequence

Why did the difference matter?

## Future behavior

What should a future agent or human do differently?

## Provenance

Files, commands, review findings, or session references.
```

## Signal

Use when you found a measurement that indicates movement or risk.

Write to `.oh/signals/<slug>.md`:

```markdown
---
id: <slug>
outcome: <related-outcome-id>
type: slo|metric|qualitative
threshold: "<measurable threshold>"
---

## What this measures

## Why it matters

## How to collect it

## What action it should trigger
```

## Guardrail

Use when something must not happen again.

Write to `.oh/guardrails/<slug>.md`:

```markdown
---
id: <slug>
severity: candidate|soft|hard
statement: "<one-line constraint>"
outcome: <related-outcome-id>
---

## Constraint

## Rationale

## Override protocol

Who can override it, under what evidence, and where the override is recorded.
```

## Outcome update

Use when status, mechanism, or affected files changed for an existing outcome.

Edit `.oh/outcomes/<slug>.md`:

```markdown
---
id: <slug>
status: proposed|active|paused|complete|retired
mechanism: "<current mechanism>"
files:
  - <path-or-area>
---

## Update

What changed?

## Evidence

What proves the status, mechanism, or file list changed?

## Next decision

What should happen next, and when should this outcome be revisited?
```

## ADR

Use when a decision constrains future architecture.

Write to `docs/ADRs/<NNN>-<slug>.md`:

```markdown
---
id: <NNN>-<slug>
status: proposed|implementing|implemented|superseded
validate:
  tests:
    - <exact test or command if available>
---

# <Decision Title>

## Context

## Decision

## Consequences

## Validation
```
