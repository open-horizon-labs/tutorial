# LLM Development Skills, Open Horizons Applied

This repo teaches practical LLM-based development in existing systems: how to shape the task, assemble a prompt with the right context, choose the right solution level, verify the work, and preserve what the next session needs.

Start with one real project slice. The docs help you clarify intent, supply context, turn that context into a checkable prompt, map the problem before choosing a fix, compare solution levels, define evidence, delegate a bounded slice, and preserve what the next session should remember.

Review, dissent, and salvage are anytime checks. Use review when correctness needs an external check, dissent when the accepted-looking answer rests on fragile assumptions, and salvage when the run starts drifting.

The curriculum has two layers:

- practical LLM-development skills: intent engineering, model-fit framing, context construction, prompt and context assembly, Open Horizons phase skills, skill authoring, subagents, evidence, review, dissent, knowledge extraction, and salvage;
- Open Horizons source material applied to those skills: LLM Prompt Types, Alignment Is the Constraint, Intent Engineering, Beyond the Nearest Peak, The Context Stack, Dissent Mode, the Salvage Loop, and strategy-clarity writing.

## What you learn

You will learn how to:

1. state intent before asking for output;
2. reframe tasks so the model transforms supplied context instead of guessing missing facts;
3. build a context pack instead of dumping context;
4. assemble prompts as interfaces: stable instructions, dynamic context, examples, output contract, fixtures, and reviewer checks;
5. use Open Horizons skills as phase gates;
6. map problem space before choosing a fix;
7. narrow the map to a selected problem statement;
8. search across solution levels before implementing;
9. write evidence checks before delegation;
10. author project skills for repeated procedures;
11. author subagents for bounded roles;
12. delegate one implementation slice;
13. invoke review when correctness needs an external check;
14. use dissent when an accepted-looking answer rests on fragile assumptions;
15. extract durable knowledge into `.oh/` artifacts;
16. salvage learning as soon as the run drifts.

## Why skills, subagents, and extraction

A loop written in prose is not enough.

The curriculum becomes practical through three reusable layers:

| Layer | What it makes possible | Flow it supports |
|---|---|---|
| Skills | Reusable procedures instead of one-off prompting. | Frame, search, check, review, salvage. |
| Subagents | Enforceable roles with bounded responsibilities. | Scout, implement, review, dissent, extract. |
| Knowledge extraction | Durable learning across sessions. | Metis, signal, guardrail, outcome update, ADR. |

Those are the tools that make the Open Horizons loop real.

## Quick start

Install the Open Horizons skills:

```bash
npx skills add open-horizon-labs/skills -g -a claude-code -y
```

Then use the study path:

- [`docs/index.md`](docs/index.md) — start here when you need the route through the repo.
- [`docs/curriculum.md`](docs/curriculum.md) — understand the full sequence.
- [`docs/tutorial.md`](docs/tutorial.md) — builder loop tutorial: one real project slice from aim through review and learning.
- [`docs/context-to-agent-tutorial.md`](docs/context-to-agent-tutorial.md) — focused tutorial: decide what stays context, what becomes a prompt, and what deserves a skill or subagent boundary.
- [`docs/evals-tutorial.md`](docs/evals-tutorial.md) — focused tutorial: turn evidence into fixtures, harness checks, graders, thresholds, and action policy.
- [`docs/further-reading.md`](docs/further-reading.md) — follow source references when the deep dive is not enough.

## Repo map

### Start here

- [`docs/index.md`](docs/index.md) — docs home: choose between focused tutorial paths and shared materials.
- [`docs/curriculum.md`](docs/curriculum.md) — overview curriculum: skills, artifacts, deep dives, and go-deeper references.
- [`docs/tutorial.md`](docs/tutorial.md) — builder loop tutorial for one real project slice.
- [`docs/context-to-agent-tutorial.md`](docs/context-to-agent-tutorial.md) — focused path for context, prompt assembly, skill, and subagent boundaries.
- [`docs/evals-tutorial.md`](docs/evals-tutorial.md) — focused path for eval purpose, fixture set, harness check, grader, threshold, and action policy.
- [`docs/further-reading.md`](docs/further-reading.md) — source material and follow-up reading.

### Foundations

