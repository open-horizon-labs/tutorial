# Improving a Real Project With Agents

Most coding-agent tutorials start with a one-file task. That is fine for tool familiarity. It is bad for judgment.

The harder problem is deciding what the agent should work on, what level of solution the problem deserves, and what evidence would let you reject a polished but shallow fix.

This repo uses an existing project with real technical debt. The seed is GitHub's Copilot cloud-agent tutorial about improving a mature project. The Open Horizons version adds the missing judgment work: aim, problem space, solution search, evals, review, dissent, and salvage.

## Before you assign work

Do not start by asking the agent to fix the first thing it finds.

First decide:

- what outcome matters;
- what constraints are real;
- which problems are symptoms;
- what levels of solution are available;
- what signal would prove the fix worked;
- what kind of agent output you will reject.

The run uses the Open Horizons skills in this order:

```text
/aim → /problem-space → /problem-statement → /solution-space → evals → brief → /execute → /review → /dissent → /salvage
```

The important addition is `/solution-space`. Cheap generation means the first workable fix is no longer good enough. You should fan out, score options, choose what deserves depth, and kill weak paths early.

## Who this is for

Builders who work in real codebases.

Developers, product engineers, founders, operators, platform leads, and anyone else who has to improve software without losing the thread between code, users, risk, and maintenance.

You do not need a perfect repo. You need one with enough texture that there is more than one plausible solution.

## What you do

You will:

1. pick an existing project;
2. install the Open Horizons skills;
3. use `/aim` to define the improvement outcome;
4. use `/problem-space` to map constraints, users, systems, blast radius, and assumptions;
5. use `/problem-statement` to choose the problem framing;
6. use `/solution-space` to compare Band-Aid, Local Optimum, Reframe, and Redesign paths;
7. write evals or acceptance checks before implementation;
8. write an agent brief;
9. run `/execute` on the selected slice;
10. run `/review` and `/dissent` before accepting the result;
11. run `/salvage` if the attempt drifts.

## Quick start

Install the skills:

```bash
npx skills add open-horizon-labs/skills -g -a claude-code -y
```

Then work through:

```text
docs/tutorial.md
```

## Repo map

- `docs/tutorial.md` — the exercise.
- `docs/problem-space.md` — why a one-file task was rejected and what replaces it.
- `docs/open-horizons.md` — the skill sequence for a real project improvement.
- `docs/strategy-clarity.md` — how to turn aim, mechanism, feedback, and guardrails into an agent brief.
- `docs/beyond-nearest-peak.md` — the shallow-breadth / score / select / deepen pattern.
- `docs/further-reading.md` — source material and follow-up reading.
- `templates/builder-playground.md` — choose a real project slice.
- `templates/agent-brief.md` — give the agent enough structure to work.
- `templates/eval-checklist.md` — define evidence before implementation.
- `examples/technical-debt-agent-brief.md` — a worked duplicate-notification example.

## What this is not

- Not a prompt cheat sheet.
- Not a one-file exercise.
- Not a tour of agent UI buttons.
- Not a claim that agents can decide what matters for you.
- Not a reason to hand technical debt ranking to a model and walk away.

The skill is choosing the right work, comparing levels of solution, and rejecting output that does not move the aim.

## Source material

The project-improvement shape comes from GitHub's [Using GitHub Copilot cloud agent to improve a project](https://docs.github.com/en/copilot/tutorials/cloud-agent/improve-a-project).

The solution-search shape comes from Muness Castle's [Beyond the Nearest Peak](https://muness.com/posts/beyond-the-nearest-peak/).
