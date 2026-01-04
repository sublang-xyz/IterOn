# TC: SPDX Headers (IR-000)

Acceptance tests to verify IR-000 completion.

## TC-001: Copyright Header

**Given** a source file in the project
**When** checking its header
**Then** it shall contain `SPDX-FileCopyrightText`

## TC-002: License Header

**Given** a project with a LICENSE file
**When** checking source file headers
**Then** each shall contain `SPDX-License-Identifier`

**Given** a project without a LICENSE file
**When** checking source file headers
**Then** `SPDX-License-Identifier` shall be absent
