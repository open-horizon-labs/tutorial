# Evidence and Evals

Evidence is the boundary between useful agent work and polished guessing.

Define evidence before delegation. If the check is invented after the patch, it will often prove the patch instead of the behavior.

## Learn

An eval is a decision tool. It should say whether a change is good enough for the purpose at hand, not whether the model or agent is good in the abstract.

The SLO framing helps: define the service level indicator, the threshold, and what you do when the threshold is missed.

| SLO concept | Eval equivalent | Example |
|---|---|---|
| Fitness for purpose | The behavior this output must support. | Maintainers can tell whether duplicate notification prevention moved to the send boundary. |
| SLI | Observable measure of quality or risk. | Same recipient plus same idempotency key produces one send and one duplicate-skip record. |
| SLO | Target that is good enough for this slice. | All boundary-level duplicate cases pass; no unrelated notification timing changes. |
| Error budget | Tolerated failure before action changes. | One flaky exploratory case may remain; a regression in the core idempotency case blocks delegation. |
| Error budget policy | Decision when the budget is exhausted. | Stop implementation, inspect traces, and revise the problem statement or solution level. |

Good evals are small, specific, and tied to the user's purpose. Start with one to three quality dimensions. Add more only when the current checks are stable and useful.

## What mature eval guides add

| Practice | Why it matters here |
|---|---|
| Define the objective first. | Prevents tests that merely prove the patch. |
| Use a dataset or fixture set. | Makes behavior comparable across prompt, model, or implementation changes. |
| Include typical, edge, adversarial, and negative cases. | One-sided evals overfit; the system learns when to act but not when to abstain. |
| Choose the cheapest reliable grader. | Prefer code or state checks when possible, model graders when nuance matters, human review for calibration. |
| Grade outcomes before transcripts. | The agent can take a different valid path; the final state matters most. |
| Read transcripts and failures. | A low score may reveal a bad agent, ambiguous task, broken grader, or unfair harness. |
| Separate capability from regression. | Capability evals ask what is newly possible; regression evals protect behavior already won. |
| Keep suites alive. | Production logs, bug reports, review findings, and salvage notes should grow the eval set. |

## Eval ladder

Use the smallest rung that can catch the failure:

| Rung | Use when | Example |
|---|---|---|
| Manual check | Automation would be fake or too expensive. | Reproduce a UI flow and capture observed behavior. |
| Deterministic test | Behavior has a clear pass/fail condition. | Unit, integration, static, build, migration, or state check. |
| Fixture set | A prompt, agent, or workflow must handle repeated scenarios. | Happy path, missing context, ambiguous input, conflicting sources, instruction inside data. |
| Rubric or model grader | Output quality is open-ended but criteria are explicit. | Grade groundedness, coverage, tone, or reasoning against a rubric. |
| Experiment suite | You need to compare versions over a stable dataset. | Run old prompt versus new prompt over the same examples. |
| Production signal | Real-world quality matters after shipping. | Alert when duplicate-skip records spike or support reports repeat. |

## Practice

Use [`templates/eval-checklist.md`](../templates/eval-checklist.md) before `/execute`.

For each selected solution level, ask:

- What user-visible behavior or maintainer decision does this eval protect?
- What old behavior should fail now?
- What invariant should hold?
- What fixture set covers normal, edge, negative, and adversarial cases?
- What grader is cheapest and reliable enough?
- What threshold is good enough for this slice?
- What trace, transcript, log, or state should be saved for review?
- What would make the eval misleading?
- Where would mocks hide production behavior?
- What action is required if the eval fails?

| Version | Check |
|---|---|
| Weak | The notification system should be cleaner. |
| Better | Given two identical notification events with the same idempotency key, the system sends one notification and records the duplicate as skipped. |
| Better suite | The duplicate-send suite covers normal send, duplicate send, missing idempotency key, different recipients, conflicting trigger paths, and skipped-record observability. |

## Artifact

Produce an evidence checklist. It should travel into the agent brief and review.

## Review check

Reject evidence if:

- it only checks implementation details;
- it relies on mocks where production behavior matters;
- it cannot fail on the old behavior;
- it has no negative or edge case;
- it ignores the selected solution level;
- it uses an LLM grader without a rubric or calibration plan;
- it has no threshold or action policy;
- it omits a manual check when automation is not practical;
- it treats the agent's confidence as proof.

## Go deeper

- [`templates/eval-checklist.md`](../templates/eval-checklist.md) — evidence template used by the tutorial.
- [Implementing SLOs for Data Quality](https://muness.com/posts/implementing-slos-for-data-quality/) — SLI, SLO, error budget, policy, and fitness-for-purpose framing applied to quality.
- [OpenAI evaluation best practices](https://developers.openai.com/api/docs/guides/evaluation-best-practices) — eval objective, dataset, metrics, iteration, continuous evaluation, and anti-patterns.
- [Anthropic: Demystifying evals for AI agents](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents) — tasks, trials, graders, transcripts, outcomes, capability versus regression evals, and eval maintenance.
- [Anthropic eval cookbook](https://github.com/anthropics/anthropic-cookbook/blob/main/misc/building_evals.ipynb) — prompt, output, golden answer, score, and code/model/human grading methods.
- [OpenAI eval build guide](https://github.com/openai/evals/blob/main/docs/build-eval.md) — datasets, reference answers, eval templates, model-graded evals, and meta-evals.
- [Phoenix Iterative Evaluation & Experimentation Workflow](https://arize.com/docs/phoenix/cookbook/ai-engineering-workflows/iterative-evaluation-and-experimentation-workflow-python) — tracing, datasets, evaluators, experiments, and iterative improvement.
- [Dissent Mode](https://muness.com/posts/dissent-mode/) — why passing checks still deserves adversarial review.


---

## Navigation

- Previous: [Beyond the Nearest Peak](beyond-nearest-peak.md)
- Up: [Docs Home](index.md) / [Curriculum](curriculum.md)
- Next: [Agent Briefs](agent-briefs.md)
