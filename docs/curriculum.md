# Curriculum

This curriculum is for builders using LLMs inside existing systems, where there are real constraints, real tests, real maintenance risk, and more than one plausible answer.

The failure mode is familiar: the model produces a decent-looking patch, the chat summary sounds confident, and nobody can tell whether the work actually served the aim. Intent was vague. Context was dumped instead of selected. Evidence came after implementation, if it came at all. Review became vibes. Dissent arrived too late. The next session has to rediscover everything.

The curriculum teaches the main path and the checks that can interrupt it:

| Mode | What happens |
|---|---|
| Grounding | State intent, fit the work to the model, and build selected context. |
| Framing | Map problem space, choose the problem statement, and compare solution levels. |
| Execution | Write evidence, delegate the slice, and build only what the brief allows. |
| Learning | Extract durable knowledge after meaningful work. |
| Anytime checks | Invoke review for correctness, dissent for fragile assumptions, and salvage when drift appears. |

That loop only becomes useful when the learner can preserve the decisions that matter:

- **Intent Engineering** states the behavior change before asking for output, then uses burst/pause/review instead of a single prompt-and-pray pass.
- **Model-fit framing** turns a vague ask into work the model can actually do: transform supplied context, compare options, critique against criteria, or expose missing context.
- **Open Horizons skills** make each phase a gate: what is allowed to move forward, what must stop, and what evidence would change the decision.
- **Context packs** select the project facts a future agent or reviewer needs, with provenance, constraints, landmines, and stop triggers.
- **Prompt and context assembly** combines the intent note, model-fit note, context pack, output contract, and reviewer checks into one request the model can answer without guessing.
- **Problem statements** narrow the terrain into one selected slice, rejected alternatives, and an invalidation signal.
- **Authored skills** capture a repeated local procedure only after the work shows it is worth preserving.
- **Subagents** create bounded roles when the work needs independent eyes, narrower tools, or isolated context.
- **Evidence and evals** define the trace, test, reviewer question, or runtime check before implementation starts.
- **Knowledge extraction** records the metis, signal, guardrail, outcome update, or ADR that a later session can actually consume.

## How to use this curriculum

Use four passes. Do not turn them into homework for its own sake.

1. **Overview pass** — read the table below and understand the sequence of decisions.
2. **Deep-dive pass** — read the linked module when that skill is the active bottleneck.
3. **Reference pass** — follow Go deeper links when you need source material, official mechanics, or a sharper model.
4. **Application pass** — use `docs/tutorial.md` to apply the loop to one real project slice.

A good artifact is not a note-shaped souvenir. It preserves at least one decision, one assumption or evidence check, and the next consumer: another skill, subagent, reviewer, maintainer, or future session. If an artifact cannot do that, shrink it or merge it.

## Overview curriculum

