# Execution, Review, Dissent, and Salvage

Execution is the inner loop. Review closes it. Dissent stress-tests it. Salvage preserves learning when the run drifts.

Execution keeps speed aligned: build the selected slice, check it against the brief, and stop when the work drifts.

## Execute

Before editing, run a pre-flight check:

```text
Aim clear?
Constraints known?
Context loaded?
Scope bounded?
Success criteria defined?
```

During execution:

1. Make the smallest coherent change for the selected solution level.
2. Add or update evidence.
3. Run the relevant checks.
4. Watch for drift.
5. Stop if the brief is wrong.

Drift signals:

- scope is expanding;
- files outside the plan keep appearing;
- “while I am here” work is accumulating;
- approach has changed direction more than once;
- tests are being bent to fit the patch;
- the agent is protecting code it already wrote.

## Review

Review the work against the aim and brief, not the agent's summary.

Ask:

- Is it still necessary?
- Is it still aligned?
- Is it sufficient without overbuilding?
- Is the mechanism clear?
- Are ripple effects complete?

A clean review still names residual risk.

## Dissent

Dissent assumes the accepted-looking answer still fails.

Look for:

- the chosen solution level was too low or too high;
- the symptom moved elsewhere;
- checks prove implementation, not behavior;
- role boundaries blurred;
- a new parallel path was introduced;
- production conditions are not represented by tests;
- future maintainers will misunderstand the boundary.

Dissent must be allowed to change the decision. Otherwise it is theater.

## Salvage

Salvage when the run is no longer converging.

Keep:

- better problem statement;
- constraints discovered;
- rejected solution paths;
- checks that should survive;
- role boundaries that mattered;
- knowledge artifact candidates;
- smaller restart plan.

Drop the draft if keeping it makes the system worse.

## Artifact

```text
execution report → review findings → dissent memo → salvage note if needed
```

## Review check

Reject the execution run if:

- pre-flight cannot state the aim;
- the patch ignores the selected solution level;
- checks were weakened or invented after the fact;
- review relies on the implementer's explanation;
- dissent cannot name a real possible failure;
- salvage preserves code only because time was spent on it.

## Go deeper

- [`skill://execute`](skill://execute) — pre-flight, build, drift detection, salvage trigger.
- [`skill://review`](skill://review) — alignment checks and drift decision.
- [Dissent Mode](https://muness.com/posts/dissent-mode/) — managed contradiction before acceptance.
- [The Salvage Loop](https://muness.com/posts/the-salvage-loop-keep-learning-drop-the-code/) — keep the learning, drop the bad draft.


---

## Navigation

- Previous: [Authoring Subagents](subagents.md)
- Up: [Tutorial](tutorial.md) / [Curriculum](curriculum.md)
- Next: [Knowledge Extraction](knowledge-extraction.md)
