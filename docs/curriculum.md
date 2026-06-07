# Curriculum

This repo teaches a curriculum of practical skills an LLM developer should know, then applies the Open Horizons philosophy corpus to those skills.

The spine is:

```text
Intent → Problem framing → Solution search → Evidence → Delegation → Verification → Dissent → Knowledge extraction → Salvage
```

That spine only becomes real when the learner can operate the tools that preserve it:

- **Intent Engineering** gives the rhythm: clarify intent, burst, pause, structure, iterate.
- **Open Horizons skills** turn the rhythm into phase gates the agent can follow.
- **Context packs** turn selective context into a reusable handoff.
- **Authored skills** turn local know-how into reusable procedures.
- **Subagents** turn role boundaries into bounded workers with scoped tools and isolated context.
- **Evidence and evals** keep the work in contact with reality.
- **Knowledge extraction** turns review, dissent, and salvage into durable `.oh/` artifacts instead of another lost chat.

## How to use this curriculum

Use four passes:

1. **Overview pass** — read the table below and understand the skill sequence.
2. **Deep-dive pass** — read the linked module only when that skill is the bottleneck.
3. **Reference pass** — follow the module's Go deeper links when you need source material or official mechanics.
4. **Application pass** — use `docs/tutorial.md` to apply the full loop to a real project slice.

Each module has an artifact. The artifact is how the learning survives long enough for another skill, subagent, or reviewer to use it.

## Overview curriculum

