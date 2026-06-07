# Agent Brief

## Purpose

What project improvement should this run make?

> 

## Aim

What outcome or behavior change does this serve?

> 

## Problem statement

What problem framing did we select?

> 

## Selected solution level

Choose one:

- [ ] Band-Aid
- [ ] Local Optimum
- [ ] Reframe
- [ ] Redesign

Why this level?

> 

Why not the other levels?

- Band-Aid:
- Local Optimum:
- Reframe:
- Redesign:

## Small strategy

**Mechanism:** Why should this approach move the aim?

> 

**Feedback:** What signal will show quickly whether it worked?

> 

**Guardrails:** What must not break or drift?

- 
- 
- 

## Context

The agent should inspect:

- 
- 
- 

Relevant constraints:

- 
- 
- 

Prior attempts, symptoms, or review comments:

- 
- 
- 

## Behavior contract

The change must:

- 
- 
- 

The change must not:

- 
- 
- 

## Checks

Commands to run:

```bash

```

Acceptance checks:

- 
- 
- 

Old behavior these checks should catch:

- 
- 
- 

## Stop conditions

The agent should stop and report instead of guessing if:

- the selected problem framing is wrong;
- required files or commands are missing;
- the patch requires a broader redesign than this slice allows;
- tests cannot be made meaningful without changing the brief;
- implementation would touch unrelated systems.

## Review checklist

Before accepting output, check:

- [ ] Does it serve the aim?
- [ ] Did it stay at the selected solution level?
- [ ] Is the mechanism visible in the code or tests?
- [ ] Do checks fail on the old behavior?
- [ ] Did the agent run the right commands?
- [ ] Are edge cases named and tested?
- [ ] Did it avoid parallel paths or compatibility shims?
- [ ] Are unrelated changes absent?
- [ ] Is the result easier for the next maintainer to edit?
