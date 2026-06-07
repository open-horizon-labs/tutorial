# Tutorial: Improve a Real Project With an Agent

You will use a coding agent to improve an existing project.

Not a one-file exercise. Use a real project with enough mess that the first plausible fix might be the wrong altitude.

The seed is GitHub's project-improvement tutorial for Copilot cloud agent: give the agent project context, have it surface technical debt, create issues, delegate one slice, and review the PR.

The Open Horizons version adds the part that matters before delegation: deciding what problem is worth solving, what level of solution it deserves, and what evidence would let you reject the agent's work.

## Required setup

Install the Open Horizons skills:

```bash
npx skills add open-horizon-labs/skills -g -a claude-code -y
```

Use a repo with real texture:

- tests, even if incomplete;
- more than one subsystem;
- a known annoyance or recurring failure;
- enough history that technical debt is not hypothetical.

If all you have is a blank project, stop. This exercise is about judgment in an existing system.

## The run

```text
/aim
/problem-space
/problem-statement
/solution-space
evals or acceptance checks
agent brief
/execute
/review
/dissent
/salvage if needed
```

The sequence matters. A coding agent can generate patches cheaply. That makes weak framing more expensive, not less.

## Step 1: Choose the project and aim

Pick one repo. Do not start by asking the agent to find all possible improvements.

Run `/aim`.

Give it:

```md
I want to use a coding agent to improve an existing project.

Project:
[repo name and short description]

Current pain:
[what keeps recurring, slowing us down, confusing users, breaking tests, or making changes risky]

What I want from this run:
- pick one meaningful improvement slice;
- compare levels of solution before implementing;
- write acceptance checks before delegation;
- review the agent's output against evidence, not confidence.
```

A good aim is a behavior change, not a task list.

Weak aim:

```md
Clean up technical debt.
```

Better aim:

```md
Reduce future change risk in one recurring problem area by selecting the right level of fix, encoding the expected behavior, and reviewing the agent's patch against those checks.
```

## Step 2: Map the problem space

Run `/problem-space`.

This is where the one-file version failed. There was no real terrain. Here there is.

Map:

- systems involved;
- users or maintainers affected;
- blast radius if the fix is wrong;
- existing tests and missing tests;
- repeated symptoms;
- hard constraints;
- soft constraints;
- assumed constraints;
- files or components that look central;
- prior attempts or abandoned fixes.

Useful input:

```md
Aim:
[paste aim]

Known pain:
[bug reports, flaky areas, slow workflows, confusing code, repeated review comments, recurring support issue]

Repo facts:
[language, test commands, build commands, architecture notes, relevant files]

Ask:
Map the problem space before we choose a fix. Separate symptoms from constraints. Identify assumptions that might be false.
```

Do not let the agent turn this into implementation advice yet. The job is to understand the terrain.

## Step 3: Frame the problem

Run `/problem-statement`.

Ask for three framings:

1. the obvious symptom framing;
2. a deeper systems framing;
3. a user or maintainer outcome framing.

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

Pick the framing you can act on without pretending to solve the whole system.

## Step 4: Search beyond the nearest peak

Run `/solution-space`.

This is the center of the exercise.

Ask for options at four levels:

| Level | Question | Example shape |
|---|---|---|
| Band-Aid | What patch suppresses the symptom? | Add a guard clause or one-off check. |
| Local Optimum | What improves the current design? | Consolidate duplicated logic, add focused tests. |
| Reframe | What changes the problem statement? | Treat this as ownership/idempotency, not a one-off bug. |
| Redesign | What would make this class of problem harder to create? | Move the invariant to one boundary, change event flow, or add a policy layer. |

Use the Beyond the Nearest Peak pattern:

```text
Shallow → Score → Select → Deepen
```

Generate breadth first. Do not evaluate while generating.

Then score each option against the same criteria:

- impact on the aim;
- implementation cost;
- reviewability;
- testability;
- reversibility;
- blast radius;
- maintenance burden;
- risk of creating a new local maximum.

Only deepen the option that survives the scoring.

The answer does not have to be Redesign. A deliberate Band-Aid can be right. The failure is accepting the first plausible patch because it compiled.

## Step 5: Define evidence before delegation

Write acceptance checks before `/execute`.

Use `templates/eval-checklist.md`.

For project improvement work, evidence may include:

- unit tests;
- integration tests;
- regression tests for the specific symptom;
- static checks;
- build or lint commands;
- migration checks;
- docs updated where behavior changed;
- review checklist tied to the chosen solution level;
- a manual reproduction step when automation is not practical.

A useful check is specific enough to fail.

Weak:

```md
The notification system should be cleaner.
```

Better:

```md
Given two identical notification events with the same idempotency key, the system sends one notification and records the duplicate as skipped.
```

## Step 6: Write the agent brief

Use `templates/agent-brief.md`.

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

The brief is not a prompt decoration. It is the contract for the agent run.

If the brief does not say what would make you reject the patch, it is not ready.

## Step 7: Execute one slice

Run `/execute` with the brief.

Keep the slice small enough to review.

The agent should:

- read the relevant files before editing;
- inspect existing tests and patterns;
- implement the selected approach;
- add or update checks;
- run the relevant commands;
- fix failures from the root cause;
- stop if the problem framing turns out wrong.

Do not let execution expand into a rewrite just because the agent can produce one.

## Step 8: Review the patch

Run `/review`.

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

## Step 9: Dissent before accepting

Run `/dissent`.

Ask it to assume the patch passes tests and still causes trouble.

Look for:

- the symptom moved somewhere else;
- the selected solution level was too low;
- the tests prove the patch, not the behavior;
- the new abstraction creates a second way to do the same thing;
- a maintainer would misunderstand the boundary;
- the fix works locally but fails in production conditions.

If dissent finds a real issue, revise the brief or patch. Do not treat dissent as theater.

## Step 10: Salvage if the run drifted

Run `/salvage` if the attempt goes sideways.

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

## What you should have at the end

- an aim;
- a problem-space map;
- a selected problem statement;
- a solution-space comparison across levels;
- acceptance checks;
- an agent brief;
- a patch or a salvage note;
- a review result;
- a dissent result;
- one thing to carry into the next run.

The output is not just the patch. The output is a better search process for the next patch.
