# What Open Horizons Adds

Open Horizons keeps an agent run from becoming “ask for patch, accept patch.”

For LLM development, the sequence is:

```text
Intent Engineering → context pack → /aim → /problem-space → /problem-statement → /solution-space → evidence → brief → skill → subagent → /execute → /review → /dissent → knowledge extraction → /salvage
```

The reason is simple: do not assign work until you know what good means, what context the agent should inherit, what role boundary it needs, and what should survive after the session.

## Evidence first

Here, evidence is not the agent's confidence.

Evidence is:

- failing behavior reproduced;
- tests that fail before the fix and pass after;
- static checks;
- build output;
- review findings;
- deleted duplicate paths;
- clarified ownership;
- a smaller blast radius;
- a salvage note that prevents repeating the same mistake.

## What each tool does

| Tool | Job in this repo |
|---|---|
| Intent Engineering | Clarify intent, burst, pause, structure, and iterate. |
| Context pack | Preserve selective context before delegation. |
| `/aim` | Name the outcome before the agent ranks work. |
| `/problem-space` | Map terrain: systems, stakeholders, constraints, blast radius, assumptions. |
| `/problem-statement` | Choose the framing that points to the right class of fix. |
| `/solution-space` | Compare Band-Aid, Local Optimum, Reframe, and Redesign paths. |
| Evidence checklist | Define checks before implementation. |
| Project skill | Preserve a repeated procedure as `SKILL.md`. |
| Subagent | Preserve a role boundary with scoped tools and isolated context. |
| `/execute` | Implement one selected slice from a brief. |
| `/review` | Judge the patch against the aim and checks. |
| `/dissent` | Look for the way the accepted-looking patch still fails. |
| Knowledge extraction | Record metis, signals, guardrails, outcome updates, or ADRs. |
| `/salvage` | Keep learning when the run drifted and restart smaller. |

## Strategy for one slice

The agent brief should carry four fields:

| Field | Question |
|---|---|
| Aim | What outcome are we trying to create? |
| Mechanism | Why should this approach move that outcome? |
| Feedback | What signal tells us quickly if it is wrong? |
| Guardrail | What must not break while we move? |

If the brief only says what to change, it is missing the strategy.

## Solution levels

This is where Open Horizons meets `Beyond the Nearest Peak`.

A real project problem usually has more than one altitude:

- Band-Aid: suppress the symptom;
- Local Optimum: improve the current design;
- Reframe: change the problem statement;
- Redesign: make the class of failure harder to create.

The selected level should show up in the brief and in review.

If you choose a Band-Aid, say why speed or risk makes that acceptable. If you choose Redesign, say why the recurrence justifies the blast radius.

## Signals at different scales

| Scale | Signal |
|---|---|
| Code | Regression tests, integration tests, static checks, deleted duplicate paths. |
| Agent run | Did it read the right files, follow the brief, run checks, and stop on drift? |
| Skill | Did the repeated procedure become easier to invoke correctly? |
| Subagent | Did the role boundary produce better evidence or lower context load? |
| Knowledge artifact | Did a future run inherit a verified learning instead of rediscovering it? |
| Review | Did the patch move the aim at the selected solution level? |
| Practice | Which rejected path, check, guardrail, or metis should survive into the next run? |

Shrink a step if needed. Do not remove the signal.
