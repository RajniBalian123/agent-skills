---
name: domain-modeling
description: Keep one glossary and one ADR format so the codebase, the docs, and the agent all use the same words. Use when a new concept needs a name, when two names mean the same thing, or when a decision needs recording.
---

# Domain Modeling

## When to use it

A concept appears in conversation, code, or docs without an agreed name — or
two names are being used for one thing, or one name for two things. Also when
a decision with consequences needs to outlive the meeting it was made in.

## Workflow

### Glossary

1. **One concept, one term.** Write the term, a one-sentence definition, and
   the words to avoid. The "avoid" list matters as much as the definition —
   it is where the confusion lives.
2. **Define by behavior, not by synonym.** "A pursuit is one opportunity
   being pursued from intake to submitted response" beats "a pursuit is a
   bid" — because a bid is exactly the word that causes the confusion.
3. **Keep the glossary where the work happens.** One file, linked from the
   repo guide. A glossary nobody can find is a glossary that doesn't exist.
4. **When a term is wrong, rename it everywhere** — code, docs, and
   messages. A half-rename is worse than no rename.

### Architecture Decision Records (ADRs)

1. **Write an ADR for any decision with real alternatives.** Format:
   context, decision, alternatives considered, consequences, revisit-when.
2. **One decision per ADR.** A decision that bundles three choices is three
   ADRs stapled together, and nobody will find the one they need later.
3. **Record the alternatives honestly.** An ADR that lists only the winning
   option is a press release, not a record. Future readers need to know what
   was rejected and why.
4. **Name the revisit condition.** "Reconsider when measured scan volume
   justifies a warehouse" beats "revisit later."

## Guardrails

- Never invent a term for a concept the business already names. Ask first.
- Never let code, docs, and chat use different words for the same thing.
  The agent reads all three; inconsistency in words becomes bugs in code.
- Never record a decision without its alternatives and its owner.

## Done means

Any person — or agent — can open the glossary and the ADR index and use the
right word for every concept, and find why each decision was made.