| Module | Learner can do this | Artifact | Deep dive | Go deeper |
|---|---|---|---|---|
| 1. Intent Engineering | Name the behavior change, use the model for a short burst, pause before commitment, and preserve the current understanding. | Intent note. | [`intent-engineering.md`](intent-engineering.md) | [Intent Engineering](https://muness.com/posts/intent-engineering/); [Alignment Is the Constraint](https://muness.com/posts/alignment-is-the-constraint/). |
| 2. Model-fit framing | Reframe the ask so the model transforms supplied context instead of guessing missing facts. | Model-fit note. | [`model-fit.md`](model-fit.md) | [LLM Prompt Types](https://muness.com/posts/llm-prompt-types/); [Anthropic context engineering](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents). |
| 3. Context construction | Build a selective context pack with provenance, constraints, landmines, and stop triggers instead of dumping the repo. | Context pack. | [`context-construction.md`](context-construction.md) | [The Context Stack](https://muness.com/posts/the-context-stack/). |
| 4. Open Horizons phase skills | Use `/aim`, `/problem-space`, `/problem-statement`, `/solution-space`, `/execute`, `/review`, `/dissent`, and `/salvage` as gates that decide whether work may continue, stop, narrow, or restart. | Session artifacts. | [`open-horizons.md`](open-horizons.md) | [Open Horizons](https://muness.com/posts/open-horizons/); [Open Horizons Skills](https://github.com/open-horizon-labs/skills). |
| 5. Problem space (`/problem-space`) | Map terrain: systems, stakeholders, constraints, assumptions, evidence, and blast radius. | Problem-space map. | [`problem-space.md`](problem-space.md) | [Documenting Strategy](https://muness.com/posts/documenting-strategy-lessons-from-leading-data-and-eng/); [Real-World Strategic Clarity](https://muness.com/posts/real-world-application-of-strategic-clarity-in-platform-leadership/). |
| 6. Problem statement (`/problem-statement`) | Narrow the map to one selected framing, name rejected framings, and define the evidence that would prove the framing wrong. | Selected problem statement. | [`problem-statement.md`](problem-statement.md) | [`problem-space.md`](problem-space.md); [Documenting Strategy](https://muness.com/posts/documenting-strategy-lessons-from-leading-data-and-eng/). |
| 7. Solution search (`/solution-space`) | Generate multiple solution levels, score them against the aim, and reject the nearest plausible patch when it does not change the failure mode. | Solution-space comparison with selected level. | [`beyond-nearest-peak.md`](beyond-nearest-peak.md) | [Beyond the Nearest Peak](https://muness.com/posts/beyond-the-nearest-peak/). |
| 8. Evidence | Define checks before implementation, including the tempting patch that should fail if the problem is deeper. | Evidence checklist. | [`evidence-and-evals.md`](evidence-and-evals.md) | [Phoenix eval workflow](https://arize.com/docs/phoenix/cookbook/ai-engineering-workflows/iterative-evaluation-and-experimentation-workflow-python); [Dissent Mode](https://muness.com/posts/dissent-mode/). |
| 9. Agent brief | Turn aim, mechanism, feedback, guardrails, and selected solution level into an execution contract. | Agent brief. | [`agent-briefs.md`](agent-briefs.md) | [`strategy-clarity.md`](strategy-clarity.md); [Alignment Is the Constraint](https://muness.com/posts/alignment-is-the-constraint/). |
| 10. Skill authoring | Author a `SKILL.md` when the current project exposes a repeated procedure worth preserving. | Project skill. | [`authoring-skills.md`](authoring-skills.md) | [Claude Code Skills](https://code.claude.com/docs/en/skills). |
| 11. Subagent authoring | Author a specialized role when the work needs independent judgment, scoped tools, or isolated context. | Project subagent. | [`subagents.md`](subagents.md) | [Claude Code Subagents](https://code.claude.com/docs/en/sub-agents). |
| 12. Execution (`/execute`) | Delegate one bounded implementation slice, keep the stop triggers visible, and detect drift before it compounds. | Patch or stopped execution report. | [`execution-review-salvage.md`](execution-review-salvage.md#execute) | [`/execute`](skill://execute); [The Salvage Loop](https://muness.com/posts/the-salvage-loop-keep-learning-drop-the-code/). |
| 13. Verification and review (`/review`) | Check the work against evidence and aim, not the agent's summary or your desire for the patch to be done. | Review findings. | [`execution-review-salvage.md`](execution-review-salvage.md#review) | [`/review`](skill://review); [Dissent Mode](https://muness.com/posts/dissent-mode/). |
| 14. Dissent (`/dissent`) | Stress the accepted-looking answer, name the assumption that could break, and decide whether to proceed, adjust, or reconsider. | Dissent memo. | [`execution-review-salvage.md`](execution-review-salvage.md#dissent) | [Dissent Mode](https://muness.com/posts/dissent-mode/). |
| 15. Knowledge extraction | Record the metis, signal, guardrail, outcome update, or ADR that should constrain the next run. | `.oh/` artifact or ADR. | [`knowledge-extraction.md`](knowledge-extraction.md) | [`record` artifact shape](knowledge-extraction.md); [The Context Stack](https://muness.com/posts/the-context-stack/). |
| 16. Salvage (`/salvage`) | Keep the learning and restart smaller when the run drifts, instead of defending the bad patch because it almost works. | Salvage note and restart plan. | [`execution-review-salvage.md`](execution-review-salvage.md#salvage) | [The Salvage Loop](https://muness.com/posts/the-salvage-loop-keep-learning-drop-the-code/). |

## Cross-curriculum slice

| Slice | Combines | Artifact | Deep dive |
|---|---|---|---|
| Prompt and context assembly | Intent Engineering, Model-fit framing, Context construction, and Evidence | Prompt assembly. | [`prompt-and-context.md`](prompt-and-context.md) |

## Open Horizons corpus applied

| Source | Curriculum use |
|---|---|
| Intent Engineering | Produces an intent note that can survive a burst, pause, structured pass, and review. |
| LLM Prompt Types | Separates model-suited transformations from brittle retrieval or closed-ended asks, then pairs the ask with context and evaluation criteria. |
| Open Horizons | Turns Aim / Do / Reflect into nested feedback loops, so every phase knows what signal it is preserving. |
| Alignment Is the Constraint | Requires every task, skill, subagent, and eval to carry aim, mechanism, feedback, and guardrail before speed can help. |
| Documenting Strategy | Treats artifacts as connected strategy and tactics, not loose notes. Every tactic should be necessary, viable, sufficient, and connected. |
| Real-World Strategic Clarity | Keeps outcomes, mechanisms, satisfaction criteria, and running logs tied together so the work can be checked later. |
| Beyond the Nearest Peak | Makes solution search observable: shallow breadth, score, select, deepen. Do not accept the first plausible patch just because it is close. |
| The Context Stack | Gives context a governance model: task identity, decision logs, provenance, guardrails, promotion paths, and agent-spawn forecasting. |
| Dissent Mode | Produces managed contradiction: dissent memos, safe-to-fail probes, stop-the-line triggers, and review that can change the decision. |
| The Salvage Loop | Treats the code draft as disposable and the learning as the asset. |

## Why skills, subagents, and extraction are in the curriculum

A phase name is cheap. Naming `/review` does not make review happen. Naming `/dissent` does not mean anything got challenged.

The harness has to carry enough context that another agent, reviewer, or future you can audit the work without trusting the chat summary.

Skills preserve **procedures** when there is a procedure worth repeating:

- how to frame a project slice;
- how to compare solution levels;
- how to write a reviewable brief;
- how to run a fragile project-specific check;
- how to salvage a failed run without keeping the bad patch.

Subagents preserve **roles** when the work needs a different set of eyes or a narrower runtime boundary:

- independent reviewer;
- codebase scout;
- test-gap hunter;
- migration planner;
- release checker;
- domain-specific validator;
- knowledge extractor.

Knowledge extraction preserves **learning** when the next session should not have to rediscover it:

- metis: what we learned from doing the work;
- signal: what measurement tells us the outcome is moving;
- guardrail: what must not happen again;
- outcome update: what changed in status, mechanism, or affected files;
- ADR: what architectural decision now constrains future work.

Skills, subagents, and extraction exist to preserve judgment across sessions: the procedure, the role boundary, the evidence, and the learning that should change the next run. Open Horizons-shaped paperwork is failure in a nicer outfit.

## Capstone

Use a real project with enough texture for judgment: tests, more than one subsystem, a known annoyance or recurring failure, and enough history that the debt is not hypothetical. If the project is blank, the exercise has no terrain. Pick a smaller real slice instead.

The learner improves that slice and leaves behind:

- an intent note;
- a model-fit note;
- a context pack;
- a prompt assembly;
- problem-space and problem-statement artifacts;
- a solution-level comparison;
- evidence checks;
- an agent brief;
- a project skill encoding one observed reusable procedure;
- a subagent encoding one independent role boundary;
- a patch or stopped execution report;
- review and dissent findings;
- one durable knowledge artifact;
- a salvage note if the run drifted.

The next-session test is the standard: a new agent or maintainer should be able to read the artifacts, recover the aim, constraints, chosen framing, evidence checks, role boundaries, and failure modes, then continue the same project slice without rediscovering the whole problem. If the artifacts do not make that possible, the curriculum produced paperwork, not learning.


---

## Navigation

- Previous: [Docs Home](index.md)
- Up: [Docs Home](index.md)
- Next: [Tutorial](tutorial.md)
