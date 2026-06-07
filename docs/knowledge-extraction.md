# Knowledge Extraction

Knowledge extraction is how the session stops being a one-off.

Review, dissent, and salvage produce raw learning. If that learning stays in chat, the next run starts cold. If it becomes hidden memory without review, it becomes unaccountable policy.

The useful middle is a durable, inspectable artifact.

## What to record

Use the smallest artifact that changes future behavior.

| Artifact | Use when | Writes to |
|---|---|---|
| Metis | You learned a situated pattern that should inform future work. | `.oh/metis/<slug>.md` |
| Signal | You found a measurement that indicates movement or risk. | `.oh/signals/<slug>.md` |
| Guardrail | Something must not happen again. | `.oh/guardrails/<slug>.md` |
| Outcome update | Status, mechanism, or affected files changed. | `.oh/outcomes/<slug>.md` |
| ADR | A decision now constrains future architecture. | `docs/ADRs/<NNN>-<slug>.md` |

This follows the shape of the RNA `record` skill: metis, signal, guardrail, outcome update, and ADR.

## Meeting notes: summary is not the finish line

A transcript summary can still leave the organization confused. It may list topics and action items while missing the thing that matters: how the conversation changes aims, projects, guardrails, risks, decisions, and future work.

Model-fit framing gets the notes grounded. Knowledge extraction decides what survives after the meeting note has done its immediate job.

Start with the grounded note from [`docs/model-fit.md`](model-fit.md):

```text
transcript
attendees and roles
active aims, projects, programs, and customer commitments
company vocabulary
prior decisions
known guardrails and risks
desired output artifact
```

Then extract only the pieces that should affect future work:

| Meeting note content | Durable artifact | Why it survives |
|---|---|---|
| “We decided the onboarding assistant should not answer entitlement questions until the permission boundary is in place.” | ADR or guardrail | Future implementation must respect the boundary. |
| “Customer-success notes show three teams asking for the same post-meeting project summary.” | Signal | The demand pattern can be measured across accounts or meetings. |
| “The model confused program names when the transcript lacked project context.” | Metis | Future note generation should require project vocabulary and active aims. |
| “The roadmap outcome now depends on the meeting-notes extractor.” | Outcome update | The outcome's mechanism or affected files changed. |
| “Someone should check whether Zoom summaries are good enough.” | Usually no durable artifact yet | It is an open question until evidence or a decision exists. |

The extraction pass keeps meeting notes tied to the big picture. A shallow note says what people talked about. A useful extracted artifact says what changed, what should constrain future work, and what evidence supports that change.

## What not to record

Do not record:

- generic advice;
- things the model already knows;
- unverified claims;
- one-off preferences;
- stale assumptions;
- private or sensitive details that should not persist;
- rules nobody has agreed to enforce.

Memory without governance is a liability.

## Extraction questions

After review, dissent, or salvage, ask:

- What did we expect?
- What actually happened?
- Why did the difference matter?
- What future run should behave differently?
- Is this a pattern, signal, constraint, outcome update, or architectural decision?
- What evidence or provenance supports it?
- Who can retire or override it?

## Candidate to promoted artifact

Treat extraction as a promotion path:

```text
raw observation → candidate learning → reviewed artifact → future context
```

Not every observation deserves promotion.

A good metis artifact changes how a future agent acts. A good guardrail prevents a repeated failure. A good signal gives the next run reality contact. A good ADR names a decision that future code must respect.

## Example: code review learning

Raw observation:

```md
The agent fixed duplicate notifications by adding a guard in the failing caller. Review found two other caller paths that could still send duplicates.
```

Metis candidate:

```md
Duplicate-send bugs in this repo usually belong at the notification boundary, not individual caller paths. Caller guards suppress the visible symptom and leave parallel trigger paths exposed.
```

Guardrail candidate:

```md
Notification duplicate prevention must be enforced at the send boundary or a documented equivalent. Caller-specific duplicate guards are not sufficient unless the caller is the only possible send path and review verifies that boundary.
```

Signal candidate:

```md
A regression test that sends two events with the same idempotency key to the same recipient should produce one send and one duplicate-skip record.
```

## How this connects to the loop

| Loop step | Extraction question |
|---|---|
| Intent | What aim should future work inherit? |
| Problem framing | What constraint or landmine did we discover? |
| Solution search | Which rejected path should future agents avoid repeating? |
| Evidence | What check should become reusable? |
| Delegation | What role or tool boundary mattered? |
| Verification | What did review prove or fail to prove? |
| Dissent | What alternate failure mode remains live? |
| Salvage | What learning survives after dropping the draft? |

The learning is the asset. The artifact is how it survives.


## Exercise

After a review or salvage pass, write one candidate artifact:

1. Metis if the learning is a situated pattern.
2. Signal if the learning is a measurement.
3. Guardrail if the learning is a constraint.
4. Outcome update if status, mechanism, or affected files changed.
5. ADR if the learning constrains architecture.

Then ask whether a future agent should actually inherit it. When the answer is no, leave it as a note, not memory.

## Go deeper

- [`templates/knowledge-artifact.md`](../templates/knowledge-artifact.md) — templates for metis, signal, guardrail, outcome update, and ADR.
- [The Context Stack](https://muness.com/posts/the-context-stack/) — promotion paths, provenance, and context governance.
- [The Salvage Loop](https://muness.com/posts/the-salvage-loop-keep-learning-drop-the-code/) — why the learning can survive even when the code draft should not.
- [`docs/model-fit.md`](model-fit.md) — how to ground meeting notes before deciding what should become durable knowledge.
- [`docs/subagents.md`](subagents.md) — the knowledge extractor as a role boundary.


---

## Navigation

- Previous: [Execution, Review, Dissent, and Salvage](execution-review-salvage.md)
- Up: [Docs Home](index.md) / [Curriculum](curriculum.md)
- Next: [Further Reading](further-reading.md)
