# Strategy Clarity for Coding With Agents

An agent brief is a small strategy doc.

If it only says what to build, it is missing the mechanism. It should say why this approach should work and what signal will tell us if we are fooling ourselves.

## The four fields

| Field | Question | Base62 example |
|---|---|---|
| Aim | What outcome are we trying to create? | Learn to direct and judge agent-written code. |
| Mechanism | Why should this approach work? | A behavior contract plus evals gives the agent a target and gives the human a rejection test. |
| Feedback | What tells us quickly if we are wrong? | Known examples, invalid-input tests, round trips, and review findings. |
| Guardrail | What must not break? | Do not accept plausible code without checks. Do not add unrelated features. |

That is enough strategy for this task.

More words do not help if the mechanism is missing.

## Compose before you send

Before handing work to an agent, write down:

1. **Purpose** — why this work exists.
2. **People** — who benefits, who maintains it, and whose judgment matters.
3. **Context** — files, constraints, examples, prior decisions, known risks.
4. **Approach** — the bet you are making.
5. **Tactics** — files, tests, commands, and review checks.

For base62:

```text
Purpose: practice directing agents without surrendering judgment.
Context: small Python package, fixed base62 alphabet, tests required.
Approach: define behavior first, turn it into evals, then implement.
Tactics: create base62.py, create pytest/Hypothesis tests, run uv run pytest, review against the contract.
```

## Make it usable

A strategy doc that nobody uses is decoration. The brief should be short enough to paste and specific enough to review.

The agent and the human should both be able to answer:

- What are we trying to change?
- Why should this approach work?
- What is out of scope?
- What examples define correctness?
- What would prove this wrong?
- Where should the agent stop instead of guessing?

## Alignment check

Use these four checks before accepting the brief or the code:

| Check | Question |
|---|---|
| Necessity | Is this needed for the aim above it? |
| Viability | Is this a plausible way to get there? |
| Sufficiency | Is a key piece missing? |
| Connectedness | Does every tactic connect back to the aim and mechanism? |

If a test, file, or instruction does not connect back, remove it. If the mechanism is missing, do not move faster. Clarify it.

## Why this matters

Agents make execution cheap. Cheap execution makes misalignment expensive.

If the aim, mechanism, feedback, and guardrails are explicit, speed helps. If they are implicit, the agent can produce a lot of polished wrong work quickly.

The brief is the alignment mechanism. Treat it that way.
