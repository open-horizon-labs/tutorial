# Evidence and Eval Checklist

Define the evidence before asking the agent to implement.

## Aim

What user behavior, maintainer decision, or product outcome should this protect?

> ...

## Selected problem statement

> ...

## Selected solution level

- [ ] Band-Aid
- [ ] Local Optimum
- [ ] Reframe
- [ ] Redesign

## Eval objective

The eval answers this question:

> ...

The eval is useful because:

- ...

## SLO-style quality bar

| Field | Value |
|---|---|
| Fitness for purpose |  |
| SLI / observable measure |  |
| SLO / threshold |  |
| Error budget / tolerated failure |  |
| Action if budget is exhausted |  |
| Owner |  |

## Behavior or invariant

The system must:

- ...
- ...
- ...

The system must reject, prevent, or avoid:

- ...
- ...
- ...

## Fixture set

| Fixture | Input or setup | Expected outcome | Grader |
|---|---|---|---|
| Happy path |  |  |  |
| Old behavior / regression |  |  |  |
| Edge case |  |  |  |
| Negative case |  |  |  |
| Ambiguous input |  |  |  |
| Conflicting source or trigger path |  |  |  |
| Instruction inside data |  |  |  |

## Checks to add or update

- [ ] Unit test:
- [ ] Integration test:
- [ ] End-to-end or manual reproduction:
- [ ] Static check / lint / typecheck:
- [ ] Build or migration check:
- [ ] Documentation or runbook update:
- [ ] Trace, transcript, log, or state capture:

## Grading plan

| Grader type | Use? | Notes |
|---|---|---|
| Code or deterministic state check |  |  |
| Human review |  |  |
| Model grader with rubric |  |  |
| Production signal |  |  |

If using a model grader:

- [ ] rubric is explicit;
- [ ] grader has a way to return uncertain or insufficient evidence;
- [ ] sample outputs are calibrated against human judgment;
- [ ] model grader is not the only proof for high-risk behavior.

## Failure modes

The output fails if it:

- suppresses the symptom without addressing the selected problem;
- changes unrelated behavior;
- adds a second way to do the same thing;
- weakens existing tests;
- relies on mocks where production behavior matters;
- hides errors behind broad fallbacks;
- passes the grader while failing the user-visible outcome;
- cannot explain what would prove the patch wrong.

## Human checks

I still have to check:

- [ ] whether the selected solution level was right;
- [ ] whether tests prove behavior, not implementation details;
- [ ] whether the eval has positive, negative, and edge cases;
- [ ] whether the threshold is good enough without gold-plating;
- [ ] whether the patch reduces future change risk;
- [ ] whether a maintainer would understand the boundary;
- [ ] whether I am accepting confidence instead of evidence.

## Fast feedback signal

I will know this is working if:

> ...
