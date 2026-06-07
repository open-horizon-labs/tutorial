# Problem Space

**Date:** 2026-06-06  
**Scope:** `open-horizon-labs/tutorial`

## What changed

The one-file version was too shallow.

There was not enough terrain for `/aim` or `/problem-space` to earn their place. The obvious task was the correct task. The only real move was “define behavior before code.” Useful, but not enough for Open Horizons.

The repo now uses a real project-improvement task: take an existing repo with technical debt, choose one improvement slice, compare levels of solution, and delegate the selected slice to an agent.

## Behavior change

A builder can use an agent to improve an existing project without accepting the first plausible patch.

They can:

- name the outcome;
- map constraints and blast radius;
- separate symptoms from problems;
- compare Band-Aid, Local Optimum, Reframe, and Redesign options;
- define evidence before implementation;
- review and dissent before accepting the patch;
- salvage learning when the attempt drifts.

## Constraints

| Constraint | Why it matters |
|---|---|
| Use a real existing project | Problem-space exploration needs actual terrain. |
| Use the Open Horizons skills | The tutorial should demonstrate the skills, not provide a parallel prompt-only path. |
| Keep the slice reviewable | “Real” cannot become “rewrite the whole product.” |
| Include multiple solution levels | This is where `Beyond the Nearest Peak` belongs. |
| Require evidence before implementation | Otherwise the agent can produce polished wrong work. |
| No customer or private data | Public tutorial must be safe to run. |
| Voice must stay concrete | No generated tutorial gloss. |

## What can go wrong

- The agent ranks technical debt and the human rubber-stamps it.
- The first plausible fix becomes the plan.
- `/problem-space` becomes ceremony instead of terrain mapping.
- `/solution-space` compares syntax choices instead of levels of solution.
- The selected slice is too large to review.
- Tests prove implementation details instead of behavior.
- Dissent becomes theater after the decision is already made.
- Salvage keeps bad code because time was spent on it.

## Source seed

GitHub's project-improvement tutorial has the right shape:

1. give the agent repo context;
2. check setup and instructions;
3. ask it to surface technical debt;
4. create issues;
5. delegate one issue;
6. review the resulting PR.

That is a better seed than a one-file exercise because the choice of work is itself part of the work.

## Why this merits problem-space exploration

A real project has constraints that may be hard, soft, or assumed:

- test coverage;
- CI speed;
- release pressure;
- migration risk;
- downstream users;
- architecture boundaries;
- ownership;
- prior failed fixes;
- reviewer capacity;
- data or security risk.

Those constraints change the right solution level.

A duplicate notification bug might be:

- a one-line guard;
- a missing regression test;
- unclear ownership of event emission;
- lack of idempotency at the boundary;
- a design that allows multiple paths to send the same notification.

Those are not the same problem.

## Why this merits solution-space exploration

`Beyond the Nearest Peak` applies directly.

Agents make it cheap to generate possible fixes. That means the human should not settle for the first path that compiles.

The tutorial should force a fan-out:

- Band-Aid;
- Local Optimum;
- Reframe;
- Redesign.

Then it should force scoring:

- impact;
- cost;
- testability;
- reviewability;
- reversibility;
- blast radius;
- maintenance burden.

Then deepen one path.

## First version

Build one tutorial around improving an existing project, plus:

- a solution-level guide;
- an agent brief template;
- an eval/acceptance-check template;
- one worked technical-debt example.

Do not add a full sample app yet. The first review question is whether the reasoning shape lands.
