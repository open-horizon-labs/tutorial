# Intent Engineering

Intent Engineering is the first lesson because it names the failure mode.

Fast AI iteration feels productive. Without checkpoints, it becomes motion without steering: unvetted advice, local hacks, hidden assumptions, and fixes that make the next fix harder.

The rhythm is:

```text
Clarify intent → Burst → Pause and reflect → Structured pass → Iterate
```

## Clarify intent

Write one sentence before touching code.

Weak:

```md
Use an agent to clean up notifications.
```

Better:

```md
Make future notification changes safer by moving duplicate prevention to the boundary where sends happen.
```

The sentence should name the outcome, not the activity.

## Burst

Use the model for cheap breadth:

- likely causes;
- plausible solution levels;
- risks;
- files to inspect;
- checks that would fail the wrong patch.

Do not commit during the burst. Generate, then pause.

## Pause and reflect

Ask:

- Is this necessary for the intent?
- Is it sufficient?
- What assumption does it depend on?
- What would prove it wrong?
- What work is tempting because it is nearby, not because it matters?

This is where `/problem-space`, `/problem-statement`, and `/solution-space` enter.

## Structured pass

Convert the best current understanding into artifacts:

- aim;
- problem-space map;
- problem statement;
- solution-space comparison;
- evidence checklist;
- agent brief.

The artifact matters because another skill, subagent, or future session can inherit intent without re-inferring it from chat history.

## Iterate

After execution, do not ask only “did it work?” Ask:

- What evidence says it worked?
- What did review find?
- What did dissent challenge?
- What should become a skill, subagent, guardrail, metis, signal, or salvage note?

Intent Engineering is not slower work. It is the control system that lets speed stay useful.
