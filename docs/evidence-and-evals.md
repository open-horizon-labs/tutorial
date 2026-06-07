# Evidence and Evals

Evidence is the boundary between useful agent work and polished guessing.

Define evidence before delegation. If the check is invented after the patch, it will often prove the patch instead of the behavior.

## Learn

Evidence can be:

- regression tests;
- integration tests;
- static checks;
- build or migration checks;
- manual reproduction steps;
- review criteria;
- deleted duplicate paths;
- production-like probes;
- explicit residual risk.

A useful check is specific enough to fail on the old behavior.

Weak:

```md
The notification system should be cleaner.
```

Better:

```md
Given two identical notification events with the same idempotency key, the system sends one notification and records the duplicate as skipped.
```

## Practice

Use `templates/eval-checklist.md` before `/execute`.

For each selected solution level, ask:

- What old behavior should fail now?
- What invariant should hold?
- What edge cases matter?
- What command or reproduction proves it?
- What would make the check misleading?
- Where would mocks hide production behavior?
- What residual risk remains after checks pass?

## Artifact

```text
evidence checklist
```

The checklist should travel into the agent brief and review.

## Review check

Reject evidence if:

- it only checks implementation details;
- it relies on mocks where production behavior matters;
- it cannot fail on the old behavior;
- it ignores the selected solution level;
- it omits a manual check when automation is not practical;
- it treats the agent's confidence as proof.

## Go deeper

- [`templates/eval-checklist.md`](../templates/eval-checklist.md) — evidence template used by the tutorial.
- [Phoenix Iterative Evaluation & Experimentation Workflow](https://arize.com/docs/phoenix/cookbook/ai-engineering-workflows/iterative-evaluation-and-experimentation-workflow-python) — deeper eval workflow when software tests are not enough.
- [Dissent Mode](https://muness.com/posts/dissent-mode/) — why passing checks still deserves adversarial review.


---

## Navigation

- Previous: [Beyond the Nearest Peak](beyond-nearest-peak.md)
- Up: [Docs Home](index.md) / [Curriculum](curriculum.md)
- Next: [Agent Briefs](agent-briefs.md)
