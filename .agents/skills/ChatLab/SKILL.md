```markdown
# ChatLab Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill teaches you how to contribute to the ChatLab codebase, a TypeScript and Vue-based project with Electron integration. You'll learn the project's coding conventions, commit standards, and the main development workflows—including i18n, release management, documentation, feature development, parser updates, and CI/CD configuration. This guide also covers how to write and locate tests, and provides handy commands for common tasks.

## Coding Conventions

### File Naming
- Use **camelCase** for file names.
  - Example: `chatParser.ts`, `userProfile.vue`

### Import Style
- Use **relative imports**.
  - Example:
    ```typescript
    import { parseChat } from './parser/chatParser'
    import UserProfile from '../components/userProfile.vue'
    ```

### Export Style
- Use **named exports**.
  - Example:
    ```typescript
    // chatParser.ts
    export function parseChat(data: string) { ... }

    // userStore.ts
    export const userStore = { ... }
    ```

### Commit Messages
- Follow **conventional commit** style.
- Prefixes: `feat`, `fix`, `release`, `chore`, `docs`, `refactor`
- Keep messages concise (average 24 characters).
  - Example: `feat: add WhatsApp parser`

## Workflows

### Add or Update i18n Entries
**Trigger:** When adding new features, UI components, or updating displayed text in multiple languages.  
**Command:** `/add-i18n`

1. Edit or add keys in locale JSON files under `src/i18n/locales/` (e.g., `en-US`, `zh-CN`, `ja-JP`, `zh-TW`).
2. Update or create relevant UI components or pages to use the new/updated i18n keys.

**Example:**
```json
// src/i18n/locales/en-US/common.json
{
  "welcome": "Welcome to ChatLab"
}
```
```vue
<!-- src/components/Welcome.vue -->
<template>
  <div>{{ $t('common.welcome') }}</div>
</template>
```

---

### Release Version Bump and Changelog
**Trigger:** When preparing for a new release version.  
**Command:** `/release`

1. Update `package.json` with the new version.
2. Update changelog files for each language in `docs/changelogs_*.json`.

**Example:**
```json
// package.json
{
  "version": "1.2.0"
}
```
```json
// docs/changelogs_en.json
[
  {
    "version": "1.2.0",
    "changes": ["Added WhatsApp parser", "Improved UI responsiveness"]
  }
]
```

---

### Add or Update Docs (Multilingual)
**Trigger:** When documentation needs to be added or updated for new features or improvements.  
**Command:** `/update-docs`

1. Edit or add markdown files in `docs/cn/`, `docs/en/`, `docs/tw/`, etc.
2. Optionally update or add GitHub Actions workflow for docs sync/build (`.github/workflows/sync-docs.yml`).

**Example:**
```markdown
// docs/en/usage.md
# How to Use ChatLab

...
```

---

### Feature Development Across Backend and Frontend
**Trigger:** When adding a new feature or refactoring a major capability that spans backend logic and frontend UI.  
**Command:** `/new-feature`

1. Update or add files in `electron/main/` (backend logic, IPC, parsers, etc).
2. Update or add files in `electron/preload/` (preload APIs, type definitions).
3. Update or add Vue components in `src/components/` or `src/pages/`.
4. Update or add store modules in `src/stores/`.
5. Update i18n files if new UI text is introduced.

**Example:**
```typescript
// electron/main/parser/formats/whatsapp.ts
export function parseWhatsAppLog(file: string) { ... }
```
```vue
<!-- src/pages/ImportWhatsApp.vue -->
<template>
  <button @click="importWhatsApp">{{ $t('import.whatsapp') }}</button>
</template>
```

---

### Parser Format Support or Improvement
**Trigger:** When adding support for a new chat log format or improving parsing for an existing format.  
**Command:** `/update-parser`

1. Edit or add files under `electron/main/parser/formats/` for the specific format.
2. Update or add related files in `electron/main/parser/` and types.
3. Optionally update preload APIs or UI to reflect new parsing capabilities.

**Example:**
```typescript
// electron/main/parser/formats/telegram.ts
export function parseTelegramLog(file: string) { ... }
```

---

### CI/CD Workflow Update
**Trigger:** When changing Node version, build tools, or automating new steps in the release process.  
**Command:** `/update-ci`

1. Edit `.github/workflows/*.yml` files.
2. Update `package.json` or lock files if dependencies or build steps change.
3. Optionally update `electron-builder.yml` or related config files.

**Example:**
```yaml
# .github/workflows/build.yml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: '18'
      ...
```

## Testing Patterns

- Test files use the pattern `*.test.*` (e.g., `parser.test.ts`).
- The testing framework is **unknown**; check existing test files for conventions.
- Place tests alongside the files they test or in a dedicated `tests/` directory.

**Example:**
```typescript
// parser.test.ts
import { parseChat } from './parser'

test('parses simple chat log', () => {
  expect(parseChat('...')).toEqual({...})
})
```

## Commands

| Command        | Purpose                                                      |
|----------------|--------------------------------------------------------------|
| /add-i18n      | Add or update i18n translation files and update UI usage     |
| /release       | Bump version and update multilingual changelogs              |
| /update-docs   | Add or update documentation in multiple languages            |
| /new-feature   | Implement new feature/refactor across backend and frontend   |
| /update-parser | Add or improve chat log parser support                       |
| /update-ci     | Update CI/CD workflows and related configuration             |
```
