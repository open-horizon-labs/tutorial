# What Open Horizons Adds

Open Horizons keeps an agent run from becoming “ask for patch, accept patch.”

For LLM development, the sequence has four arcs:

| Arc | Steps |
|---|---|
| Grounding | Intent Engineering → model-fit note → context pack |
| Framing | `/aim` → `/problem-space` → `/problem-statement` → `/solution-space` |
| Delegation | evidence → brief → skill decision → subagent decision → `/execute` |
| Reflection | `/review` → `/dissent` → knowledge extraction → `/salvage` |

The reason is simple: do not assign work until you know what good means, what language operation the model should perform, what context it should inherit, what role boundary it needs, and what should survive after the session.

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
| Model-fit note | Name the model job — extract, compare, classify, rewrite, critique, generate candidates, or translate — and the context it must be supplied rather than asked to guess. |
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


## Exercise

Take a planned agent run and mark where each gate happens:

1. intent;
2. model-fit note;
3. context pack;
4. aim;
5. problem space;
6. problem statement;
7. solution search;
8. evidence;
9. brief;
10. skill decision;
11. subagent decision;
12. execute;
13. review;
14. dissent;
15. extraction;
16. salvage.

If a gate has no artifact, decide whether it is unnecessary for this slice or whether the run is relying on implicit judgment.

## Go deeper

- [Open Horizons](https://muness.com/posts/open-horizons/) — the source framing for aim, do, reflect, and nested feedback.
- [`docs/curriculum.md`](curriculum.md) — overview map of modules, artifacts, deep dives, and references.
- [`docs/execution-review-salvage.md`](execution-review-salvage.md) — the inner execution loop.


---

## Navigation

- Previous: [Context Construction](context-construction.md)
- Up: [Docs Home](index.md) / [Curriculum](curriculum.md)
- Next: [Problem Space](problem-space.md)
