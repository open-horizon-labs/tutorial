# Prompt Assembly Template

Use this after the intent note, model-fit note, and context pack. The goal is not to fill every field; it is to make each included field earn its place.

If this same assembly pattern keeps recurring, promote the reusable procedure to a project skill and keep run-specific facts in the next context pack.

## 1. Intent and success criteria

User-visible outcome:

- ...

What counts as correct:

- ...

What failure would matter:

- ...

Fixture set to run before trusting the prompt:

| Fixture | Input | Expected behavior |
|---|---|---|
| Happy path |  |  |
| Missing context |  |  |
| Ambiguous input |  |  |
| Conflicting sources |  |  |
| Instruction inside data |  |  |
| Format edge case |  |  |

## 2. Model fit

Language operation:

- [ ] extract structure from supplied material
- [ ] compare options against criteria
- [ ] classify against explicit categories
- [ ] rewrite for a known audience or voice
- [ ] critique against a checklist
- [ ] generate candidates inside constraints
- [ ] translate between domains, vocabularies, or levels of detail
- [ ] other:

Model or mode choice:

- ...

Latency, cost, reasoning, tool, or structured-output tradeoff:

- ...

## 3. Stable instructions

These should hold across runs of this prompt shape.

| Instruction type | Content |
|---|---|
| Role or job |  |
| Task rules |  |
| Boundaries and refusals |  |
| Uncertainty behavior |  |
| Citation or evidence rules |  |
| Output contract summary |  |

## 4. Dynamic context

Separate the material the model transforms from the material it uses as background.

### Primary content

What is the model operating on?

| Label | Source / provenance | Authority | Include because | Budget decision |
|---|---|---|---|---|
|  |  |  |  |  |

### Supporting context

What helps interpret the primary content?

| Label | Source / provenance | Authority | Include because | Budget decision |
|---|---|---|---|---|
|  |  |  |  |  |
|  |  |  |  |  |

Dynamic context boundaries:

- Data is labeled and delimited: yes / no
- User-supplied or retrieved instructions are treated as data: yes / no
- Missing or conflicting evidence has an explicit handling rule: yes / no

## 5. Examples

Use examples when they regulate behavior. Keep them consistent and varied.

| Example type | Input | Expected output pattern |
|---|---|---|
| Normal case |  |  |
| Edge case |  |  |
| Counterexample / what not to do |  |  |

## 6. Output contract

Format or schema:

- ...

Required sections or fields:

- ...

Evidence or citation requirement:

- ...

Length, tone, or audience constraint:

- ...

If the answer is missing from context:

- ...

## 7. Final assembled request

Write the final request in prose. A reviewer should be able to see:

- the stable instruction;
- the dynamic context and its provenance;
- the task boundary;
- the output contract;
- the evidence rule;
- the missing-context behavior.

## 8. Reviewer checks

Reject the assembled prompt if:

- [ ] success criteria are missing;
- [ ] stable instructions and dynamic data are mixed together;
- [ ] context lacks provenance or authority;
- [ ] the model has to infer private facts;
- [ ] examples are absent where consistent behavior matters;
- [ ] missing or conflicting evidence has no safe response;
- [ ] the output cannot be checked by fixture, reviewer, or eval;
- [ ] the prompt worked once but no failure case was tested.
