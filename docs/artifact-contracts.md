# Artifact Contracts

Artifacts are not note-shaped souvenirs. Each artifact must let the next consumer continue the work without rediscovering the conversation.

A useful artifact preserves four things:

| Requirement | Question |
|---|---|
| Decision | What did this step settle or choose? |
| Evidence or assumption | What supports it, and what could prove it wrong? |
| Boundary | What is in scope, out of scope, or unsafe to infer? |
| Next consumer | Who or what uses this next: a skill, subagent, reviewer, maintainer, future session, or eval? |

If an artifact does not change the next action, shrink it, merge it, or delete it.

## Builder-loop artifacts

| Artifact | Produce when | Must include | Consumed by | Reject if |
|---|---|---|---|---|
| Intent note | Before exploring fixes. | Desired behavior change, current pain, likely causes/files/checks from the burst, pause questions, what would prove this is the wrong task. | Model-fit framing, context pack, `/aim`. | It names an activity instead of an outcome. |
| Model-fit note | Before asking the model for output. | Model task, language operation, required context, what the model must not infer, output contract, reviewer check. | Context pack, prompt assembly, agent brief. | It asks the model to guess missing organizational or repo context. |
| Context pack | Before implementation or delegation. | Task identity, project shape, relevant sources with provenance, hard/soft/assumed constraints, evidence available now, landmines, stop/dissent/salvage triggers. | Prompt assembly, `/problem-space`, `/execute`, `/review`, `/dissent`. | It dumps files without saying why they matter or hides provenance. |
| Prompt assembly | Before using a prompt shape for real work. | Success criteria, stable instructions, dynamic context, primary/supporting content, examples if needed, output contract, missing-evidence behavior, fixture/reviewer checks. | One real run, Context to Agent Tutorial, eval design. | Instructions and data are mixed, or no failure case can reject the output. |
| Aim statement | Before problem mapping. | Outcome, current state, desired state, mechanism, assumptions, feedback signal, guardrails. | Problem-space map, solution search, agent brief, review. | It treats a mechanism such as “clean up” as the outcome. |
| Problem-space map | Before choosing the problem statement. | Systems, actors, repeated symptoms, constraints, assumptions to test, evidence, prior attempts, blast radius. | Problem statement, solution search, dissent. | It restates the symptom without terrain or affected people. |
| Selected problem statement | Before solution search. | Selected framing, rejected framings, scope boundary, invalidation signal, handoff question for solution-space. | Solution comparison, eval checklist, agent brief. | It hides what was rejected or cannot be proven wrong. |
| Solution-space comparison | Before delegation. | Band-Aid/local optimum/reframe/redesign options, scoring criteria, rejected options, selected level, why this level fits the aim. | Evidence checklist, agent brief, dissent. | It accepts the first plausible patch without comparing levels. |
| Evidence and eval checklist | Before `/execute`. | Eval objective, behavior/invariant, fixture set, harness/app/user/model grader choice, threshold, action policy, residual risk. | Agent brief, `/execute`, `/review`. | It cannot fail on the old behavior or has no decision rule. |
| Agent brief | Before implementation. | Purpose, aim, problem statement, selected solution level, mechanism, feedback, guardrails, context to inspect, behavior contract, checks, stop conditions, review checklist. | `/execute`, `/review`, `/dissent`, knowledge extraction. | It only says what to edit or omits how the work will be rejected. |
| Patch or stopped execution report | After `/execute`. | Changed files, behavior changed, checks run with observed results, failures fixed or still open, reason for stopping if stopped. | `/review`, maintainer, salvage. | It reports confidence without observed commands or state. |
| Review findings | After `/review`. | Accepted behavior, findings, evidence checked, residual risk, follow-up required, whether the selected level still holds. | `/dissent`, patch revision, knowledge extraction. | It relies on the implementer’s summary instead of external evidence. |
| Dissent memo | Before accepting an accepted-looking answer. | Steel-man, contrary evidence, pre-mortem, hidden assumptions, recommendation, confidence after dissent. | Patch revision, ADR, knowledge extraction. | It cannot name a plausible way the work fails. |
| Durable knowledge artifact | When learning should constrain the next run. | Artifact type, claim/update, evidence, provenance, future behavior or action trigger, owner or review path when relevant. | Future context pack, skill, subagent, maintainer. | It records an unreviewed observation as durable policy. |
| Salvage note and restart plan | When work drifts. | Original aim, why salvaged, learnings, guardrails, missing context, reusable fragments, smaller restart recommendation. | Next session, `/aim`, `/problem-space`. | It preserves code because effort was spent on it rather than because it improves the system. |

## Interface artifacts

| Artifact | Produce when | Must include | Consumed by | Reject if |
|---|---|---|---|---|
| Project skill | A repeated workflow has proved reusable. | Trigger, inputs, steps, constraints, stop conditions, output shape, verification. | Future sessions and agents. | It contains stale project facts that belong in a fresh context pack. |
| Subagent | A bounded role improves evidence, context load, independence, or parallelism. | Role purpose, input contract, tools, process, output contract, stop conditions, boundaries. | Main agent, reviewer, parallel workflow. | It needs the whole chat to function or has no independent output contract. |

## Navigation

- Previous: [Docs Home](index.md)
- Up: [Docs Home](index.md) / [Curriculum](curriculum.md)
- Next: [Builder Loop Tutorial](tutorial.md)
