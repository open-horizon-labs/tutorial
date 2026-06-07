# Agent Briefs

An agent brief turns a selected solution into bounded execution.

It carries aim, mechanism, feedback, guardrails, scope, checks, and stop conditions in one artifact.

## Learn

A useful brief contains:

- aim;
- selected problem statement;
- selected solution level;
- rejected solution levels;
- mechanism;
- feedback signal;
- guardrails;
- context to inspect first;
- behavior contract;
- commands and checks;
- explicit non-goals;
- stop conditions;
- review criteria.

The brief should make it possible to reject a plausible patch.

## Practice

Use `templates/agent-brief.md` after `/solution-space` and the evidence checklist.

Before giving it to `/execute`, ask:

- Does every tactic connect to the aim?
- Is the causal mechanism stated plainly?
- Are rejected solution levels named?
- Are checks tied to behavior, not implementation details?
- Does the agent know where to stop instead of guessing?
- Could a reviewer use this brief without reading the whole conversation?

## Artifact

Use `templates/agent-brief.md` and produce a brief with this shape:

```text
Purpose
Aim
Problem statement
Selected solution level
Rejected solution levels
Mechanism / feedback / guardrails
Context to inspect first
Behavior contract
Commands and acceptance checks
Old behavior the checks should catch
Stop conditions
Review checklist
```

The brief is consumed by `/execute`, `/review`, `/dissent`, and knowledge extraction. A reviewer should be able to reject the work using only this artifact plus the diff.

## Review check

Reject a brief if:

- it only says what to edit;
- it omits mechanism;
- it hides why other solution levels were rejected;
- it lacks commands or acceptance checks;
- it does not name non-goals;
- it gives the agent permission to expand scope silently.

## Go deeper

- [`templates/agent-brief.md`](../templates/agent-brief.md) — handoff template.
- [`docs/strategy-clarity.md`](strategy-clarity.md) — aim, mechanism, feedback, guardrail, and solution level.
- [Alignment Is the Constraint](https://muness.com/posts/alignment-is-the-constraint/) — why speed without alignment creates more wrong work faster.
- [Documenting Strategy](https://muness.com/posts/documenting-strategy-lessons-from-leading-data-and-eng/) — why artifacts should connect vision, needs, strategy, tactics, and evidence.


---

## Navigation

- Previous: [Evidence and Evals](evidence-and-evals.md)
- Up: [Docs Home](index.md) / [Curriculum](curriculum.md)
- Next: [Strategy Clarity](strategy-clarity.md)
