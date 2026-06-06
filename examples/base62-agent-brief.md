# Example: Base62 Agent Brief

This is the worked example for `docs/tutorial.md`.

## Aim

Learn to direct a coding agent through a small implementation by making behavior, tests, and review criteria explicit before the agent writes code.

## Problem Statement

Beginners using coding agents often ask for code before defining behavior, edge cases, and review criteria. Then they accept plausible implementations without knowing whether the code is correct.

## Small Strategy

| Field | Value |
|---|---|
| Aim | Learn to direct and judge agent-written code. |
| Mechanism | A precise behavior contract plus evals gives the agent a concrete target and gives the human evidence for rejection. |
| Feedback | Known examples, invalid-input tests, Hypothesis round trips, and review findings. |
| Guardrail | Do not accept plausible code that the tests cannot evaluate. Do not add unrelated features. |

## Behavior Contract

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

## Eval Rules

The implementation is acceptable if:

- known examples pass: `0 -> "0"`, `61 -> "z"`, `62 -> "10"`, `3843 -> "zz"`, `3844 -> "100"`;
- `decode(encode(n)) == n` for many non-negative integers;
- `encode` rejects negative integers and non-integers;
- `decode` rejects empty strings, invalid characters, and non-canonical leading zeroes;
- code is small enough to inspect directly.

The implementation fails if it:

- treats `0` as an empty string;
- silently accepts invalid input;
- uses a different alphabet order;
- passes example tests but fails round trips;
- adds unrelated features before the basic contract is correct.

## Brief for the Agent

```md
Purpose:
Implement a small Python base62 encoder/decoder and tests so I can practice directing and checking agent-written code.

Small strategy:
- Aim: practice directing and judging agent-written code.
- Mechanism: use a precise behavior contract plus evals before implementation.
- Feedback: known examples, invalid-input tests, round-trip tests, and review findings.
- Guardrails: no unrelated features; no claims of correctness without `uv run pytest`.

Files:
- Create or update `src/base62_agent_playground/base62.py`.
- Create `tests/test_base62.py`.

Behavior:
- Alphabet is `0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz`.
- `encode(n)` accepts non-negative integers and returns canonical base62.
- `decode(s)` accepts canonical base62 strings and returns non-negative integers.
- Reject negative integers, non-integers, empty strings, invalid characters, and leading zeroes except `"0"`.

Tests:
- Use pytest for known examples and invalid inputs.
- Use Hypothesis for round-trip tests over non-negative integers.
- Include examples: `0 -> "0"`, `61 -> "z"`, `62 -> "10"`, `3843 -> "zz"`, `3844 -> "100"`.

Rules:
- Keep the implementation simple.
- Do not add a CLI, web app, benchmark, or packaging changes unless required by the existing project.
- Run `uv run pytest` and fix root causes of failures.

Review checklist:
- Alphabet is explicit and tested.
- Invalid input behavior is tested.
- Canonical output is tested.
- Round-trip property is tested.
- No unrelated features were added.
```

## Tests the Agent Should Produce

```py
import pytest
from hypothesis import given, strategies as st

from base62_agent_playground.base62 import decode, encode


@pytest.mark.parametrize(
    ("number", "encoded"),
    [
        (0, "0"),
        (1, "1"),
        (9, "9"),
        (10, "A"),
        (35, "Z"),
        (36, "a"),
        (61, "z"),
        (62, "10"),
        (3843, "zz"),
        (3844, "100"),
    ],
)
def test_known_examples(number, encoded):
    assert encode(number) == encoded
    assert decode(encoded) == number


@given(st.integers(min_value=0, max_value=10**18))
def test_round_trip(number):
    assert decode(encode(number)) == number


@pytest.mark.parametrize("bad", [-1, -62])
def test_encode_rejects_negative_integers(bad):
    with pytest.raises(ValueError):
        encode(bad)


@pytest.mark.parametrize("bad", [1.2, "1", None, True, False])
def test_encode_rejects_non_integers(bad):
    with pytest.raises(TypeError):
        encode(bad)


@pytest.mark.parametrize("bad", ["", "01", "00", "hello!", "base_62"])
def test_decode_rejects_invalid_strings(bad):
    with pytest.raises(ValueError):
        decode(bad)


@pytest.mark.parametrize("bad", [1, None])
def test_decode_rejects_non_strings(bad):
    with pytest.raises(TypeError):
        decode(bad)
```

## Review Prompt

```md
Review the implementation against the brief.

Findings first. Check for:
- wrong alphabet;
- missing invalid input handling;
- missing canonical output checks;
- weak tests that pass a broken implementation;
- unrelated features;
- code that is harder than the task requires.

If there are no findings, say what residual risk remains.
```
