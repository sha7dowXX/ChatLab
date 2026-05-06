---
name: release-version-bump-and-changelog
description: Workflow command scaffold for release-version-bump-and-changelog in ChatLab.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /release-version-bump-and-changelog

Use this workflow when working on **release-version-bump-and-changelog** in `ChatLab`.

## Goal

Release a new version by updating the package version and changelog files in multiple languages.

## Common Files

- `package.json`
- `docs/changelogs_*.json`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Update package.json with the new version.
- Update changelog files for each language (docs/changelogs_*.json).

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.