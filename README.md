# Agent Skills

Agent skills I wrote for engineering teams — the instructions that make an AI
coding agent do reliable work without follow-up questions. Each skill is a
`SKILL.md` in the [skills.sh](https://www.skills.sh) format: YAML frontmatter
with a `name` and a `description` that tells the agent exactly when to fire,
then a short workflow it follows.

These are personal, generic versions of patterns I authored for my team's
skill library — rewritten here without any company-specific tooling, project
names, or internal references. See [How to install](#how-to-install) below.

## How to install

**Prerequisites:** Node.js 22.20 or later — check with `node --version`.
`npx` ships with Node, so there is nothing else to install first.

**Install the whole set.** Run this from the root of the project where you
want the skills:

```bash
npx skills add rajnibalian123/agent-skills
```

The CLI asks which agents to install for (Claude Code, Codex, Cursor, and
others) and writes one copy into the project's skills directory, linked into
each chosen agent. Add `-g` to install once for your user instead of one
project, and `-y` to accept the defaults without prompting.

**Install one skill only:**

```bash
npx skills add rajnibalian123/agent-skills --skill code-review
```

**Verify it worked:**

```bash
npx skills list       # skills installed in this project
npx skills list -g    # skills installed globally
```

**Manual install (no CLI):** copy a skill's folder — the folder that holds
its `SKILL.md` — into your agent's skills directory, for example
`.claude/skills/code-review/` for one project or
`~/.claude/skills/code-review/` for every project. The agent picks the skill
up from the `description` in its frontmatter, so the folder name must match
the skill's `name`.

**Keep them current, remove one:**

```bash
npx skills update              # update all installed skills
npx skills remove code-review  # remove one skill
```

Once installed, use a skill by describing the job in the agent's own terms —
"review this diff", "turn this scope into an estimate" — and the agent matches
the `description` and invokes it. No extra configuration is needed.

## The skills

| Skill | What it does |
|---|---|
| [issue-writer](./issue-writer/SKILL.md) | Write issues an AI coding agent can execute without follow-up questions — scoped by behavior, not file lists. |
| [code-review](./code-review/SKILL.md) | Review a diff for evidence-backed correctness bugs and regressions. |
| [pr-lifecycle](./pr-lifecycle/SKILL.md) | Open a PR from local changes, maintain it through review feedback and CI failures, and drive it to merge. |
| [domain-modeling](./domain-modeling/SKILL.md) | Keep one glossary and one ADR format so the codebase, the docs, and the agent all use the same words. |
| [estimate-from-scope](./estimate-from-scope/SKILL.md) | Turn a technical scope document into an editable WBS estimate with hour confidence. |
| [release](./release/SKILL.md) | Cut a production release: semver tag, release notes, breaking-change gate, CI watch. |

## How a skill is written

A good skill is short, specific about when it fires, and strict about what
"done" means. Every skill here follows the same shape:

1. **When to use it** — the trigger, in the agent's own terms.
2. **Workflow** — the steps, in order, with the checks that gate each one.
3. **Guardrails** — what the agent must never do (invent, skip verification,
   claim success without evidence).
4. **Done means** — the observable outcome, not a feeling.

The `description` in frontmatter is the most important line in the file: it
is what the agent matches against to decide whether to invoke the skill. Make
it specific about *when*, not just *what*.

## Authoring notes

- One skill, one job. If a skill needs another skill, it names it — it does
  not absorb it.
- Reference files live beside the skill and are addressed relative to the
  skill's own directory, so the skill works wherever it is installed.
- Never hardcode absolute paths, project names, or credentials.
- When a skill changes, its version note says what changed and why — skills
  are code, and they get reviewed like code.
