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

## Skill curriculum

| Module | Learner can do this | Artifact |
|---|---|---|
| 1. Intent Engineering | State a real intent, use the model for bursts, pause before commitment, and preserve the current understanding. | Intent note. |
| 2. Context construction | Build a selective context pack with provenance, constraints, landmines, and stop triggers. | Context pack. |
| 3. Open Horizons phase skills | Use `/aim`, `/problem-space`, `/problem-statement`, `/solution-space`, `/execute`, `/review`, `/dissent`, and `/salvage` as gates. | Session artifacts. |
| 4. Problem framing | Map terrain, separate symptoms from constraints, and choose a problem statement. | Problem-space map and problem statement. |
| 5. Solution search | Generate multiple solution levels and reject the nearest plausible patch. | Solution-space comparison with selected level. |
| 6. Evidence | Define checks before implementation. | Evidence checklist. |
| 7. Agent brief | Turn aim, mechanism, feedback, guardrails, and selected level into execution context. | Agent brief. |
| 8. Skill authoring | Encode repeated project procedures as `SKILL.md` files. | Project skill. |
| 9. Subagent authoring | Encode specialized roles as subagents with input contracts and tool limits. | Project subagent. |
| 10. Execution | Delegate one bounded implementation slice. | Patch or stopped execution report. |
| 11. Verification and review | Check the work against evidence and aim, not the agent's summary. | Review findings. |
| 12. Dissent | Stress the accepted-looking answer before committing. | Dissent memo. |
| 13. Knowledge extraction | Record metis, signals, guardrails, outcome updates, or ADRs that should survive the session. | `.oh/` artifact or ADR. |
| 14. Salvage | Keep the learning and restart smaller when the run drifts. | Salvage note and restart plan. |

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
