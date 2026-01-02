<!-- SPDX-License-Identifier: CC-BY-SA-4.0 -->
<!-- SPDX-FileCopyrightText: 2025 SubLang contributors <https://github.com/sublang-xyz> -->

# Rules

This document is **internal** (repository contribution rules).

## Commit Message Format

- Use `<type>(<optional scope>)<optional !>: <subject>` format.
- Type: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `ci`, `build`, `perf`, or `chore`.
- `!` for breaking changes.
- Subject: imperative, ≤50 chars, no period. Example: `feat(auth): add OAuth login`.
- Body: explain **what/why** (not how); wrap at 72 chars; use bullets if clearer.
- Co-authorship: add trailer if AI-assisted.
- Signing: required.

## Spec Item Format

- Each spec item shall be self-contained and not rely on section headers for context.
- Item IDs shall not be modified once assigned; new items shall use higher IDs.

## Licensing

Project uses dual licensing:

- **Code** (src/, bin/, config files): Apache-2.0
- **Content** (specs/): CC-BY-SA-4.0

### SPDX Headers

All new files must include SPDX headers at the top:

**TypeScript/JavaScript (Apache-2.0):**

```typescript
// SPDX-License-Identifier: Apache-2.0
// SPDX-FileCopyrightText: 2025 SubLang contributors <https://github.com/sublang-xyz>
```

**Markdown in specs/ (CC-BY-SA-4.0):**

```markdown
<!-- SPDX-License-Identifier: CC-BY-SA-4.0 -->
<!-- SPDX-FileCopyrightText: 2025 SubLang contributors <https://github.com/sublang-xyz> -->
```

**YAML/Shell/Config (Apache-2.0):**

```yaml
# SPDX-License-Identifier: Apache-2.0
# SPDX-FileCopyrightText: 2025 SubLang contributors <https://github.com/sublang-xyz>
```

JSON files cannot carry inline comments; they inherit the code license by proximity.
