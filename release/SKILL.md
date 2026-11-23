---
name: release
description: Cut a production release from the default branch — semver tag, release notes, breaking-change gate, and CI watch. Use when it is time to ship a version.
---

# Release

## When to use it

The default branch is ready to become a version users can depend on. A
release is a promise: this exact code, with these exact notes, is the version.

## Workflow

1. **Check the gate.** All required checks green on the head you will tag.
   A release from a red head is not a release, it is a hope.
2. **Decide the version.** Semver: breaking change → major; new capability
   → minor; fix → patch. If the change breaks an API or a migration path,
   it is breaking — say so in the notes, loudly.
3. **Write the notes from the merged work.** What changed, what it means for
   users, what to do if upgrading breaks something. No entry without a
   linked PR.
4. **Tag and publish.** One tag, one release, from the verified head. The
   tag and the release notes point at the same commit.
5. **Watch CI on the release.** Build, publish, and deploy checks must pass
   on the tagged commit. A release is not done until its own checks are
   green.

## Guardrails

- Never tag a commit you have not verified after the last push.
- Never hide a breaking change in the notes. It goes at the top, with the
  migration path.
- Never release from a branch that is not the default. A release from a
  feature branch is a different promise than the one users expect.

## Done means

A tagged version, published notes that describe it honestly, and green
checks on the tagged commit.
