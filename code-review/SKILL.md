---
name: code-review
description: Review a working-tree diff, a branch, or a specified PR for evidence-backed correctness bugs and regressions. Use when code is ready for review, or when you need a second pair of eyes before merging.
---

# Code Review

## When to use it

A diff exists and someone needs to know whether it is correct — not whether
it is stylish. Run it before merge, and after any rebase or force-push that
changed the head.

## Workflow

1. **Read the diff, not the description.** The description says what the
   author intended; the diff says what changed.
2. **Trace the data.** Follow inputs through the changed code: where they
   come from, what transforms them, where they land. The bugs live in the
   joins, the boundaries, and the error paths.
3. **Check the tests against the change.** Does a test cover the new
   behavior? Does an existing test now assert something the change broke?
   A change with no test for its new behavior is unverified.
4. **Verify, don't assert.** Reproduce a suspected bug with a minimal case,
   or point to the exact line and the exact input that breaks it. A finding
   without evidence is a guess.
5. **Rank findings by severity.** Correctness bugs and regressions first;
   everything else is a note. Never block on style.

## Guardrails

- Never report a bug you cannot show: line, input, expected vs. actual.
- Never approve a diff you did not read. "Looks fine" is not a review.
- Never rewrite the author's code in the review. Say what is wrong and why;
  the fix is theirs.
- Never use review to relitigate a decision that lives in the decision log.
  If the decision is wrong, open that conversation separately.

## Done means

A list of findings, each with evidence and severity — or a clean review that
says what was checked. The author can act on every line without asking what
you meant.
