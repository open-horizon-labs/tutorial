# Further Reading

Read these when a module is the bottleneck. The curriculum is overview first, then deep dive, then references.

## Core

- [`docs/curriculum.md`](curriculum.md) — overview map: module, artifact, deep dive, and go-deeper references.
- [`docs/intent-engineering.md`](intent-engineering.md) — clarify intent, burst, pause, structure, iterate.
- [`docs/model-fit.md`](model-fit.md) — shape asks around model strengths and supplied context.
- [`docs/context-construction.md`](context-construction.md) — construct selective context packs with provenance and stop triggers.
- [`docs/prompt-and-context.md`](prompt-and-context.md) — assemble prompt wording, selected context, boundaries, output contract, and checks.
- [`docs/open-horizons.md`](open-horizons.md) — how the full loop applies to LLM development.
- [`docs/problem-space.md`](problem-space.md) — why problem framing needs real terrain.
- [`docs/problem-statement.md`](problem-statement.md) — narrow terrain into one selected framing.
- [`docs/beyond-nearest-peak.md`](beyond-nearest-peak.md) — why cheap generation should change solution search.
- [`docs/evidence-and-evals.md`](evidence-and-evals.md) — checks before delegation and evals that can fail.
- [`docs/agent-briefs.md`](agent-briefs.md) — turn the selected solution into execution context.
- [`docs/authoring-skills.md`](authoring-skills.md) — write reusable `SKILL.md` procedures.
- [`docs/subagents.md`](subagents.md) — write bounded role agents with scoped tools.
- [`docs/execution-review-salvage.md`](execution-review-salvage.md) — execute, review, dissent, drift detection, and salvage.
- [`docs/knowledge-extraction.md`](knowledge-extraction.md) — record metis, signals, guardrails, outcome updates, and ADRs.
- [`docs/strategy-clarity.md`](strategy-clarity.md) — aim, mechanism, feedback, guardrails, and solution level.

## Strategy background

- [Alignment Is the Constraint](https://muness.com/posts/alignment-is-the-constraint/) — aim, mechanism, feedback, and guardrail before speed.
- [Documenting Strategy: Lessons from Leading Data and Engineering Teams](https://muness.com/posts/documenting-strategy-lessons-from-leading-data-and-eng/) — vision, stakeholder needs, context, strategy, tactics, and connected work.
- [Real-World Application of Strategic Clarity in Platform Leadership](https://muness.com/posts/real-world-application-of-strategic-clarity-in-platform-leadership/) — outcomes, mechanisms, updates, feedback, and ownership in a platform team.

## LLM mechanics

- [LLM Prompt Types](https://muness.com/posts/llm-prompt-types/) — prompt types, suitability, context, and evaluation criteria.
- [Anthropic: Effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents) — context as a finite attention resource.
- [Anthropic prompting best practices](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices) — clear instructions, context, examples, structure, and grounding.
- [OpenAI prompt engineering guide](https://developers.openai.com/api/docs/guides/prompt-engineering) — structured prompts, typed inputs, examples, and evaluation for prompt behavior.
- [OpenAI evaluation best practices](https://developers.openai.com/api/docs/guides/evaluation-best-practices) — eval objective, dataset, metrics, iteration, and continuous evaluation.
- [Anthropic: Demystifying evals for AI agents](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents) — agent tasks, trials, graders, transcripts, outcomes, and suite maintenance.
- [Implementing SLOs for Data Quality](https://muness.com/posts/implementing-slos-for-data-quality/) — SLI, SLO, error budget, and policy framing for quality.

## Later

- [Claude Code Skills](https://code.claude.com/docs/en/skills) — official mechanics for `SKILL.md`, supporting files, and invocation.
- [Claude Code Subagents](https://code.claude.com/docs/en/sub-agents) — official mechanics for `.claude/agents/*.md`, tool scopes, and role isolation.
- [Anthropic skill authoring guide](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices) — concise skills, progressive disclosure, descriptions, and testing.
- [Using GitHub Copilot cloud agent to improve a project](https://docs.github.com/en/copilot/tutorials/cloud-agent/improve-a-project) — the source shape for mature-project improvement.
- [Phoenix Iterative Evaluation & Experimentation Workflow](https://arize.com/docs/phoenix/cookbook/ai-engineering-workflows/iterative-evaluation-and-experimentation-workflow-python) — deeper eval work when regression tests are not enough.
- [Open Horizons Skills](https://github.com/open-horizon-labs/skills) — the phase skills used by this exercise.
- [Intent Engineering](https://muness.com/posts/intent-engineering/) — making intent explicit enough that software, agents, and people can use it.
- [The Context Stack](https://muness.com/posts/the-context-stack/) — why dumping more text into the agent is not the same as giving it the right context.
- [Dissent Mode](https://muness.com/posts/dissent-mode/) — how to look for flaws before committing.
- [The Salvage Loop](https://muness.com/posts/the-salvage-loop-keep-learning-drop-the-code/) — when the draft is wrong, keep the learning and drop the draft.

## What to read when

If your agent rushes to code, read Intent Engineering and Alignment Is the Constraint.  
If the model gives fluent but generic output, read Model-Fit Framing, Context Construction, and Prompt and Context Assembly.
If problem-space produced a map but not a slice, read Problem Statement.
If the agent only proposes one fix, read Beyond the Nearest Peak.  
If the agent ignores needed context, read The Context Stack.  
If repeated instructions keep getting pasted, write a skill.  
If role boundaries keep blurring, write a subagent.  
If the same lesson keeps being rediscovered, record metis, a signal, a guardrail, an outcome update, or an ADR.  
If you accept the first plausible implementation, read Dissent Mode.  
If the run goes sideways, read The Salvage Loop.


---

## Navigation

- Previous: [Knowledge Extraction](knowledge-extraction.md)
- Up: [Docs Home](index.md) / [Curriculum](curriculum.md)
- Next: [README](../README.md)
