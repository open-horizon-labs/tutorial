# Docs Home

Start here when the repo feels like a pile of good pages but you need a path.

This curriculum has two jobs:

1. teach practical LLM-development skills inside existing systems;
2. apply the Open Horizons loop to those skills without turning it into paperwork.

## Start here

If you are new, use this order:

1. Read the [Curriculum](curriculum.md) for the map.
2. Run the [Tutorial](tutorial.md) with one real project slice.
3. Open each deep dive only when that skill becomes active.
4. Use the templates when the tutorial asks for an artifact.
5. Finish by checking whether the next session could continue from what you left behind.

## Choose your path

| If you are trying to... | Start with | Then use |
|---|---|---|
| Understand the whole curriculum | [Curriculum](curriculum.md) | [Tutorial](tutorial.md) |
| Work through one real project slice | [Tutorial](tutorial.md) | [Builder playground](../templates/builder-playground.md) |
| Learn prompt engineering as context assembly | [Prompt and Context Assembly](prompt-and-context.md) | [Prompt assembly template](../templates/prompt-assembly.md) |
| Turn a one-off prompt into a reusable agent interface | [Context to Agent Tutorial](context-to-agent-tutorial.md) | [Context Construction](context-construction.md) |
| Stop getting generic model output | [Model-Fit Framing](model-fit.md) | [Context Construction](context-construction.md) |
| Decide what problem the agent is allowed to solve | [Problem Space](problem-space.md) | [Problem Statement](problem-statement.md) |
| Avoid the nearest plausible patch | [Beyond the Nearest Peak](beyond-nearest-peak.md) | [Evidence and Evals](evidence-and-evals.md) |
| Delegate implementation safely | [Agent Briefs](agent-briefs.md) | [Execution, Review, Dissent, and Salvage](execution-review-salvage.md) |
| Clarify aim, mechanism, feedback, and guardrails | [Strategy Clarity](strategy-clarity.md) | [Agent Briefs](agent-briefs.md) |
| Preserve learning for the next session | [Knowledge Extraction](knowledge-extraction.md) | [Knowledge artifact template](../templates/knowledge-artifact.md) |
| Read the source material | [Further Reading](further-reading.md) | linked essays and references |

## Full curriculum map

| Step | Deep dive | Artifact |
|---|---|---|
| 1. Intent Engineering | [Intent Engineering](intent-engineering.md) | intent note |
| 2. Model-fit framing | [Model-Fit Framing](model-fit.md) | [model-fit note](../templates/model-fit-note.md) |
| 3. Context construction | [Context Construction](context-construction.md) | [context pack](../templates/context-pack.md) |
| 4. Open Horizons phase skills | [Open Horizons Phase Skills](open-horizons.md) | session artifacts |
| 5. Problem space (`/problem-space`) | [Problem Space](problem-space.md) | problem-space map |
| 6. Problem statement (`/problem-statement`) | [Problem Statement](problem-statement.md) | [problem statement](../templates/problem-statement.md) |
| 7. Solution search (`/solution-space`) | [Beyond the Nearest Peak](beyond-nearest-peak.md) | solution-space comparison |
| 8. Evidence | [Evidence and Evals](evidence-and-evals.md) | [eval checklist](../templates/eval-checklist.md) |
| 9. Agent brief | [Agent Briefs](agent-briefs.md) | [agent brief](../templates/agent-brief.md) |
| 10. Skill authoring | [Authoring Skills](authoring-skills.md) | [project skill](../templates/project-skill.md) |
| 11. Subagent authoring | [Authoring Subagents](subagents.md) | [subagent](../templates/subagent.md) |
| 12. Execution (`/execute`) | [Execution, Review, Dissent, and Salvage](execution-review-salvage.md#execute) | patch or stopped execution report |
| 13. Verification and review (`/review`) | [Execution, Review, Dissent, and Salvage](execution-review-salvage.md#review) | review findings |
| 14. Dissent (`/dissent`) | [Execution, Review, Dissent, and Salvage](execution-review-salvage.md#dissent) | dissent memo |
| 15. Knowledge extraction | [Knowledge Extraction](knowledge-extraction.md) | [knowledge artifact](../templates/knowledge-artifact.md) |
| 16. Salvage (`/salvage`) | [Execution, Review, Dissent, and Salvage](execution-review-salvage.md#salvage) | salvage note and restart plan |

## Slices through the curriculum

| Slice | Combines | Use when |
|---|---|---|
| Prompt and context assembly | Intent Engineering, Model-Fit Framing, Context Construction, and Evidence | You know what you want from the model but not how to assemble the request without dumping context. |
| Context to agent interface | Context Construction, Prompt and Context Assembly, Authoring Skills, and Authoring Subagents | You have a useful one-off prompt and need to decide what becomes context, prompt, skill, or subagent. |


## Templates map

| Template | Use it when |
|---|---|
| [Builder playground](../templates/builder-playground.md) | choosing the real project slice for the tutorial |
| [Model-fit note](../templates/model-fit-note.md) | deciding what work the model is suited to do |
| [Context pack](../templates/context-pack.md) | supplying project facts without dumping the repo |
| [Prompt assembly](../templates/prompt-assembly.md) | separating stable instructions from dynamic context, adding examples, output contract, fixtures, and reviewer checks |
| [Problem statement](../templates/problem-statement.md) | narrowing mapped terrain into the selected slice |
| [Eval checklist](../templates/eval-checklist.md) | defining checks before delegation |
| [Agent brief](../templates/agent-brief.md) | handing execution to an agent or future session |
| [Project skill](../templates/project-skill.md) | preserving a repeated procedure |
| [Subagent](../templates/subagent.md) | preserving a bounded role |
| [Knowledge artifact](../templates/knowledge-artifact.md) | recording durable metis, signals, guardrails, outcome updates, or ADRs |

## I am stuck at...

| Symptom | Go here |
|---|---|
| The model output is fluent but generic. | [Model-Fit Framing](model-fit.md), [Context Construction](context-construction.md), and [Prompt and Context Assembly](prompt-and-context.md) |
| You know the model task and context, but not how to separate instructions, data, examples, and checks. | [Prompt and Context Assembly](prompt-and-context.md) |
| You keep copy-pasting the same prompt or checklist. | [Context to Agent Tutorial](context-to-agent-tutorial.md) and [Authoring Skills](authoring-skills.md) |
| The repo has too many possible fixes. | [Problem Space](problem-space.md), then [Problem Statement](problem-statement.md) |
| The first patch looks plausible but shallow. | [Beyond the Nearest Peak](beyond-nearest-peak.md) |
| Nobody knows whether the change is correct. | [Evidence and Evals](evidence-and-evals.md) |
| The agent keeps wandering. | [Agent Briefs](agent-briefs.md) and [Execution, Review, Dissent, and Salvage](execution-review-salvage.md) |
| The patch works, but the next session would forget the lesson. | [Knowledge Extraction](knowledge-extraction.md) |
| The work keeps expanding and the finish line keeps moving. | [Execution, Review, Dissent, and Salvage](execution-review-salvage.md#salvage) |

---

## Navigation

- Previous: [README](../README.md)
- Up: [README](../README.md)
- Next: [Curriculum](curriculum.md)
