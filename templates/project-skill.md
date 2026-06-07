# Project Skill Template

Copy this into:

```text
.claude/skills/<skill-name>/SKILL.md
```

Then replace the placeholders.

```markdown
---
description: <What this skill does and when to use it. Put the trigger here.>
---

# /<skill-name>

<One sentence: what procedure this preserves.>

## When to use

Use when:

- 
- 
- 

Do not use when:

- 
- 

## Inputs

The agent needs:

- 
- 
- 

## Process

1. 
2. 
3. 
4. 
5. 

## Stop conditions

Stop and report if:

- 
- 
- 

## Verification

Before completion, produce evidence:

- command:
- test:
- manual check:
- review criterion:

## Output

```markdown
## <Skill Output Title>

### Summary

### Evidence

### Findings or Decisions

### Follow-up / Salvage Trigger
```

## Anti-patterns

- Do not restate generic advice.
- Do not hide uncertainty.
- Do not skip verification.
- Do not continue if a stop condition fires.
```
