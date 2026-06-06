# Open Horizons in This Repo

Open Horizons is not the command pack. The commands are wrappers around signals.

The full frame is:

> Clarify direction, nurture strengths, and maintain momentum through nested feedback loops.

For coding with agents, I use it this way:

> Know what the work is for. Run the smallest useful pass. Reflect hard enough that the next pass is better.

Short version:

```text
Aim → Do → Reflect
```

## Frame, ritual, skill

| Layer | Meaning here |
|---|---|
| Frame | The judgment loop that keeps work aligned. |
| Ritual | A repeatable move that leaves a signal. |
| Skill | A command wrapper around the ritual. |

The distinction matters.

If `/review` goes away, you still need review. If `/salvage` goes away, you still need to stop dragging bad code forward. Do not confuse the wrapper for the work.

## What we keep

### Reality first

Open Horizons starts from evidence, not aspiration.

Here, the evidence is code and tests. The agent either implements the contract or it does not. The tests either catch bad work or they do not. A confident summary is not evidence.

### A model worth copying

The Microsoft tutorial gives us a small coding task. We keep that.

Then we add the parts that make the work safer: aim, constraints, evals, review, dissent, salvage.

### A real horizon

The goal is not to learn base62.

The goal is to become the kind of builder who can direct agents without handing over judgment.

### Plans that can change

The plan is small:

1. define behavior;
2. write checks;
3. brief the agent;
4. run the work;
5. review;
6. adjust.

If a step is too heavy for your setting, shrink it. Do not remove the signal.

### Loops at different scales

| Scale | Signal |
|---|---|
| Code | Examples, invalid inputs, round trips. |
| Agent run | Did it read files, follow constraints, and run checks? |
| Session | What did review, dissent, and salvage find? |
| Practice | What brief or eval should survive into the next task? |

## Strategy for one task

Alignment is the constraint. Speed just makes misalignment louder.

For a small coding task, strategy can fit in four fields:

| Field | Question |
|---|---|
| Aim | What outcome are we trying to create? |
| Mechanism | Why should this approach work? |
| Feedback | What signal tells us quickly if it is wrong? |
| Guardrail | What must not break while we move? |

The agent brief should carry those answers. Otherwise the agent has a task, but not enough context to make tradeoffs.

When reviewing the brief, ask:

- Is this necessary for the aim?
- Is this a plausible way to move the aim?
- Is a key piece missing?
- Does each file, test, and instruction connect back to the mechanism?

See `docs/strategy-clarity.md` for the strategy piece.

## What this does not include

This is not the full Open Horizons personal worksheet. It does not ask you to reflect on years of achievements, name your strengths, affirm a mission, or set quarterly aims.

Those belong in the full frame. This repo uses the part needed for coding with agents: aim, do, reflect, and preserve the signals that keep the work honest.

## Translation table

| Open Horizons idea | Coding translation |
|---|---|
| Aim with clarity | Say what behavior change the work should create. |
| Planning over plans | Explore a few paths, then choose the smallest useful one. |
| Sustain momentum | Run a bounded pass; stop when the work drifts. |
| Growth mindset | Treat bad agent output as evidence. Fix the loop. |
| Use strengths | Keep human taste, context, and standards in the work. |
| Reflect | Review, dissent, salvage, and save what improves the next run. |

Skills make the loop easier to run. They are not the loop.

The rule to keep: do not ask the agent to write code until you know what signal will tell you whether the code is good.
