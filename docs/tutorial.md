# Tutorial: Build Base62 With an Agent, Then Make It Prove It

You will use a coding agent to build a small Python base62 encoder/decoder.

The seed task comes from Microsoft's agent-first tutorial:

```text
Using Python 3.13 and uv, implement a base62 encoder/decoder.
```

That prompt is a start. It is not a contract.

We are going to add the missing parts: aim, constraints, evals, review, dissent, and salvage.

By the end, you should have:

- a tiny Python project;
- tests that catch obvious bad implementations;
- a brief an agent can use;
- a review prompt that checks the work;
- a way to recover when the first pass is wrong.

## Open Horizons here

Open Horizons is the frame. The slash-command skills are optional.

```text
Aim → Do → Reflect
```

For this repo, that becomes:

```text
Aim → Problem Space → Problem Statement → Solution Space → Evals → Brief → Execute → Review → Dissent → Salvage
```

The command names do not matter. The signals matter:

- aim before action;
- checks before trust;
- review before acceptance;
- salvage before dragging a bad draft forward.

The strategy kernel is:

```text
Aim → Mechanism → Feedback → Guardrail
```

The brief you give the agent should carry those four fields. Otherwise the agent only has a task.

Read `docs/open-horizons.md` and `docs/strategy-clarity.md` if you want the longer version. The run works without the skills installed.

## What we keep from the source tutorial

The source tutorial is useful because it separates the pieces that matter:

| Piece | How we use it |
|---|---|
| Harness | Use whatever environment you trust. It must read files, edit files, and run tests. |
| Model | Use enough reasoning for implementation and review. Do not use a weak model to judge correctness. |
| Context | Give the agent the aim, behavior contract, examples, files, and checks. More text is not automatically better. |
| Tools | Let the agent read, edit, search, and run `uv run pytest`. Skipped reads and skipped tests are warning signs. |
| Prompt | Build it from the aim, problem statement, evals, brief, and review criteria. Do not rely on one perfect sentence. |

If you are impatient, do three things: define the behavior contract, write evals before code, and review the implementation against the contract.

## Before you start

You need:

- Python 3.13 or later;
- `uv`;
- a coding agent: Claude Code, Cursor, Copilot, Codex, ChatGPT, or similar;
- 45-90 minutes;
- willingness to reject code that looks fine but fails the contract.

Optional:

```bash
npx skills add open-horizon-labs/skills -g -a claude-code -y
```

If you do not have slash commands, copy the prompts as normal messages.

## Step 0: Create the playground

Create a small Python project:

```bash
uv init base62-agent-playground --package --python 3.13 --no-readme
cd base62-agent-playground
uv add --dev pytest hypothesis
```

This gives the agent a small workspace with dependencies, tests, and a package shape.

Do not start with code. Start with what the task is for.

## Step 1: Name the aim

Use `/aim` if you have it. Otherwise paste:

```md
I want to define the aim for a small coding-agent exercise.

Task:
Build a Python base62 encoder/decoder with tests.

What I want to learn:
How to direct a coding agent through a small implementation, define checks before code, and review the result instead of trusting the first pass.

Success looks like:
- code implements the agreed behavior;
- tests catch obvious bad implementations;
- the agent can explain what it changed and why;
- I can tell whether the result is acceptable.

Please produce:
- one concise aim;
- why it matters;
- the bet I am making;
- assumptions;
- a fast feedback signal;
- the mechanism;
- guardrails.
```

Expected result:

```md
Aim: Learn to direct a coding agent through a small implementation by making behavior, tests, and review criteria explicit before the agent writes code.
Mechanism: A behavior contract plus evals gives the agent a concrete target and gives the human a way to reject plausible wrong code.
Feedback: Known examples, invalid-input tests, round-trip tests, and review findings.
Guardrail: Do not accept code the checks cannot evaluate.
```

If the agent says something vague like “build a useful encoder,” push back:

```md
Too vague. The aim is not the encoder. The aim is learning how to direct and judge agent-written code. Rewrite it around that behavior change.
```

## Step 2: Map what is going on

Use `/problem-space` if you have it. Otherwise paste:

