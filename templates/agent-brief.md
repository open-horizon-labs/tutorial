# Agent Brief

## Purpose

What should the agent build or change?

> 

## Aim

What behavior change or learning does this serve?

> 

## Small strategy

**Mechanism:** Why should this approach work?

> 

**Feedback:** What signal will show quickly whether it is working?

> 

**Guardrails:** What must not break or drift?

- 
- 
- 

**Alignment check:**

- Necessity: why is this needed?
- Viability: why should this work?
- Sufficiency: what is still missing?
- Connectedness: how do the files and tests below connect back to the aim?

## Files

The agent should inspect:

- 
- 
- 

The agent may create or edit:

- 
- 
- 

## Behavior contract

The code must:

- 
- 
- 

The code must reject or avoid:

- 
- 
- 

## Tests and evals

Required checks:

- 
- 
- 

Bad outputs these checks should catch:

- 
- 
- 

## Constraints

The agent must:

- read relevant files before editing;
- keep the change small;
- reuse existing patterns;
- run the relevant tests;
- explain any blocker instead of guessing.

The agent must not:

- add unrelated features;
- weaken tests to pass;
- hide errors behind broad fallbacks;
- claim correctness without evidence.

## Failure modes

Watch for:

- plausible but wrong code;
- missing edge cases;
- tests that only check happy paths;
- behavior that is not documented;
- extra abstractions the task did not earn;
- review summaries that skip findings.

## Review checklist

Before accepting output, check:

- [ ] Does it serve the aim?
- [ ] Is the mechanism clear?
- [ ] Are feedback signals explicit?
- [ ] Are guardrails explicit?
- [ ] Does it implement the behavior contract?
- [ ] Do tests catch known bad implementations?
- [ ] Did the agent run the right checks?
- [ ] Are edge cases named and tested?
- [ ] Are there unrelated changes?
- [ ] Is the result simple enough to maintain?
