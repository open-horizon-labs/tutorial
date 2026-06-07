# Problem Space

Problem space maps the terrain before the agent chooses a fix.

The same symptom can point to different terrain:

- a one-line bug;
- a missing regression test;
- unclear ownership;
- a boundary that lacks an invariant;
- a system design that keeps producing the same failure.

Those are different maps. A problem statement comes next and chooses the slice.

## Learn

Problem-space work answers, “What is going on?”

Map:

- systems involved;
- users, maintainers, operators, or reviewers affected;
- repeated symptoms;
- hard constraints;
- soft constraints;
- assumed constraints to test;
- existing evidence and missing evidence;
- blast radius if wrong;
- prior attempts or abandoned fixes.

Terrain mapping explains what the implementation is for before the agent starts proposing fixes.

## Why real terrain matters

A one-file exercise is often too shallow. The obvious task is the correct task. There is no real reason to use `/problem-space` or `/problem-statement` beyond ceremony.

A real project has constraints that change the right solution level:

- test coverage;
- CI speed;
- release pressure;
- migration risk;
- downstream users;
- architecture boundaries;
- ownership;
- prior failed fixes;
- reviewer capacity;
- data or security risk.

Those constraints determine whether the right next move is Band-Aid, Local Optimum, Reframe, or Redesign.

## Practice

Create a problem-space map before selecting a problem statement.

Include:

- relevant systems and interfaces;
- affected users, maintainers, operators, and reviewers;
- repeated symptoms and known triggers;
- constraints and assumptions;
- existing evidence and missing evidence;
- prior attempts;
- blast radius if the map is wrong.

Then hand the map to [`problem-statement.md`](problem-statement.md), where you choose the slice for this run.

## Artifact

```text
problem-space map
```

## What Good Looks Like

```md
Systems involved:
- notification event ingestion
- reminder scheduler
- send boundary
- duplicate-skip recording

Repeated symptom:
- duplicate reminders can reach the same recipient when trigger paths overlap.

Constraints:
- do not change notification copy or timing policy in this slice;
- the fix must be reviewable with a same-recipient, same-idempotency-key regression check.

Assumptions to test:
- more than one trigger path can reach the send boundary;
- duplicate prevention belongs at the send boundary, not each caller.
```

## Review check

Reject the map if:

- it only restates the symptom;
- it hides affected maintainers or users;
- it treats assumed constraints as facts;
- it omits blast radius;
- it gives [`problem-statement.md`](problem-statement.md) no basis for choosing a slice.

## Go deeper

- [`docs/context-construction.md`](context-construction.md) — what context must exist before problem-space mapping is useful.
- [`docs/problem-statement.md`](problem-statement.md) — narrowing terrain into one selected framing.
- [`docs/beyond-nearest-peak.md`](beyond-nearest-peak.md) — how the selected statement changes the solution altitude.
- [Documenting Strategy](https://muness.com/posts/documenting-strategy-lessons-from-leading-data-and-eng/) — keeping context, needs, strategy, and tactics connected.
- [Real-World Application of Strategic Clarity in Platform Leadership](https://muness.com/posts/real-world-application-of-strategic-clarity-in-platform-leadership/) — outcomes, ownership, updates, and feedback loops.
