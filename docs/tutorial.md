# Tutorial: Build the LLM Development Loop

This exercise teaches the skills an LLM developer should know, then applies the Open Horizons corpus to those skills.

The spine is:

```text
Intent → Model-fit framing → Context construction → Problem framing → Solution search → Evidence → Delegation → Verification → Dissent → Knowledge extraction → Salvage
```

Use a real project with enough texture that there is more than one plausible solution. If all you have is a blank repo, stop. The point is judgment in an existing system.

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

Read `docs/intent-engineering.md`.

Write one sentence that names the outcome, not the activity.

Weak:

```md
Use an agent to clean up notifications.
```

Better:

```md
Make future notification changes safer by moving duplicate prevention to the boundary where sends happen.
```

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

Read `docs/model-fit.md`, then use `templates/model-fit-note.md`.

Before building the context pack, decide what work the model is actually suited to do.

Weak:

```md
Summarize this Zoom transcript.
```

Better:

```md
Using the transcript and context pack, produce a decision-preserving meeting note for the platform roadmap review. Separate decisions, proposals, risks, action items, and missing context. Quote the transcript line or timestamp for every commitment.
```

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

Read `docs/context-construction.md`, then build a context pack for the agent.

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

Run `/problem-statement`.

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

```md
Symptom framing: Notifications sometimes send twice.
Systems framing: Notification ownership is split across multiple trigger paths, so no single layer enforces idempotency.
Maintainer framing: Engineers cannot safely add notification behavior because the current flow does not make ownership or duplicate prevention obvious.
```

Artifact:

```text
selected problem statement
```

### Step 7: Solution search

Run `/solution-space`.

Use the `Beyond the Nearest Peak` pattern:

```text
Shallow → Score → Select → Deepen
```

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

Read `docs/evidence-and-evals.md`, then use `templates/eval-checklist.md`.

Define checks before `/execute`.

Evidence may include:

- unit tests;
- integration tests;
- regression tests for the specific symptom;
- static checks;
- build or lint commands;
- migration checks;
- docs updated where behavior changed;
- manual reproduction when automation is not practical;
- review criteria tied to the selected solution level.

A useful check is specific enough to fail.

Weak:

```md
The notification system should be cleaner.
```

Better:

```md
Given two identical notification events with the same idempotency key, the system sends one notification and records the duplicate as skipped.
```

Artifact:

```text
evidence checklist
```

### Step 9: Agent brief

Read `docs/agent-briefs.md`, then use `templates/agent-brief.md`.

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

### Step 10: Author a project skill

Read `docs/authoring-skills.md`.

Use `templates/project-skill.md` to encode one reusable procedure discovered during the run.

Good candidates:

- a fragile test command sequence;
- a repeated review checklist;
- a recurring bug-class check;
- a project-specific release verification;
- a salvage/restart procedure.

Do not author a skill for generic advice. The skill should preserve local procedure.

Artifact:

```text
.claude/skills/<skill-name>/SKILL.md
```

### Step 11: Author a subagent

Read `docs/subagents.md`.

Use `templates/subagent.md` to encode one role boundary.

Good candidates:

- independent reviewer;
- codebase scout;
- test-gap hunter;
- migration planner;
- release checker;
- domain validator;
- knowledge extractor.

The role should have:

- input contract;
- tool limits;
- process;
- stop conditions;
- output format;
- anti-patterns.

Artifact:

```text
.claude/agents/<name>.md
```

## Part 2: Apply the loop to code

### Step 12: Execute one slice

Read `docs/execution-review-salvage.md`, then run `/execute` with the agent brief.

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

### Step 13: Review

Use the review section in `docs/execution-review-salvage.md`, then run `/review`.

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

### Step 14: Dissent

Use the dissent section in `docs/execution-review-salvage.md`, then run `/dissent`.

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

### Step 15: Knowledge extraction

Read `docs/knowledge-extraction.md`.

Use `templates/knowledge-artifact.md` to record what should survive the session.

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

### Step 16: Salvage if needed

Use the salvage section in `docs/execution-review-salvage.md`, then run `/salvage` if the attempt went sideways.

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

## Capstone output

You should finish with:

- intent note;
- model-fit note;
- context pack;
- aim;
- problem-space map;
- selected problem statement;
- solution-space comparison;
- evidence checklist;
- agent brief;
- project skill;
- subagent;
- patch or stopped execution report;
- review findings;
- dissent memo;
- durable knowledge artifact;
- salvage note if needed.

The patch is only one output. The larger output is a working development loop that can improve the next run.