```md
Map the problem space for this aim.

Aim:
[paste aim]

Context:
I am using a coding agent to implement a small Python base62 encoder/decoder. I want the exercise to teach prompts, evals, review, and recovery from bad first drafts.

Please identify:
- what we are trying to improve;
- actual constraints;
- assumed constraints;
- who uses or is affected by the output;
- what breaks if the code is wrong;
- hidden assumptions;
- whether I am solving the wrong problem.
```

Expected result:

```md
We are trying to improve how the builder directs and checks agent work, not merely produce a base62 library.
```

That shift matters. The coding task is the vehicle. The learning loop is the work.

## Step 3: State the problem

Use `/problem-statement` if you have it. Otherwise paste:

```md
Turn this problem space into three possible problem statements.

For each statement:
- say what it improves;
- say what it hides;
- say what kinds of solutions it points toward.

Then recommend one problem statement for a first pass.
```

Expected result:

```md
Problem statement: Beginners using coding agents often ask for code before defining behavior, edge cases, and review criteria, so they accept plausible implementations without knowing whether the code is correct.
```

If the agent jumps to implementation, stop it:

```md
Do not solve yet. I only want the problem statement and the trade-offs between possible framings.
```

## Step 4: Compare a few paths

Use `/solution-space` if you have it. Otherwise paste:

```md
Generate four ways to run this exercise:

1. ask the agent to implement base62 immediately;
2. write tests first, then ask for implementation;
3. write an agent brief with behavior, constraints, and evals, then execute;
4. build a larger app where base62 is one small part.

For each, compare:
- what it teaches;
- cost;
- risk;
- upkeep;
- when it would be the wrong choice.

Recommend the smallest approach that changes behavior.
```

Expected result:

```md
Recommendation: Write an agent brief with behavior, constraints, and evals before implementation. It teaches direction, not just prompting.
```

The agent may want to rush to code. Do not reward that.

## Step 5: Define behavior before code

Copy `templates/eval-checklist.md` and fill it in.

Base62 has variants. Use this dialect so the checks have a fixed target:

```md
Alphabet: 0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz

encode(n):
- accepts non-negative integers;
- returns "0" for 0;
- returns canonical base62 with no leading zeroes;
- rejects negative integers;
- rejects non-integers.

decode(s):
- accepts non-empty strings using the alphabet;
- rejects empty strings;
- rejects invalid characters;
- rejects leading zeroes except the string "0";
- returns a non-negative integer.

Round trip:
- decode(encode(n)) == n for non-negative integers.
```

Now ask the agent:

```md
Before writing implementation code, turn this contract into eval rules and tests.

Create:
- acceptance criteria;
- examples of good behavior;
- examples of bad behavior;
- failure modes;
- pytest cases;
- one property-based test for round trips.

Do not implement the encoder yet.
```

Good output should include checks like:

```md
- encode(0) == "0"
- encode(61) == "z"
- encode(62) == "10"
- decode("10") == 62
- decode(encode(n)) == n
- decode("") raises ValueError
- decode("01") raises ValueError
- decode("hello!") raises ValueError
- encode(-1) raises ValueError
- encode(True) raises TypeError
```

## Step 6: Use a bad output to sharpen the evals

Do not stop at a checklist. Make the agent reason from a concrete failure.

Paste this bad implementation idea:

```py
def encode(n):
    return "" if n == 0 else "TODO"

def decode(s):
    return 0 if not s else 1
```

Ask:

```md
Assume an agent produced this implementation.

Which eval rules catch it?
Which failures are not caught yet?
Add missing eval rules and tests.
Do not fix the implementation yet.
```

Expected learning:

```md
The zero case alone is not enough. We need known examples, invalid input checks, and round-trip tests over many values.
```

This is how evals get better: catch a specific failure, then turn it into a rule the next run has to satisfy.

Before you write the brief, treat it as a small strategy doc:

```text
Aim: what change this work should create.
Mechanism: why this approach should work.
Feedback: how we will know quickly if it is wrong.
Guardrail: what must not break while moving fast.
```

Then turn that into files, tests, commands, and review checks.

## Step 7: Write the brief

