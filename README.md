# LLM Development Skills, Open Horizons Applied

This repo teaches practical LLM-based development in existing systems: how to shape the task, supply context, choose the right solution level, verify the work, and preserve what the next session needs.

The shape is:

```text
Intent → Model-fit framing → Context construction → Problem framing → Solution search → Evidence → Delegation → Verification → Dissent → Knowledge extraction → Salvage
```

The first layer is the skill curriculum: intent engineering, model-fit framing, context construction, Open Horizons phase skills, skill authoring, subagents, evidence, review, dissent, knowledge extraction, and salvage.

The second layer applies Muness Castle's Open Horizons philosophy corpus to those skills: LLM Prompt Types, Alignment Is the Constraint, Intent Engineering, Beyond the Nearest Peak, The Context Stack, Dissent Mode, the Salvage Loop, and strategy-clarity writing.

## What you learn

You will learn how to:

1. state intent before asking for output;
2. reframe tasks so the model transforms supplied context instead of guessing missing facts;
3. build a context pack instead of dumping context;
4. use Open Horizons skills as phase gates;
5. search across solution levels before implementing;
6. write evidence checks before delegation;
7. author project skills for repeated procedures;
8. author subagents for bounded roles;
9. delegate one implementation slice;
10. verify and review against the aim;
11. run dissent before acceptance;
12. extract durable knowledge into `.oh/` artifacts;
13. salvage learning when the run drifts.

## Why skills, subagents, and extraction

A loop written in prose is not enough.

Skills make procedures reusable:

```text
how to frame → how to search → how to check → how to review → how to salvage
```

Subagents make roles enforceable:

```text
scout → implementer → reviewer → dissenter → extractor
```

Knowledge extraction makes learning durable:

```text
metis → signal → guardrail → outcome update → ADR
```

Those are the tools that make the Open Horizons loop real.

## Quick start

Install the Open Horizons skills:

```bash
npx skills add open-horizon-labs/skills -g -a claude-code -y
```

Then use the study path:

- [`docs/curriculum.md`](docs/curriculum.md) — start with the overview table.
- [`docs/model-fit.md`](docs/model-fit.md) — learn how to shape asks around model strengths and supplied context.
- Use the named deep-dive links in [`docs/curriculum.md`](docs/curriculum.md#overview-curriculum) when a skill becomes the bottleneck.
- [`docs/further-reading.md`](docs/further-reading.md) — follow source references when the deep dive is not enough.
- [`docs/tutorial.md`](docs/tutorial.md) — apply the full loop to a real project slice.

## Repo map

- [`docs/curriculum.md`](docs/curriculum.md) — overview curriculum: skills, artifacts, deep dives, and go-deeper references.
- [`docs/tutorial.md`](docs/tutorial.md) — the hands-on run through the curriculum and capstone.
- [`docs/intent-engineering.md`](docs/intent-engineering.md) — intent, burst, pause, structured pass, iterate.
- [`docs/model-fit.md`](docs/model-fit.md) — shape asks around model strengths and supplied context.
- [`docs/context-construction.md`](docs/context-construction.md) — selective context packs, provenance, constraints, and stop triggers.
- [`docs/open-horizons.md`](docs/open-horizons.md) — how the phase skills fit the curriculum.
- [`docs/problem-space.md`](docs/problem-space.md) — why problem framing needs real terrain.
- [`docs/beyond-nearest-peak.md`](docs/beyond-nearest-peak.md) — shallow breadth, score, select, deepen.
- [`docs/evidence-and-evals.md`](docs/evidence-and-evals.md) — checks before delegation and evals that can fail.
- [`docs/agent-briefs.md`](docs/agent-briefs.md) — turning selected solution into execution contract.
- [`docs/authoring-skills.md`](docs/authoring-skills.md) — how and when to write `SKILL.md` procedures.
- [`docs/subagents.md`](docs/subagents.md) — how and when to write `.claude/agents/*.md` roles.
- [`docs/execution-review-salvage.md`](docs/execution-review-salvage.md) — execute, review, dissent, drift detection, and salvage.
- [`docs/knowledge-extraction.md`](docs/knowledge-extraction.md) — metis, signals, guardrails, outcome updates, ADRs.
- [`docs/strategy-clarity.md`](docs/strategy-clarity.md) — aim, mechanism, feedback, guardrails, and solution level.
- [`docs/further-reading.md`](docs/further-reading.md) — source material and follow-up reading.
- [`templates/context-pack.md`](templates/context-pack.md) — selective context before delegation.
- [`templates/model-fit-note.md`](templates/model-fit-note.md) — starting point for a model-fit note.
- [`templates/project-skill.md`](templates/project-skill.md) — starting point for a project skill.
- [`templates/subagent.md`](templates/subagent.md) — starting point for a project subagent.
- [`templates/knowledge-artifact.md`](templates/knowledge-artifact.md) — starting point for durable `.oh/` artifacts.
- [`templates/agent-brief.md`](templates/agent-brief.md) — handoff contract for implementation.
- [`templates/eval-checklist.md`](templates/eval-checklist.md) — evidence before delegation.
- [`templates/builder-playground.md`](templates/builder-playground.md) — choose a real project slice.
- [`examples/technical-debt-agent-brief.md`](examples/technical-debt-agent-brief.md) — worked duplicate-notification example.

## What Good Looks Like

The work produces a loop a maintainer can inspect: intent, model fit, context, procedure, role boundary, evidence, review, extraction, and salvage.

## What Good Does Not Look Like

- A prompt cheat sheet.
- A tour of agent UI buttons.
- A claim that agents can decide what matters for you.
- Memory that silently becomes policy.
- Technical-debt ranking handed to a model without human judgment.

## Source material

The project-improvement shape comes from GitHub's [Using GitHub Copilot cloud agent to improve a project](https://docs.github.com/en/copilot/tutorials/cloud-agent/improve-a-project).

The philosophy layer comes from Muness Castle's Open Horizons corpus: [LLM Prompt Types](https://muness.com/posts/llm-prompt-types/), [Intent Engineering](https://muness.com/posts/intent-engineering/), [Open Horizons](https://muness.com/posts/open-horizons/), [Alignment Is the Constraint](https://muness.com/posts/alignment-is-the-constraint/), [Beyond the Nearest Peak](https://muness.com/posts/beyond-the-nearest-peak/), [The Context Stack](https://muness.com/posts/the-context-stack/), [Dissent Mode](https://muness.com/posts/dissent-mode/), and the strategy-clarity essays.