- [`docs/intent-engineering.md`](docs/intent-engineering.md) — intent, burst, pause, structured pass, iterate.
- [`docs/model-fit.md`](docs/model-fit.md) — shape asks around model strengths and supplied context.
- [`docs/context-construction.md`](docs/context-construction.md) — selective context packs, provenance, constraints, and stop triggers.
- [`docs/prompt-and-context.md`](docs/prompt-and-context.md) — assemble prompt, context, boundaries, output contract, and reviewer checks.
- [`docs/open-horizons.md`](docs/open-horizons.md) — how the phase skills fit the curriculum.

### Framing and solution choice

- [`docs/problem-space.md`](docs/problem-space.md) — Open Horizons skill deep dive for `/problem-space`: map terrain before choosing the slice.
- [`docs/problem-statement.md`](docs/problem-statement.md) — Open Horizons skill deep dive for `/problem-statement`: narrow terrain into a selected framing.
- [`docs/beyond-nearest-peak.md`](docs/beyond-nearest-peak.md) — Open Horizons skill deep dive for `/solution-space`: shallow breadth, score, select, deepen.
- [`docs/evidence-and-evals.md`](docs/evidence-and-evals.md) — checks before delegation and evals that can fail.

### Delegation and execution

- [`docs/agent-briefs.md`](docs/agent-briefs.md) — turning selected solution into execution contract.
- [`docs/strategy-clarity.md`](docs/strategy-clarity.md) — aim, mechanism, feedback, guardrails, and solution level.
- [`docs/authoring-skills.md`](docs/authoring-skills.md) — how and when to write `SKILL.md` procedures.
- [`docs/subagents.md`](docs/subagents.md) — how and when to write `.claude/agents/*.md` roles.
- [`docs/execution-review-salvage.md`](docs/execution-review-salvage.md) — Open Horizons skill deep dive for `/execute`, `/review`, `/dissent`, drift detection, and `/salvage`.

### Durable learning

- [`docs/knowledge-extraction.md`](docs/knowledge-extraction.md) — metis, signals, guardrails, outcome updates, ADRs.

### Templates

- [`templates/builder-playground.md`](templates/builder-playground.md) — choose a real project slice.
- [`templates/model-fit-note.md`](templates/model-fit-note.md) — starting point for a model-fit note.
- [`templates/context-pack.md`](templates/context-pack.md) — selective context before delegation.
- [`templates/prompt-assembly.md`](templates/prompt-assembly.md) — starting point for an assembled prompt.
- [`templates/problem-statement.md`](templates/problem-statement.md) — selected statement, rejected framings, scope boundary, and invalidation signal.
- [`templates/eval-checklist.md`](templates/eval-checklist.md) — evidence before delegation.
- [`templates/agent-brief.md`](templates/agent-brief.md) — handoff contract for implementation.
- [`templates/project-skill.md`](templates/project-skill.md) — starting point for a project skill.
- [`templates/subagent.md`](templates/subagent.md) — starting point for a project subagent.
- [`templates/knowledge-artifact.md`](templates/knowledge-artifact.md) — starting point for durable `.oh/` artifacts.

### Examples

- [`examples/technical-debt-agent-brief.md`](examples/technical-debt-agent-brief.md) — worked duplicate-notification example.

## What Good Looks Like

The work produces a loop a maintainer can inspect: intent, model fit, context, prompt assembly, procedure, role boundary, evidence, review, extraction, and salvage.

## What Good Does Not Look Like

- A prompt cheat sheet detached from context, evidence, and reviewer checks.
- A tour of agent UI buttons.
- A claim that agents can decide what matters for you.
- Memory that silently becomes policy.
- Technical-debt ranking handed to a model without human judgment.

## Source material

The project-improvement shape comes from GitHub's [Using GitHub Copilot cloud agent to improve a project](https://docs.github.com/en/copilot/tutorials/cloud-agent/improve-a-project).

The philosophy layer comes from the Open Horizons corpus and related essays: [LLM Prompt Types](https://muness.com/posts/llm-prompt-types/), [Intent Engineering](https://muness.com/posts/intent-engineering/), [Open Horizons](https://muness.com/posts/open-horizons/), [Alignment Is the Constraint](https://muness.com/posts/alignment-is-the-constraint/), [Beyond the Nearest Peak](https://muness.com/posts/beyond-the-nearest-peak/), [The Context Stack](https://muness.com/posts/the-context-stack/), [Dissent Mode](https://muness.com/posts/dissent-mode/), and the strategy-clarity essays.