| Module | Learner can do this | Artifact | Deep dive | Go deeper |
|---|---|---|---|---|
| 1. Intent Engineering | State a real intent, use the model for bursts, pause before commitment, and preserve the current understanding. | Intent note. | [`intent-engineering.md`](intent-engineering.md) | [Intent Engineering](https://muness.com/posts/intent-engineering/); [Alignment Is the Constraint](https://muness.com/posts/alignment-is-the-constraint/). |
| 2. Context construction | Build a selective context pack with provenance, constraints, landmines, and stop triggers. | Context pack. | [`context-construction.md`](context-construction.md) | [The Context Stack](https://muness.com/posts/the-context-stack/). |
| 3. Open Horizons phase skills | Use `/aim`, `/problem-space`, `/problem-statement`, `/solution-space`, `/execute`, `/review`, `/dissent`, and `/salvage` as gates. | Session artifacts. | [`open-horizons.md`](open-horizons.md) | [Open Horizons](https://muness.com/posts/open-horizons/); [Open Horizons Skills](https://github.com/open-horizon-labs/skills). |
| 4. Problem framing | Map terrain, separate symptoms from constraints, and choose a problem statement. | Problem-space map and problem statement. | [`problem-space.md`](problem-space.md) | [Documenting Strategy](https://muness.com/posts/documenting-strategy-lessons-from-leading-data-and-eng/); [Real-World Strategic Clarity](https://muness.com/posts/real-world-application-of-strategic-clarity-in-platform-leadership/). |
| 5. Solution search | Generate multiple solution levels and reject the nearest plausible patch. | Solution-space comparison with selected level. | [`beyond-nearest-peak.md`](beyond-nearest-peak.md) | [Beyond the Nearest Peak](https://muness.com/posts/beyond-the-nearest-peak/). |
| 6. Evidence | Define checks before implementation. | Evidence checklist. | [`evidence-and-evals.md`](evidence-and-evals.md) | [Phoenix eval workflow](https://arize.com/docs/phoenix/cookbook/ai-engineering-workflows/iterative-evaluation-and-experimentation-workflow-python); [Dissent Mode](https://muness.com/posts/dissent-mode/). |
| 7. Agent brief | Turn aim, mechanism, feedback, guardrails, and selected level into execution context. | Agent brief. | [`agent-briefs.md`](agent-briefs.md) | [`strategy-clarity.md`](strategy-clarity.md); [Alignment Is the Constraint](https://muness.com/posts/alignment-is-the-constraint/). |
| 8. Skill authoring | Encode repeated project procedures as `SKILL.md` files. | Project skill. | [`authoring-skills.md`](authoring-skills.md) | [Claude Code Skills](https://code.claude.com/docs/en/skills). |
| 9. Subagent authoring | Encode specialized roles as subagents with input contracts and tool limits. | Project subagent. | [`subagents.md`](subagents.md) | [Claude Code Subagents](https://code.claude.com/docs/en/sub-agents). |
| 10. Execution | Delegate one bounded implementation slice and detect drift. | Patch or stopped execution report. | [`execution-review-salvage.md`](execution-review-salvage.md#execute) | [`/execute`](skill://execute); [The Salvage Loop](https://muness.com/posts/the-salvage-loop-keep-learning-drop-the-code/). |
| 11. Verification and review | Check the work against evidence and aim, not the agent's summary. | Review findings. | [`execution-review-salvage.md`](execution-review-salvage.md#review) | [`/review`](skill://review); [Dissent Mode](https://muness.com/posts/dissent-mode/). |
| 12. Dissent | Stress the accepted-looking answer before committing. | Dissent memo. | [`execution-review-salvage.md`](execution-review-salvage.md#dissent) | [Dissent Mode](https://muness.com/posts/dissent-mode/). |
| 13. Knowledge extraction | Record metis, signals, guardrails, outcome updates, or ADRs that should survive the session. | `.oh/` artifact or ADR. | [`knowledge-extraction.md`](knowledge-extraction.md) | [`record` artifact shape](knowledge-extraction.md); [The Context Stack](https://muness.com/posts/the-context-stack/). |
| 14. Salvage | Keep the learning and restart smaller when the run drifts. | Salvage note and restart plan. | [`execution-review-salvage.md`](execution-review-salvage.md#salvage) | [The Salvage Loop](https://muness.com/posts/the-salvage-loop-keep-learning-drop-the-code/). |

## Open Horizons corpus applied

| Source | Curriculum use |
|---|---|
| Intent Engineering | Teaches the operating rhythm: clarify intent, burst, pause, structured pass, iterate. |
| Open Horizons | Turns the rhythm into Aim / Do / Reflect and nested feedback loops. |
| Alignment Is the Constraint | Requires every task, skill, subagent, and eval to carry aim, mechanism, feedback, and guardrail. |
| Documenting Strategy | Treats artifacts as connected strategy/tactics, not notes. Every tactic should be necessary, viable, sufficient, and connected. |
| Real-World Strategic Clarity | Keeps outcomes, mechanisms, satisfaction criteria, and running logs tied together. |
| Beyond the Nearest Peak | Teaches solution search: shallow breadth, score, select, deepen. Do not accept the first plausible patch. |
| The Context Stack | Teaches context governance: task identity, decision logs, provenance, guardrails, promotion paths, and agent-spawn forecasting. |
| Dissent Mode | Teaches managed contradiction: dissent memos, safe-to-fail probes, stop-the-line triggers, and review that can change the decision. |
| The Salvage Loop | Teaches that the code draft is disposable and the learning is the asset. |

## Why skills, subagents, and extraction are in the curriculum

A phase name is not enough.

`Intent → ... → Salvage` becomes useful only when the learner can preserve behavior across sessions and agents.

Skills preserve **procedures**:

- how to frame a project slice;
- how to compare solution levels;
- how to write a reviewable brief;
- how to run a fragile project-specific check;
- how to salvage a failed run without keeping the bad patch.

Subagents preserve **roles**:

- independent reviewer;
- codebase scout;
- test-gap hunter;
- migration planner;
- release checker;
- domain-specific validator;
- knowledge extractor.

Knowledge extraction preserves **learning**:

- metis: what we learned from doing the work;
- signal: what measurement tells us the outcome is moving;
- guardrail: what must not happen again;
- outcome update: what changed in status, mechanism, or affected files;
- ADR: what architectural decision now constrains future work.

The skill tells the agent what workflow to follow. The subagent controls whose eyes are on the work, what context they receive, and what tools they are allowed to use. The knowledge artifact decides what should survive after the session ends.

## Capstone

The learner improves one real project slice and leaves behind:

- an intent note;
- a context pack;
- problem-space and problem-statement artifacts;
- a solution-level comparison;
- evidence checks;
- an agent brief;
- a project skill encoding one reusable procedure;
- a subagent encoding one independent role;
- a patch or stopped execution report;
- review and dissent findings;
- one durable knowledge artifact;
- a salvage note if the run drifted.

The project should be easier to work on next time because the procedure, role boundary, and learning survived the session.
