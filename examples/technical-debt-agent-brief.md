# Example: Duplicate Notification Improvement Brief

This is a worked example for `docs/tutorial.md`.

The repo is hypothetical, but the shape is common: users occasionally receive duplicate notifications, and the codebase has more than one path that can trigger a send.

## Aim

Reduce future change risk in the notification system by fixing one recurring duplicate-send path at the right level and encoding the behavior so it stays fixed.

## Problem statement selected

Notification ownership is split across multiple trigger paths, so no single layer enforces idempotency. Engineers can add notification behavior without seeing where duplicate prevention belongs.

## Solution-space summary

| Option | Level | Approach | Why rejected or selected |
|---|---|---|---|
| Add caller guard | Band-Aid | Add a duplicate check in the failing caller. | Rejected. It suppresses this symptom and leaves other paths exposed. |
| Consolidate helper | Local Optimum | Move shared send logic into one helper and update callers. | Rejected for this slice. Better, but still leaves ownership unclear if callers bypass it. |
| Boundary idempotency | Reframe | Treat duplicate sends as a boundary invariant. Enforce idempotency where notifications are sent. | Selected. It addresses the repeated symptom without redesigning the whole event system. |
| Event pipeline redesign | Redesign | Route all notification events through a single durable queue with idempotency keys. | Rejected for now. May be right later, but too large for one reviewable slice. |

## Small strategy

| Field | Value |
|---|---|
| Aim | Make notification changes safer by removing one recurring duplicate-send failure mode. |
| Mechanism | Enforcing idempotency at the notification boundary prevents duplicate sends regardless of which upstream path emitted the event. |
| Feedback | Regression test with duplicate events, integration test for the send path, review confirming no parallel send path remains in the selected slice. |
| Guardrail | Do not change notification content, timing policy, or subscription preferences. Do not redesign the full event pipeline in this slice. |

## Context for the agent

Inspect first:

- notification sending boundary;
- event handlers that call it;
- existing notification tests;
- logs or tests that mention duplicate sends;
- docs or comments about idempotency keys.

Likely files in a real repo might look like:

```text
src/notifications/send.*
src/notifications/events.*
src/notifications/subscriptions.*
tests/notifications/*
```

Use the actual repo paths. Do not invent these names if they do not exist.

## Behavior contract

The change must:

- define where duplicate prevention belongs;
- require an idempotency key, event id, or equivalent stable identifier at the send boundary;
- skip duplicate sends for the same recipient and notification event;
- record or expose enough signal to debug skipped duplicates;
- add a regression check that fails on the old behavior.

The change must not:

- change notification copy;
- change subscription or preference semantics;
- hide send failures as duplicates;
- add caller-specific duplicate checks while leaving the boundary unprotected;
- rewrite the full event pipeline.

## Checks

Acceptance checks:

- A duplicate event for the same recipient sends one notification.
- Two distinct events for the same recipient still send two notifications.
- A send failure is not recorded as a duplicate skip.
- Existing notification behavior still passes.
- The new test fails against the old duplicate-send behavior.

Commands:

```bash
# Replace with the repo's actual commands
npm test -- notifications
npm run typecheck
npm run lint
```

## Stop conditions

The agent should stop and report if:

- there is no stable idempotency key or event identifier;
- notification sending is split across more paths than the brief identified;
- meaningful tests require a broader test harness change;
- fixing this slice requires changing subscription semantics;
- the selected Reframe path turns into a full event-pipeline Redesign.

## Review checklist

- [ ] The patch enforces the invariant at the notification boundary, not only in one caller.
- [ ] The regression test fails on the old behavior.
- [ ] Duplicate and distinct-event cases are both covered.
- [ ] Error handling is not collapsed into duplicate suppression.
- [ ] No unrelated notification behavior changed.
- [ ] The next maintainer can see where duplicate prevention belongs.

## Dissent prompt

After the patch passes tests, run `/dissent` with this concern:

```md
Assume this duplicate-notification fix passes tests but still fails in production.
Look for:
- missing idempotency-key cases;
- a caller path that bypasses the boundary;
- test doubles that hide production behavior;
- a boundary that maintainers will misunderstand;
- cases where duplicate suppression hides real send failures.
```
