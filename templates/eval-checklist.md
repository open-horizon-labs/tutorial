# Eval Checklist

Define good before asking for code.

## Aim

> 

## Behavior contract

The code must:

- 
- 
- 

The code must reject or avoid:

- 
- 
- 

## Known good examples

```text

```

Why these matter:

- 
- 

## Known bad examples

```text

```

Why these should fail:

- 
- 

## Failure modes

The output fails if it:

- passes only happy-path examples;
- silently accepts invalid input;
- invents behavior not in the contract;
- changes unrelated files;
- weakens tests to pass;
- looks polished but is not correct.

## Agent checks

The agent can check:

- [ ] required files are present;
- [ ] tests cover examples and bad inputs;
- [ ] property or round-trip tests exist where useful;
- [ ] the relevant test command passes;
- [ ] failures are fixed at the root cause.

## Human checks

I still have to check:

- [ ] whether the behavior contract is the right one;
- [ ] whether tests would catch a bad implementation;
- [ ] whether the implementation is simpler than the problem;
- [ ] whether the agent added unrelated work;
- [ ] whether I am accepting confidence instead of evidence.

## Fast feedback signal

I will know this is working if:

> 
