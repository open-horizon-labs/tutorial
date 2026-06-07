# Model-Fit Framing

Model-fit framing shapes the task so the model uses its strengths: extracting structure, comparing options, rewriting for an audience, critiquing against criteria, or translating supplied context into a checkable artifact.

A generic summary can look useful because it is fluent. Fluency is not grounding. When the output depends on company context, project history, names, prior decisions, or active aims, those facts belong in the input. Missing context belongs in the output as missing context.

The boundary:

| Weak | Strong |
|---|---|
| Ask the model to supply missing reality. | Ask the model to transform supplied reality. |

## What models are good at

LLMs are useful when the task is a language operation over supplied material:

- summarize with a named lens;
- classify against explicit categories;
- compare options against criteria;
- rewrite for a known audience or voice;
- translate between domains, vocabularies, or levels of detail;
- generate candidate options inside constraints;
- critique an artifact against a checklist;
- extract decisions, risks, owners, and open questions.

Each operation needs context, an output contract, and a way to check the result.

## Where they fail

Do not ask the model to infer private context from public words.

It will try. That is the danger.

Weak tasks usually ask for:

- facts not present in the context;
- private organizational meaning;
- final judgment without criteria;
- commitments from ambiguous language;
- confidence without evidence;
- a clean answer where the honest answer is “missing context.”

Better adjectives do not fix the prompt. Change the task shape.

## Example: meeting notes

A Zoom-style auto-summary gets the transcript and produces a topic summary. That uses one model strength: compression. It misses the work that matters.

A useful meeting note is grounded in the organization:

| Input | Why it matters |
|---|---|
| Transcript | The raw conversation. |
| Attendees and roles | Who can commit, decide, or own follow-up. |
| Active aims, projects, programs, and customer commitments | The big picture the note must tie back to. |
| Company vocabulary | Names and concepts the model should not invent or blur. |
| Prior decisions | Context for what is settled versus reopened. |
| Known guardrails and risks | Constraints the note should surface conflicts against. |
| Desired output artifact | The shape reviewers need. |

Then the model can do a better-shaped task: produce meeting notes that map discussion to active aims, separate decisions from proposals, list action items with evidence, identify risks and missing context, flag guardrail conflicts, and end with what a future agent or reviewer would need to continue.

Supplied context makes the transcript checkable against roles, aims, projects, guardrails, and evidence. The model turns that context into an artifact a person can audit.

## Artifact

Use [`templates/model-fit-note.md`](../templates/model-fit-note.md).

A model-fit note should answer:

- What task are we asking the model to perform?
- Which model strength does that task use?
- What context must be supplied?
- What should the model refuse to infer?
- What output shape should it produce?
- What evidence lets a reviewer check it?

## Practice

Take the next thing you want to ask an LLM to do and write both versions.

| Version | Prompt |
|---|---|
| Weak | Summarize this meeting. |
| Better | Using the transcript and context pack, produce a decision-preserving meeting note for the platform roadmap review. Separate decisions, proposals, risks, action items, and missing context. Quote the transcript line or timestamp for every commitment. |

If the better version requires context you do not have, the task is not ready. Build the context pack before you ask for output.

## Review check

Reject a model-fit note if:

- it asks the model to know facts not supplied;
- the output shape is just “summary” or “analysis”;
- no reviewer could tell whether the result is correct;
- missing context has nowhere to appear;
- the task uses the model for final judgment instead of structured first draft.

## Go deeper

- [LLM Prompt Types](https://muness.com/posts/llm-prompt-types/) — the older prompt taxonomy: contextual, exploratory, generative, rewrite, and translation prompts fit the model better than brittle retrieval or closed-ended asks.
- [The Context Stack](https://muness.com/posts/the-context-stack/) — why the right context matters more than more context.
- [Anthropic: Effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents) — context as a finite attention resource and the case for high-signal tokens.
- [Anthropic prompting best practices](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices) — clear instructions, context, examples, structure, and grounding.
- [OpenAI prompt engineering guide](https://developers.openai.com/api/docs/guides/prompt-engineering) — structured prompts, typed inputs, examples, and evaluation for prompt behavior.
- [`docs/context-construction.md`](context-construction.md) — the next step: supplying the context the model-fit note requires.
- [`docs/knowledge-extraction.md`](knowledge-extraction.md) — deciding which grounded meeting-note findings become metis, signals, guardrails, outcome updates, or ADRs.


---

## Navigation

- Previous: [Intent Engineering](intent-engineering.md)
- Up: [Docs Home](index.md) / [Curriculum](curriculum.md)
- Next: [Context Construction](context-construction.md)
