# Context Construction

Context construction is the skill of deciding what the agent should know, what it should not assume, and what should survive the handoff.

More context is not automatically better. Useful context is selected, structured, provenance-backed, and small enough to govern.

## Learn

A context pack should answer:

- What is the task identity?
- What outcome is this work meant to move?
- What files, systems, or users are in scope?
- What constraints are hard, soft, or assumed?
- What prior attempts or landmines matter?
- What evidence already exists?
- What should trigger stop, dissent, or salvage?

This is where The Context Stack enters the curriculum. The agent should not infer strategy from a messy transcript. The human should construct a context object the agent and reviewer can inspect.

## Practice

Use `templates/context-pack.md`.

Build the pack before `/aim` or `/execute`:

1. Name the intent.
2. List relevant subsystems and files.
3. Separate hard constraints from soft constraints.
4. Mark assumptions that should be tested.
5. Add provenance for claims.
6. Add stop, dissent, and salvage triggers.

Keep the pack short enough that a reviewer can challenge it.

## Artifact

```text
context pack
```

The context pack should be reusable by:

- `/aim` to clarify outcome;
- `/problem-space` to map terrain;
- `/problem-statement` to choose the slice;
- `/solution-space` to compare solution levels;
- `/execute` to avoid guessing;
- `/review` and `/dissent` to check drift.

## Review check

Reject a context pack if:

- it hides provenance;
- it dumps files without explaining why they matter;
- constraints are mixed with preferences;
- it contains unverified claims as facts;
- it does not name stop conditions;
- the agent would still need to infer the actual task.

## Go deeper

- [The Context Stack](https://muness.com/posts/the-context-stack/) — context as governed memory, provenance, task identity, and promotion path.
- [`templates/context-pack.md`](../templates/context-pack.md) — starting point for the artifact.
- [`docs/prompt-and-context.md`](prompt-and-context.md) — how to turn the context pack into a checkable prompt.
- [`docs/context-to-agent-tutorial.md`](context-to-agent-tutorial.md) — guided path from context pack to prompt, skill, and subagent.
- [`docs/open-horizons.md`](open-horizons.md) — where the context pack sits in the full loop.


---

## Navigation

- Previous: [Model-Fit Framing](model-fit.md)
- Up: [Docs Home](index.md) / [Curriculum](curriculum.md)
- Next: [Prompt and Context Assembly](prompt-and-context.md)