Copy `templates/agent-brief.md`.

Ask:

```md
Using the aim, problem statement, behavior contract, and eval checklist, draft a brief the coding agent can use for this task.

The brief should include:
- purpose;
- aim, mechanism, feedback, and guardrails;
- files to create or edit;
- behavior contract;
- tests to write;
- implementation constraints;
- failure modes;
- review checklist;
- a quick necessity / viability / sufficiency / connectedness check.

Keep it short enough that I would actually use it.
```

Expected result:

```md
Purpose: Implement a small base62 encoder/decoder and tests so the builder can practice directing and checking agent-written code.
```

If it writes a giant spec, say:

```md
Too much. Cut this by 40%. Keep only instructions that would change the code or tests.
```

## Step 8: Execute

Use `/execute` if you have it. Otherwise paste this into your coding agent:

```md
Implement the base62 encoder/decoder using this brief.

Rules:
- read the current project files first;
- create the smallest sensible module and test files;
- implement the behavior contract exactly;
- write pytest tests and one Hypothesis round-trip test;
- run the tests;
- fix failures from the root cause;
- do not add unrelated features;
- stop only when tests pass or you can name the blocker.

Brief:
[paste brief]
```

A reasonable implementation shape is:

```text
src/base62_agent_playground/base62.py
tests/test_base62.py
```

Do not micromanage the code unless the agent drifts. Let it work, then inspect what it did.

## Step 9: Review

Use `/review` if you have it. Otherwise paste:

```md
Review the base62 implementation against the original aim and behavior contract.

Check:
- Does the code implement the agreed alphabet?
- Does it reject invalid inputs?
- Does it enforce canonical output?
- Does every file and test connect back to the aim and mechanism?
- Do tests cover examples and round trips?
- Are there unrelated changes?
- Is the implementation simple enough to maintain?

Do not summarize first. Findings first. If there are no findings, say what residual risk remains.
```

Then run the tests yourself or ask the agent to run them again:

```bash
uv run pytest
```

Passing tests are evidence, not proof. Read the tests and the implementation.

## Step 10: Dissent

Use `/dissent` if you have it. Otherwise paste:

```md
Assume this base62 implementation passes tests but still fails in use.

Generate three failure scenarios:
1. a behavior contract ambiguity;
2. a missing edge case;
3. a bad test that gives false confidence.

For each, name:
- the warning sign;
- the assumption that broke;
- the smallest change to the contract or tests.
```

Expected result:

```md
Failure: The alphabet order was assumed but not documented in the code.
Fix: Put the alphabet constant in the module and assert known examples like 61 -> z and 62 -> 10.
```

Now revise once. Do not let the agent turn this into a package, CLI, web app, or benchmark project unless that was the aim.

## Step 11: Salvage if the run went sideways

Use `/salvage` if you have it. Otherwise paste:

```md
This implementation attempt went sideways.

Original aim:
[paste aim]

What happened:
[describe the drift, bad code, bad tests, or confusion]

Extract:
- what assumption was wrong;
- what guardrail should have existed;
- what context was missing;
- what part is worth keeping;
- how to restart smaller.
```

Salvage is not failure. It is how you avoid keeping a bad draft because you already spent time on it.

## Step 12: Save the pieces

You should now have:

- one aim;
- one problem statement;
- one behavior contract;
- one eval checklist;
- one brief;
- implementation code;
- tests;
- a review result;
- at least one dissent finding or explicit residual risk.

Save the brief and eval checklist next to the code or in your project scratch space. Next time, start from the shape, not from a blank prompt.

## What you practiced

```text
Aim → Problem Space → Problem Statement → Solution Space → Evals → Brief → Execute → Review → Dissent → Salvage
```

The main skill is not prompting. The main skill is knowing what you want, defining checks before code, and refusing to confuse agent confidence with correctness.

## Repeat with your own task

Run the loop again on something you care about:

- a parser;
- a small CLI;
- a bug fix;
- a refactor;
- a data transform;
- a test suite improvement;
- a documentation generator.

Keep it small. The first dozen repetitions may feel awkward. That is fine. You are building a judgment loop, not copying somebody else's workflow.
