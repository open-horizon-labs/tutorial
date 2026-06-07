# Further Reading

Do the tutorial first. Read these when you hit a specific problem.

## Core

- [`docs/curriculum.md`](curriculum.md) — the module map: LLM-development skills first, Open Horizons corpus applied second.
- [`docs/intent-engineering.md`](intent-engineering.md) — clarify intent, burst, pause, structure, iterate.
- [`docs/authoring-skills.md`](authoring-skills.md) — write reusable `SKILL.md` procedures.
- [`docs/subagents.md`](subagents.md) — write bounded role agents with scoped tools.
- [`docs/knowledge-extraction.md`](knowledge-extraction.md) — record metis, signals, guardrails, outcome updates, and ADRs.
- [`docs/open-horizons.md`](open-horizons.md) — how the full loop applies to LLM development.
- [`docs/strategy-clarity.md`](strategy-clarity.md) — how aim, mechanism, feedback, guardrails, and solution level become an agent brief.
- [`docs/beyond-nearest-peak.md`](beyond-nearest-peak.md) — why cheap generation should change how you search for solutions.

## Strategy background

- [Alignment Is the Constraint](https://muness.com/posts/alignment-is-the-constraint/) — aim, mechanism, feedback, and guardrail before speed.
- [Documenting Strategy: Lessons from Leading Data and Engineering Teams](https://muness.com/posts/documenting-strategy-lessons-from-leading-data-and-eng/) — vision, stakeholder needs, context, strategy, tactics, and connected work.
- [Real-World Application of Strategic Clarity in Platform Leadership](https://muness.com/posts/real-world-application-of-strategic-clarity-in-platform-leadership/) — outcomes, mechanisms, updates, feedback, and ownership in a platform team.

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
If the agent only proposes one fix, read Beyond the Nearest Peak.  
If the agent ignores needed context, read The Context Stack.  
If repeated instructions keep getting pasted, write a skill.  
If role boundaries keep blurring, write a subagent.  
If the same lesson keeps being rediscovered, record metis, a signal, a guardrail, an outcome update, or an ADR.  
If you accept the first plausible implementation, read Dissent Mode.  
If the run goes sideways, read The Salvage Loop.
