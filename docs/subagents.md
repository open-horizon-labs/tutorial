# Authoring Subagents

A subagent is how a role survives the chat.

Use one when a bounded worker should run with its own context, tools, and instructions.

The skill preserves the procedure. The subagent preserves the role.

## When to use a subagent

Use a subagent when:

- a side investigation would flood the main context;
- a reviewer should not inherit the implementer's reasoning;
- a specialist needs a narrow tool set;
- the same role repeats across projects;
- independent work can run in parallel;
- a phase gate needs its own output contract.

Do not use a subagent when:

- the task needs the full conversation context;
- the role boundary is fake;
- the work is too ambiguous to delegate;
- the subagent would only summarize what the main agent already knows.

## What to encode

Subagents live at:

```text
.claude/agents/<name>.md
```

A subagent file has YAML frontmatter and a body prompt.

Use `templates/subagent.md` as the starting point.

Important fields:

```yaml
---
name: notification-reviewer
description: Independent reviewer for notification changes. Use after patches that modify notification send logic, event handlers, or notification tests.
tools: Read, Grep, Glob, Bash
model: sonnet
---
```

Then define:

- input contract;
- what the subagent must not receive;
- review or execution process;
- tool rules;
- output format;
- stop conditions;
- anti-patterns.

## Role boundary examples

| Role | Why isolate it |
|---|---|
| Code reviewer | Should review the diff, not the author's explanation. |
| Codebase scout | Can inspect many files without filling the main context. |
| Test-gap hunter | Looks only for missing or weak evidence. |
| Migration planner | Maps blast radius before implementation. |
| Release checker | Verifies target-environment reality before ship. |
| Domain validator | Checks local invariants that generic review misses. |
| Knowledge extractor | Preserves learning without defending the discarded work. |

## Pattern from RNA agents

The repo-native-alignment agents show the shape:

- `code-reviewer.md` defines a cold reviewer with guardrail, metis, graph-impact, and acceptance-criteria checks.
- `gen-extractor.md` defines a specialized generator for `.oh/extractors/*.toml` with validation steps and report shape.
- `dev-pipeline.md` defines a gated pipeline where phases spawn specialized agents instead of inlining everything.

Copy the role contract, not the exact wording:

```text
Input → Tool limits → Process → Gate → Output → Anti-patterns
```

## How this connects to the loop

| Loop step | Subagent role |
|---|---|
| Problem framing | Codebase scout or domain mapper. |
| Solution search | Option generator or dissenting architect. |
| Evidence | Test-gap hunter. |
| Delegation | Implementer in a bounded worktree or phase agent. |
| Verification | Independent reviewer. |
| Dissent | Contrarian reviewer with no implementation context. |
| Knowledge extraction | Extractor that records metis, signals, guardrails, and ADRs. |
| Salvage | Learning extractor. |

A subagent should make the work safer, not just more elaborate.

If the subagent cannot say what context it should receive, what tools it needs, and what output proves it did its job, do not create it yet.


## Exercise

Author one subagent that should not inherit the implementer's reasoning.

Good first choices:

- cold code reviewer;
- test-gap hunter;
- migration planner;
- knowledge extractor.

Give it only the input it needs. If it needs the whole chat to function, the role boundary is not clear enough.

## Go deeper

- [Claude Code Subagents](https://code.claude.com/docs/en/sub-agents) — official mechanics for `.claude/agents/*.md`, tool scopes, and role isolation.
- [`templates/subagent.md`](../templates/subagent.md) — project subagent template used by this tutorial.
- [`docs/knowledge-extraction.md`](knowledge-extraction.md) — the extractor role as a concrete subagent use case.
- [Dissent Mode](https://muness.com/posts/dissent-mode/) — why independent review must be allowed to contradict the main run.


---

## Navigation

- Previous: [Authoring Skills](authoring-skills.md)
- Up: [Tutorial](tutorial.md) / [Curriculum](curriculum.md)
- Next: [Execution, Review, Dissent, and Salvage](execution-review-salvage.md)
