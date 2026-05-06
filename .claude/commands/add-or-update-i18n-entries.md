---
name: add-or-update-i18n-entries
description: Workflow command scaffold for add-or-update-i18n-entries in ChatLab.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-or-update-i18n-entries

Use this workflow when working on **add-or-update-i18n-entries** in `ChatLab`.

## Goal

Add or update internationalization (i18n) translation files for new features, UI changes, or terminology updates.

## Common Files

- `src/i18n/locales/*/*.json`
- `src/pages/**/*.vue`
- `src/components/**/*.vue`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit or add keys in multiple locale JSON files under src/i18n/locales/ (e.g., en-US, zh-CN, ja-JP, zh-TW).
- Update or create relevant UI components or pages to use the new/updated i18n keys.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.