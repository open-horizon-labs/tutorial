# Builder Loop Tutorial

Use this tutorial for one real project slice: clarify the aim, frame the problem, choose a solution level, define evidence, delegate the work, review it, and preserve what the next session needs.

This is one guided path. Use [Context to Agent Tutorial](context-to-agent-tutorial.md) when the question is whether a prompt or checklist should become a skill or subagent. Use [Eval Tutorial](evals-tutorial.md) when the evidence needs fixtures, graders, thresholds, or production signals.

Review, dissent, and salvage can interrupt any step. They are checks, not final ceremony.

Use a real project with enough texture that there is more than one plausible solution. If all you have is a blank repo, stop. Judgment needs an existing system.

## Required setup

Install the Open Horizons skills:

```bash
npx skills add open-horizon-labs/skills -g -a claude-code -y
```

Use a project with:

- tests, even if incomplete;
- more than one subsystem;
- a known annoyance or recurring failure;
- enough history that technical debt is not hypothetical.

## How to use the deep dives

Start with [`curriculum.md`](curriculum.md). It is the overview map: module, artifact, deep dive, and go-deeper path.

During the tutorial, read the deep dive when that skill becomes active. Do not read everything as homework first; use the references when the work needs them.

## Part 1: Build the curriculum artifacts

### Step 1: Intent Engineering

Read [Intent Engineering](intent-engineering.md).

Write one sentence that names the outcome, not the activity.

| Version | Intent |
|---|---|
| Weak | Use an agent to clean up notifications. |
| Better | Make future notification changes safer by moving duplicate prevention to the boundary where sends happen. |

Then do a short model burst:

- likely causes;
- likely files;
- possible solution levels;
- likely checks;
- ways the patch could look right and still fail.

Pause before committing to any path.

Artifact:

```text
intent note
```

### Step 2: Model-fit framing

Read [Model-Fit Framing](model-fit.md), then use the [model-fit note template](../templates/model-fit-note.md).

Before building the context pack, decide what work the model is actually suited to do.

| Version | Prompt |
|---|---|
| Weak | Summarize this Zoom transcript. |
| Better | Using the transcript and context pack, produce a decision-preserving meeting note for the platform roadmap review. Separate decisions, proposals, risks, action items, and missing context. Quote the transcript line or timestamp for every commitment. |

Write down:

- the task you are asking the model to perform;
- the supplied context it needs;
- the language operation it should perform;
- what it must not infer;
- the output contract;
- how a reviewer can check the result.

If the answer needs private organizational context, provide it or mark the task not ready.

Artifact:

```text
model-fit note
```

### Step 3: Context pack

Read [Context Construction](context-construction.md), then build a context pack for the agent.

Do not dump the repo. Select context and record provenance.

Include:

- intent;
- model-fit note;
- project shape;
- relevant files or components;
- known constraints;
- current pain;
- prior attempts;
- tests and commands;
- landmines;
- what should trigger stop, dissent, or salvage.

This is The Context Stack applied to coding work: context should be inspectable, editable, provenance-backed, and small enough to use.

Artifact:

```text
context pack
```

### Checkpoint: Prompt and context assembly

Read [Prompt and Context Assembly](prompt-and-context.md), then use the [prompt assembly template](../templates/prompt-assembly.md).

This is a slice through the early artifacts. It turns the intent note, model-fit note, context pack, and evidence expectations into a request with:

- success criteria and fixture cases;
- stable instructions separated from dynamic context;
- primary content and supporting context with provenance;
- examples where behavior needs to be consistent;
- output contract and missing-context behavior;
- reviewer checks that can reject fluent but ungrounded output.

If the assembled prompt still requires the model to infer private context, lacks fixtures, or mixes instructions with source data, go back to the context pack before continuing.

### Step 4: Aim

Run `/aim`.

Give it the intent note and context pack.

The output should name:

- aim;
- current state;
- desired state;
- mechanism;
- assumptions;
- feedback signal;
- guardrails.

Do not let “clean up technical debt” pass as an aim. Simplicity is usually a mechanism, not the outcome.

Artifact:

```text
aim statement
```

### Step 5: Problem space

Run `/problem-space`.

Map:

- systems involved;
- users or maintainers affected;
- blast radius if wrong;
- existing tests and missing tests;
- repeated symptoms;
- hard constraints;
- soft constraints;
- assumed constraints;
- central files or components;
- prior attempts or abandoned fixes.

This step maps terrain before implementation advice has a chance to narrow the frame.

Artifact:

```text
problem-space map
```

### Step 6: Problem statement

Read [Problem Statement](problem-statement.md), then run `/problem-statement` and use the [problem statement template](../templates/problem-statement.md).

Ask for at least three framings:

1. symptom framing;
2. systems framing;
3. user or maintainer outcome framing.

For each, require:

- what it improves;
- what it hides;
- what solution shapes it makes likely;
- what evidence would show the framing is wrong.

Example:

| Framing | Example |
|---|---|
| Symptom | Notifications sometimes send twice. |
| Systems | Notification ownership is split across multiple trigger paths, so no single layer enforces idempotency. |
| Maintainer | Engineers cannot safely add notification behavior because the current flow does not make ownership or duplicate prevention obvious. |

Artifact:

```text
selected problem statement
```

### Step 7: Solution search

Read [Beyond the Nearest Peak](beyond-nearest-peak.md), then run `/solution-space`.

Use the `Beyond the Nearest Peak` pattern: shallow breadth, score, select, then deepen.

Generate breadth first. Do not evaluate while generating.

Require at least one option at each level:

