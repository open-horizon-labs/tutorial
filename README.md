# LLM Development Skills, Open Horizons Applied

This repo is a curriculum for practical LLM-based development.

Not prompt trivia. Not a one-file coding demo. The goal is to teach the skills that let a builder use LLMs without handing over judgment.

The shape is:

```text
Intent → Problem framing → Solution search → Evidence → Delegation → Verification → Dissent → Knowledge extraction → Salvage
```

The first layer is the skill curriculum: intent engineering, context construction, Open Horizons phase skills, skill authoring, subagents, evidence, review, dissent, knowledge extraction, and salvage.

The second layer applies Muness Castle's Open Horizons philosophy corpus to those skills: Alignment Is the Constraint, Intent Engineering, Beyond the Nearest Peak, The Context Stack, Dissent Mode, the Salvage Loop, and strategy-clarity writing.

## What you learn

You will learn how to:

1. state intent before asking for output;
2. build a context pack instead of dumping context;
3. use Open Horizons skills as phase gates;
4. search across solution levels before implementing;
5. write evidence checks before delegation;
6. author project skills for repeated procedures;
7. author subagents for bounded roles;
8. delegate one implementation slice;
9. verify and review against the aim;
10. run dissent before acceptance;
11. extract durable knowledge into `.oh/` artifacts;
12. salvage learning when the run drifts.

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

```text
docs/curriculum.md          # overview curriculum
docs/<module>.md            # deep dive when that skill is the bottleneck
docs/further-reading.md     # references and go-deeper paths
docs/tutorial.md            # apply the full loop to a real project slice
```

## Repo map

- `docs/curriculum.md` — overview curriculum: skills, artifacts, deep dives, and go-deeper references.
- `docs/tutorial.md` — the hands-on run through the curriculum and capstone.
- `docs/intent-engineering.md` — intent, burst, pause, structured pass, iterate.
- `docs/context-construction.md` — selective context packs, provenance, constraints, and stop triggers.
- `docs/open-horizons.md` — how the phase skills fit the curriculum.
- `docs/problem-space.md` — why problem framing needs real terrain.
- `docs/beyond-nearest-peak.md` — shallow breadth, score, select, deepen.
- `docs/evidence-and-evals.md` — checks before delegation and evals that can fail.
- `docs/agent-briefs.md` — turning selected solution into execution contract.
- `docs/authoring-skills.md` — how and when to write `SKILL.md` procedures.
- `docs/subagents.md` — how and when to write `.claude/agents/*.md` roles.
- `docs/execution-review-salvage.md` — execute, review, dissent, drift detection, and salvage.
- `docs/knowledge-extraction.md` — metis, signals, guardrails, outcome updates, ADRs.
- `docs/strategy-clarity.md` — aim, mechanism, feedback, guardrails, and solution level.
- `docs/further-reading.md` — source material and follow-up reading.
- `templates/context-pack.md` — selective context before delegation.
- `templates/project-skill.md` — starting point for a project skill.
- `templates/subagent.md` — starting point for a project subagent.
- `templates/knowledge-artifact.md` — starting point for durable `.oh/` artifacts.
- `templates/agent-brief.md` — handoff contract for implementation.
- `templates/eval-checklist.md` — evidence before delegation.
- `templates/builder-playground.md` — choose a real project slice.
- `examples/technical-debt-agent-brief.md` — worked duplicate-notification example.

## What this is not

- Not a prompt cheat sheet.
- Not a tour of agent UI buttons.
- Not a claim that agents can decide what matters for you.
- Not a reason to let memory silently become policy.
- Not a reason to hand technical debt ranking to a model and walk away.

The skill is building the loop: intent, context, procedure, role boundary, evidence, review, extraction, salvage.

## Source material

The project-improvement shape comes from GitHub's [Using GitHub Copilot cloud agent to improve a project](https://docs.github.com/en/copilot/tutorials/cloud-agent/improve-a-project).

The philosophy layer comes from Muness Castle's Open Horizons corpus: [Intent Engineering](https://muness.com/posts/intent-engineering/), [Open Horizons](https://muness.com/posts/open-horizons/), [Alignment Is the Constraint](https://muness.com/posts/alignment-is-the-constraint/), [Beyond the Nearest Peak](https://muness.com/posts/beyond-the-nearest-peak/), [The Context Stack](https://muness.com/posts/the-context-stack/), [Dissent Mode](https://muness.com/posts/dissent-mode/), and the strategy-clarity essays.
