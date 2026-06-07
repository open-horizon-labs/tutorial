# Strategy Clarity for Agent-Driven Project Improvement

An agent brief is a small strategy doc.

If it only says “fix this issue,” it is missing the mechanism. It should say why this approach should move the aim, what level of solution was selected, and what evidence will tell us if the patch is wrong.

## The four fields

| Field | Question | Technical-debt example |
|---|---|---|
| Aim | What outcome are we trying to create? | Make notification changes safer by eliminating one recurring duplicate-send path. |
| Mechanism | Why should this approach work? | Moving idempotency to the notification boundary prevents duplicate sends regardless of which upstream path emitted the event. |
| Feedback | What tells us quickly if we are wrong? | Regression test with duplicate events, integration test for the send path, review confirming no parallel send path remains. |
| Guardrail | What must not break? | Do not change user-visible notification content or delivery timing except duplicate suppression. |

That is enough strategy for one implementation slice.

More words do not help if the mechanism is missing.

## Include the solution level

Every brief should say which level was selected:

- Band-Aid;
- Local Optimum;
- Reframe;
- Redesign.

It should also say why the other levels were rejected.

Example:

```md
Selected level: Reframe.

We are not treating this as a one-off duplicate-send bug. The repeated symptom suggests notification ownership is unclear. The slice is to enforce idempotency at the notification boundary and add regression coverage there.

Rejected:
- Band-Aid: another guard in the caller would leave other trigger paths exposed.
- Full Redesign: replacing the event flow is too large for this review slice.
```

## Compose before execution

Before handing work to an agent, write down:

1. **Purpose** — why this improvement matters now.
2. **People** — who is affected: users, maintainers, operators, reviewers.
3. **Context** — files, constraints, existing behavior, known risks, prior attempts.
4. **Approach** — the selected solution level and causal bet.
5. **Tactics** — files, tests, commands, review checks.

For a technical-debt slice:

```text
Purpose: reduce repeated duplicate notifications without changing notification content.
Context: duplicate sends have appeared in multiple caller paths; tests only cover happy-path send behavior.
Approach: enforce idempotency at the notification boundary, not in each caller.
Tactics: map send paths, add regression test, update boundary logic, run notification test suite, review for parallel paths.
```

## Make it reviewable

The brief should be short enough to use and specific enough to reject.

The agent and reviewer should both be able to answer:

- What are we trying to change?
- Why this level of solution?
- What did we explicitly not choose?
- What examples define correctness?
- What would prove this wrong?
- Where should the agent stop instead of guessing?

## Alignment check

Use these four checks before accepting the brief or patch:

| Check | Question |
|---|---|
| Necessity | Is this needed for the aim above it? |
| Viability | Is this a plausible way to get there? |
| Sufficiency | Is a key piece missing? |
| Connectedness | Does every tactic connect back to the aim and mechanism? |

If a file, test, or instruction does not connect back, remove it. If the mechanism is missing, do not move faster. Clarify it.

## Why this matters

Agents make execution cheap. Cheap execution makes misalignment expensive.

If the aim, mechanism, feedback, guardrails, and selected solution level are explicit, speed helps. If they are implicit, the agent can produce a lot of polished wrong work quickly.

The brief is the alignment mechanism. Treat it that way.


## Exercise

Rewrite a vague task as a one-slice strategy doc:

```md
Aim:
Mechanism:
Feedback:
Guardrails:
Selected solution level:
Rejected levels:
Tactics:
```

Then remove any tactic that does not connect back to aim and mechanism.

## Go deeper

- [Alignment Is the Constraint](https://muness.com/posts/alignment-is-the-constraint/) — aim, mechanism, feedback, and guardrails before speed.
- [Documenting Strategy](https://muness.com/posts/documenting-strategy-lessons-from-leading-data-and-eng/) — connected strategy artifacts and tactics.
- [Real-World Application of Strategic Clarity in Platform Leadership](https://muness.com/posts/real-world-application-of-strategic-clarity-in-platform-leadership/) — outcomes, updates, feedback, and ownership.
- [`docs/agent-briefs.md`](agent-briefs.md) — applying strategy clarity to an agent brief.
