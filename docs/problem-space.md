# Problem Framing

Problem framing is the skill of choosing what problem the agent is allowed to solve.

The same symptom can point to different problems:

- a one-line bug;
- a missing regression test;
- unclear ownership;
- a boundary that lacks an invariant;
- a system design that keeps producing the same failure.

Those are not the same task.

## Learn

Problem-space work maps terrain before choosing a solution.

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

The goal is not implementation advice. The goal is to understand what the implementation would be for.

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

Create a problem-space map before selecting a solution.

Then write three problem statements:

1. symptom framing;
2. systems framing;
3. user or maintainer outcome framing.

Example:

```md
Symptom framing: Notifications sometimes send twice.
Systems framing: Notification ownership is split across multiple trigger paths, so no single layer enforces idempotency.
Maintainer framing: Engineers cannot safely add notification behavior because the current flow does not make ownership or duplicate prevention obvious.
```

For each framing, name:

- what it improves;
- what it hides;
- what solution shapes it makes likely;
- what evidence would show the framing is wrong.

## Artifact

```text
problem-space map
selected problem statement
```

## Review check

Reject the framing if:

- it only restates the symptom;
- it hides affected maintainers or users;
- it treats assumed constraints as facts;
- it points to only one solution level before `/solution-space`;
- it does not name evidence that could prove the framing wrong.

## Go deeper

- [`docs/context-construction.md`](context-construction.md) — what context must exist before problem framing is useful.
- [`docs/beyond-nearest-peak.md`](beyond-nearest-peak.md) — how problem framing changes the solution altitude.
- [Documenting Strategy](https://muness.com/posts/documenting-strategy-lessons-from-leading-data-and-eng/) — keeping context, needs, strategy, and tactics connected.
- [Real-World Application of Strategic Clarity in Platform Leadership](https://muness.com/posts/real-world-application-of-strategic-clarity-in-platform-leadership/) — outcomes, ownership, updates, and feedback loops.
