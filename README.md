# Working With Agents Without Losing the Plot

Most coding-agent tutorials begin at the prompt. That is already downstream of the real problem.

The real problem is judgment. What are we trying to change? What does good look like before code exists? What signal tells us the agent is wrong? What do we do when the first pass sounds confident and fails the contract?

This repo uses a small task from Microsoft's agent-first tutorial: build a Python base62 encoder/decoder. Small is useful here. You can finish it, inspect it, and still hit enough edge cases to catch plausible nonsense.

## Open Horizons here

Open Horizons is the frame. The skills are one way to run parts of it.

If you have the skills, use them. If you do not, copy the prompts. The command is not the signal. The step should leave evidence behind.

```text
Aim → Do → Reflect
```

For this repo:

1. name the aim;
2. map the problem;
3. state the behavior contract;
4. write checks before code;
5. brief the agent;
6. run the work;
7. review the output;
8. look for the failure you missed;
9. save what improves the next run.

See `docs/open-horizons.md` for the Open Horizons piece. See `docs/strategy-clarity.md` for the strategy piece.

## Who this is for

Builders.

Developers, product engineers, founders, operators, data people, platform leads, and anyone else who has to shape work and stay close enough to judge it.

You do not need to be a full-time software engineer. You do need taste and responsibility. You need to know what matters, what should be ignored, and what would make the result useful.

## What we build

We ask an agent to build:

> A Python base62 encoder/decoder with tests.

The repo produces:

1. a small Python project;
2. a one-sentence aim;
3. a small strategy: aim, mechanism, feedback, guardrail;
4. a problem map;
5. a problem statement;
6. a few possible approaches;
7. eval rules before code;
8. a brief for the agent;
9. implementation code;
10. a review result;
11. at least one dissent finding or an explicit residual risk.

Base62 is the workbench. The reusable thing is the loop.

## Quick start

If you use Open Horizons Skills:

```bash
npx skills add open-horizon-labs/skills -g -a claude-code -y
```

Then work through:

```text
docs/tutorial.md
```

If you do not use the skills, the tutorial still works. Copy the prompts into Claude Code, Cursor, Copilot, Codex, ChatGPT, or whatever you use. Treat the slash commands as section names.

## Repo map

- `docs/tutorial.md` — the runbook.
- `docs/problem-space.md` — what this repo is trying to do, and what it is refusing to become.
- `docs/open-horizons.md` — how Open Horizons shows up here.
- `docs/strategy-clarity.md` — how to turn strategy into an agent brief.
- `docs/further-reading.md` — source material and follow-up reading.
- `templates/builder-playground.md` — choose a small task worth practicing on.
- `templates/agent-brief.md` — give the agent enough structure to work.
- `templates/eval-checklist.md` — define good and bad before code.
- `examples/base62-agent-brief.md` — the worked base62 brief and eval set.

## What this is not

- Not a prompt cheat sheet.
- Not a course about agents in general.
- Not a product-management guide hiding inside a coding exercise.
- Not a vendor tutorial for one tool.
- Not a claim that agents replace judgment.

The skill is not writing perfect prompts. The skill is getting clear about the work, giving the agent the right context, and rejecting polished crap when the checks do not support it.

## Source tutorial

The seed task comes from Microsoft's [Introduction to agent-first development](https://code.visualstudio.com/learn/foundations/introduction-to-agent-first-development), which uses a Python/uv base62 encoder/decoder as a first agent task.

This repo keeps the small coding task and changes the operating model around it.
