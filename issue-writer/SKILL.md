---
name: issue-writer
description: Write issues an AI coding agent can execute without follow-up questions — scoped by behavior, not file lists — or turn a feature into a spec with tracer-bullet tickets. Use when a ticket needs to become agent-ready, or when a feature needs breaking down before any code is written.
---

# Issue Writer

## When to use it

A ticket exists as a rough idea, a bug report, or a feature request, and an
agent (or a teammate) is about to implement it. If the implementer would have
to ask a question before starting, the ticket is not ready.

## Workflow

1. **Interview the person who knows why the ticket exists.** Ask what
   changes for the user, what is out of scope, and how they will know it
   works. Stop when the answers are concrete.
2. **Scope by behavior, not file lists.** Describe the observable change:
   inputs, outputs, edge cases, error states. Never prescribe which files to
   touch — that is the implementer's job.
3. **Write the acceptance criteria as checks.** Each criterion is something
   that can be verified after the change: a behavior, a test, a number.
4. **Name the dependencies.** What must exist first, and what blocks what.
   A ticket with an unmet dependency is a ticket that will stall.
5. **Break a feature into tracer-bullet tickets.** One thin vertical slice
   first (end to end, minimal), then the rest behind it, with blocking
   relations between them.

## Guardrails

- Never write "implement X in file Y" as the requirement. The requirement is
  the behavior; the file is an implementation detail.
- Never leave an acceptance criterion that cannot be checked. "Works well"
  is not a criterion.
- Never split work by layer (frontend ticket, backend ticket) when the user
  value crosses layers. Split by behavior.

## Done means

An agent can pick up the ticket, implement it, run the checks, and merge —
without asking a single question.