| Level | Question | Example shape |
|---|---|---|
| Band-Aid | What patch suppresses the symptom? | Add a guard clause or one-off check. |
| Local Optimum | What improves the current design? | Consolidate duplicated logic, add focused tests. |
| Reframe | What changes the problem statement? | Treat this as ownership/idempotency, not a one-off bug. |
| Redesign | What would make this class of problem harder to create? | Move the invariant to one boundary, change event flow, or add a policy layer. |

Then score each option against the same criteria:

- impact on the aim;
- implementation cost;
- reviewability;
- testability;
- reversibility;
- blast radius;
- maintenance burden;
- risk of creating a new local maximum.

Only deepen the option that survives scoring.

Artifact:

```text
solution-space comparison and selected level
```

### Step 8: Evidence before delegation

Read [Evidence and Evals](evidence-and-evals.md), then use the [eval checklist template](../templates/eval-checklist.md). If the check needs a fixture set, grader, threshold, or production signal, run the [Eval Tutorial](evals-tutorial.md).

Define checks before `/execute`:

- old behavior that should now fail;
- invariant that should hold;
- positive, negative, and edge cases;
- grader or command that proves the behavior;
- threshold good enough for this slice;
- action if the check fails;
- residual risk after checks pass.

Artifact: evidence checklist.

### Step 9: Agent brief

Read [Agent Briefs](agent-briefs.md), then use the [agent brief template](../templates/agent-brief.md).

The brief should include:

- aim;
- selected problem statement;
- selected solution level;
- why other levels were rejected;
- files or areas to inspect first;
- behavior contract;
- acceptance checks;
- commands to run;
- explicit non-goals;
- stop conditions;
- review criteria.

The brief is the execution contract.

Artifact:

```text
agent brief
```

### Optional checkpoint: promote reusable interfaces

If the run surfaced a repeated prompt shape, checklist, evidence gate, or role boundary, pause here and use [Context to Agent Tutorial](context-to-agent-tutorial.md).

Do not make skill or subagent authoring mandatory for this tutorial. Promote only when the workflow or role has proved reusable.

Artifact if needed: project skill, subagent, or a note explaining why the interface stays one-off.

## Part 2: Apply the loop to code

### Step 10: Execute one slice

Read [Execution, Review, Dissent, and Salvage](execution-review-salvage.md), then run `/execute` with the agent brief.

The agent should:

- read relevant files before editing;
- inspect existing tests and patterns;
- implement the selected approach;
- add or update checks;
- run the relevant commands;
- fix failures from the root cause;
- stop if the problem framing turns out wrong.

Do not let execution expand into a rewrite just because the agent can produce one.

Artifact:

```text
patch or stopped execution report
```

### Step 11: Review

Use the review section in [Execution, Review, Dissent, and Salvage](execution-review-salvage.md#review), then run `/review`.

Review against the aim, not against the agent's summary.

Check:

- Did it solve the framed problem?
- Did it stay at the selected solution level?
- Did it leave the system easier to change?
- Did it add checks that would fail on the old behavior?
- Did it remove obsolete code or create a parallel path?
- Did it touch unrelated files?
- Did it run the commands it claims to have run?

If there are no findings, name the residual risk. There is always residual risk.

Artifact:

```text
review findings
```

### Step 12: Dissent

Use the dissent section in [Execution, Review, Dissent, and Salvage](execution-review-salvage.md#dissent), then run `/dissent`.

Assume the patch passes tests and still fails.

Look for:

- the symptom moved somewhere else;
- the selected solution level was too low;
- the tests prove the patch, not the behavior;
- the new abstraction creates a second way to do the same thing;
- a maintainer would misunderstand the boundary;
- the fix works locally but fails in production conditions.

Dissent is not theater. If it finds a real issue, revise the brief or patch.

Artifact:

```text
dissent memo
```

### Step 13: Knowledge extraction

Read [Knowledge Extraction](knowledge-extraction.md), then use the [knowledge artifact template](../templates/knowledge-artifact.md) to record what should survive the session.

Choose the right artifact:

| Artifact | Use when |
|---|---|
| Metis | You learned a situated pattern. |
| Signal | You found a measurement that indicates movement. |
| Guardrail | Something must not happen again. |
| Outcome update | Status, mechanism, or affected files changed. |
| ADR | A decision now constrains future architecture. |

This is where the run becomes future context.

Artifact:

```text
.oh/metis/*, .oh/signals/*, .oh/guardrails/*, .oh/outcomes/*, or docs/ADRs/*
```

### Step 14: Salvage if needed

Use the salvage section in [Execution, Review, Dissent, and Salvage](execution-review-salvage.md#salvage), then run `/salvage` if the attempt went sideways.

Use it when:

- the agent patched symptoms after you selected a deeper fix;
- tests were weak or mocked away the real behavior;
- the problem statement changed during implementation;
- the patch grew beyond reviewable size;
- the code works but the design is now less obvious.

Keep:

- the better problem statement;
- the constraints you learned;
- the rejected solution paths;
- the checks that should survive;
- the smaller restart plan.

Drop the draft if keeping it would make the system worse.

Artifact:

```text
salvage note and restart plan
```

## Builder output

You should finish with:

- intent note;
- model-fit note;
- context pack;
- prompt assembly;
- aim;
- problem-space map;
- selected problem statement;
- solution-space comparison;
- evidence checklist;
- agent brief;
- project skill or subagent only if a reusable procedure or role boundary emerged;
- patch or stopped execution report;
- review findings;
- dissent memo;
- durable knowledge artifact;
- salvage note if needed.

The patch is only one output. The larger output is a working development loop that can improve the next run.


---

## Navigation

- Previous: [Curriculum](curriculum.md)
- Up: [Docs Home](index.md) / [Curriculum](curriculum.md)
- Next: [Intent Engineering](intent-engineering.md)
