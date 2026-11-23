---
name: pr-lifecycle
description: Open a PR from local changes, maintain it through human and automated review feedback, merge conflicts, and CI failures, and drive it to merge. Use when the user asks to open, ship, land, or merge a PR, or when a PR is stuck in review.
---

# PR Lifecycle

## When to use it

Local changes are ready to become a PR, or an open PR needs to move: review
feedback arrived, CI failed, a conflict appeared, or the user asked to merge.

## Workflow

### Open

1. Decide whether to ship one PR, split it, or stack dependent PRs. One
   behavior per PR; a stack when the second genuinely depends on the first.
2. Write the PR description from the change: what it does, why, how to
   verify. Link the issue it closes.
3. Attach verified screenshots when the diff changes UI. A screenshot you
   did not verify is not evidence.

### Maintain

1. Triage every finding: human review, automated review, CI failure, merge
   conflict. Fix, validate, push, reply or resolve — then recheck the latest
   head.
2. Repeat until the latest head is ready or concretely blocked. "Ready"
   means: review feedback addressed, CI green, no conflicts.
3. If blocked, say exactly what blocks it and who owns the unblock. Never
   leave a PR in a silent stuck state.

### Land

1. Arm auto-merge only on a verified head. Disarm before each of your own
   pushes, so an unverified head never merges.
2. Watch CI on the merged head. A merge is not done until the main-branch
   checks pass.

## Guardrails

- Never merge a head you have not verified after the last push.
- Never force-push over someone else's review comments without addressing
  them.
- Never open a PR with a description the author would not recognize. The
  description is a contract with the reviewer.

## Done means

The PR is merged, main-branch checks are green — or the PR is concretely
blocked with the blocker named and owned.
