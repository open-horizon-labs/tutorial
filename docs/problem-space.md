# Problem Space

**Date:** 2026-06-06  
**Scope:** `open-horizon-labs/tutorial`

## What I am trying to do

Build a tutorial for someone who wants to get better at coding with agents, not collect prompt tricks.

The behavior change:

> A builder can take a small coding task, name the aim and constraints, define checks before code, direct an agent through the work, and review the result without confusing confidence for correctness.

The repo is the vehicle. The skill is the judgment loop.

## Constraints

| Constraint | Why it matters |
|---|---|
| Use an existing tutorial as the seed | The ask was to find a tutorial we can use, not invent another toy from scratch. |
| No customer names or private transcript details | The public version should not leak context. |
| No unrelated warm-up scenario | That direction was rejected. Keep the work tied to coding. |
| No domain workflow example | This version should be about prompts, evals, code, review, and recovery. |
| Coding task must be small but checkable | The learner needs edge cases without fighting a whole app. |
| Open Horizons first; skills optional | The method should work in Claude Code, Cursor, Copilot, Codex, or another tool. |
| Evals before code | Otherwise this becomes “ask the agent and hope.” |
| MVP, not curriculum | A giant course is an easy way to produce nothing useful. |
| Voice must be human | No generated polish. No consultant fog. |

## What can go wrong

- It becomes another prompt guide.
- It confuses Open Horizons with the skill pack.
- It treats the agent brief as a prompt instead of a strategy artifact.
- It explains the philosophy but gives nobody anything to run.
- It picks a task too trivial to teach judgment.
- It picks a task so large that setup becomes the lesson.
- It treats evals like decoration.
- It sounds generated.

## Why base62

The Microsoft tutorial uses this prompt:

```text
Using Python 3.13 and uv, implement a base62 encoder/decoder.
```

That is a good seed. It is small, code-shaped, and easy to check. It has edge cases:

- zero;
- negative numbers;
- invalid characters;
- empty input;
- round trips;
- canonical output.

A bad implementation can look plausible. That is exactly why it works as the exercise.

## What problem inversion misses

Problem inversion helps. When someone hands you a solution, recover the problem underneath.

That is one move. It is not the whole operating system for coding with agents.

This repo needs the full loop:

```text
Aim → Problem Space → Problem Statement → Solution Space → Execute → Review → Dissent → Salvage
```

For agent work, the missing pieces are execution discipline, evals, review, dissent, and salvage. Without those, a learner can avoid the wrong problem and still accept wrong code.

## Assumptions

1. The learner wants to contribute faster, not learn vocabulary.
2. A small coding task beats an abstract prompt lesson.
3. Base62 is boring enough to avoid distraction and sharp enough to need tests.
4. The first lesson should teach one loop through one task.
5. Open Horizons can be useful without installing the skills.

## X-Y check

- **Asked for:** find a coding-agent tutorial we can use and apply the frame to it.
- **Actually needed:** a practical starting point for learning how to direct agents through coding work with prompts, evals, review, and salvage.

These line up.

## First version

Build one tutorial, a few templates, one worked base62 example, and a short reading list.

Do not add videos, tracks, automation, or a big curriculum yet. Put this in front of someone and see where they get stuck.
