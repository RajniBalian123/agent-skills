---
name: estimate-from-scope
description: Turn a technical scope document into an editable work-breakdown estimate with hour confidence. Use when a scope document arrives and an estimate is needed, or when past estimates should ground the hours instead of a blank template.
---

# Estimate from Scope

## When to use it

A technical scope document lists required work and someone needs hours for
it. The organization has past estimates; the skill makes that history usable
instead of starting from a blank spreadsheet.

## Workflow

1. **Parse the scope.** Extract the deliverables (named work packages),
   the engineering stages, and the disciplines. Confirm them — do not guess
   a deliverable from a vague heading.
2. **Retrieve the nearest past estimates.** Match on scope similarity. The
   match must be real: a close scope match, not a shared keyword.
3. **Expand deliverables through WBS templates.** Each deliverable becomes
   its standard task tree with placeholder hours. Hours come from the
   matching past estimate; template hours only when nothing matches.
4. **Score confidence per row.** High is a close scope match or an engineer
   edit; Medium is a title match or a weaker scope match; Low is template
   hours or a poor scope match. Stored as 0–100. Confidence is a property of
   the evidence, not a measure of AI quality — and a Low row stays visible,
   so the engineer knows which hours to scrutinize.
5. **Derive the schedule from effort.** Duration in working days = hours /
   (resources × hours per working day). Stages run in sequence; disciplines
   in the same stage run in parallel. Project management is a percentage of
   engineering hours (default 10%).
6. **Route it through review.** The reviewer is assigned per estimate, sees
   the exact saved revision, and cannot be the estimate owner. Approved
   content is immutable; changing it means reopening as a new revision.

## Guardrails

- Never present template hours as if they came from a past estimate. The
  source is on the row.
- Never treat absence of evidence as zero. An unmatched deliverable is
  Low confidence, not zero hours.
- Never let an estimate's edits change the organization's templates. Edits
  stay on the estimate.
- Never approve your own estimate, and never review a revision you have not
  read in full.

## Done means

An estimate with every hour sourced, every row confidence-scored, a schedule
derived from effort, and a review decision recorded against the exact
revision reviewed.
