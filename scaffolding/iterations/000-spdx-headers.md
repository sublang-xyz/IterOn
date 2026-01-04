# IR-000: SPDX Headers

## Goal

Add SPDX headers to all source files.

## Deliverables

- [ ] Add SPDX headers to source files missing them
- [ ] Document header format in specs/dev/rules.md

## Tasks

1. **Detect license** from LICENSE file; skip license line if absent
2. **Add headers** using appropriate comment syntax per file type
3. **Document format** in specs/dev/rules.md
   E.g.:

   > ## Licensing
   >
   > Dual licensing:
   > - **Code** (src/): Apache-2.0
   > - **Content** (specs/, docs/): CC-BY-SA-4.0
   >
   > ### SPDX Headers
   >
   > All files must include SPDX headers at the top:
   >
   > **Code:**
   >
   > ```typescript
   > // SPDX-License-Identifier: Apache-2.0
   > // SPDX-FileCopyrightText: 2026 SubLang contributors <https://github.com/sublang-xyz>
   > ```
   >
   > **Markdown:**
   >
   > ```markdown
   > <!-- SPDX-License-Identifier: CC-BY-SA-4.0 -->
   > <!-- SPDX-FileCopyrightText: 2025 SubLang contributors <https://github.com/sublang-xyz> -->
   > ```

## Acceptance Criteria

- All source files have SPDX-FileCopyrightText header
- Files have SPDX-License-Identifier if LICENSE exists
