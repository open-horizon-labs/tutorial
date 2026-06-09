# Prompt Assembly Template

Use this after the model-fit note and context pack, before asking an LLM or agent for output.

## Objective

What decision, behavior, or artifact should this output support?

>

## Model job

What language operation should the model perform?

- [ ] extract structure from supplied material
- [ ] compare options against criteria
- [ ] classify against explicit categories
- [ ] rewrite for a known audience or voice
- [ ] critique against a checklist
- [ ] generate candidates inside constraints
- [ ] translate between domains, vocabularies, or levels of detail
- [ ] other:

## Supplied context

| Context item | Provenance | Why it belongs in the prompt |
|---|---|---|
|  |  |  |
|  |  |  |
|  |  |  |

## Boundaries

In scope:

- ...

Out of scope:

- ...

Must not infer:

- ...

Missing context should be handled by:

- ...

## Output contract

Format:

- ...

Required sections or fields:

- ...

Evidence requirement:

- ...

Missing-context section:

- ...

## Reviewer checks

How will a person reject fluent but ungrounded output?

- ...
- ...
- ...

## Final ask

Write the final request in prose. Keep it short enough that a reviewer can see what was included, what was excluded, and what the model should do when context is missing.
