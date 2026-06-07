# Authoring Skills

A skill is how a repeated procedure survives the chat.

Use a skill when you keep pasting the same checklist, project rule, review process, or implementation recipe into the agent.

Do not create a skill for generic advice. Create one when local procedure matters.

## What a skill is for

A skill preserves a **workflow**:

- when to use it;
- what to inspect;
- what constraints matter;
- what output shape must be produced;
- what evidence is required before the work is done;
- what should trigger stop, dissent, or salvage.

It should be short enough to load and specific enough to change behavior.

## When to author one

Create a project skill when:

- a review checklist repeats;
- a fragile command sequence must be run correctly;
- a recurring bug class needs the same evidence every time;
- project context has grown into a procedure;
- a session produced a useful pattern that should survive.

Do not create one when:

- the instruction is a one-off;
- the model already knows the concept;
- the skill would only restate generic advice;
- the real need is a subagent role, not a workflow.

## Minimal shape

Project skills live at:

```text
.claude/skills/<skill-name>/SKILL.md
```

The command name comes from the directory name.

Use `templates/project-skill.md` as the starting point.

A useful skill starts with a trigger:

```yaml
---
description: Reviews notification changes for idempotency boundaries and duplicate-send risk. Use when notification send logic, event handlers, or notification tests change.
---
```

Then a short process:

1. Inspect notification send boundaries and caller paths.
2. Check whether duplicate prevention belongs at the boundary or caller.
3. Require a regression check that fails on duplicate sends.
4. Reject patches that add another caller-specific guard while leaving the boundary unprotected.
5. Report findings with file references and command evidence.

## Authoring rules

- Put the trigger in the description.
- Keep `SKILL.md` hot-path sized.
- Move rare details into supporting files.
- Match detail to risk: fragile operations get exact commands; judgment work gets criteria.
- Include stop conditions.
- Include output shape.
- Include verification.
- Test the skill against the repo before trusting it.

## How this connects to the loop

| Loop step | Skill job |
|---|---|
| Intent | Preserve what the work is for. |
| Problem framing | Preserve how to map terrain. |
| Solution search | Preserve how to compare levels and retire risks. |
| Evidence | Preserve checks that should fail the tempting wrong patch. |
| Delegation | Preserve the handoff contract. |
| Verification | Preserve commands, repro steps, and review criteria. |
| Dissent | Preserve known failure modes. |
| Salvage | Preserve learning and restart shape. |

A useful skill stops the next session from rediscovering the same procedure.


## Exercise

Turn one repeated instruction from your project into a skill:

1. Name the trigger.
2. Write the shortest process that changes agent behavior.
3. Add stop conditions.
4. Add evidence requirements.
5. Test whether the skill would reject the tempting wrong output.

## Go deeper

- [Claude Code Skills](https://code.claude.com/docs/en/skills) — official mechanics for `SKILL.md`, supporting files, and invocation.
- [Anthropic skill authoring guide](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices) — progressive disclosure, concise descriptions, and testing.
- [`templates/project-skill.md`](../templates/project-skill.md) — project skill template used by this tutorial.
- [`docs/subagents.md`](subagents.md) — when the repeated need is a role boundary rather than a workflow.


---

## Navigation

- Previous: [Strategy Clarity](strategy-clarity.md)
- Up: [Docs Home](index.md) / [Curriculum](curriculum.md)
- Next: [Authoring Subagents](subagents.md)
