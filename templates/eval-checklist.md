# Evidence Checklist

Define the evidence before asking the agent to implement.

## Aim

> 

## Selected problem statement

> 

## Selected solution level

- [ ] Band-Aid
- [ ] Local Optimum
- [ ] Reframe
- [ ] Redesign

## Behavior or invariant

The system must:

- 
- 
- 

The system must reject, prevent, or avoid:

- 
- 
- 

## Regression case

What old behavior should fail after this change?

```text

```

Why this matters:

- 
- 

## Checks to add or update

- [ ] Unit test:
- [ ] Integration test:
- [ ] End-to-end or manual reproduction:
- [ ] Static check / lint / typecheck:
- [ ] Build or migration check:
- [ ] Documentation or runbook update:

## Failure modes

The output fails if it:

- suppresses the symptom without addressing the selected problem;
- changes unrelated behavior;
- adds a second way to do the same thing;
- weakens existing tests;
- relies on mocks where production behavior matters;
- hides errors behind broad fallbacks;
- cannot explain what would prove the patch wrong.

## Human checks

I still have to check:

- [ ] whether the selected solution level was right;
- [ ] whether tests prove behavior, not implementation details;
- [ ] whether the patch reduces future change risk;
- [ ] whether a maintainer would understand the boundary;
- [ ] whether I am accepting confidence instead of evidence.

## Fast feedback signal

I will know this is working if:

> 
