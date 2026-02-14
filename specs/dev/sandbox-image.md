<!-- SPDX-License-Identifier: Apache-2.0 -->
<!-- SPDX-FileCopyrightText: 2026 SubLang International <https://www.sublang.ai> -->

# SANDBOX: Sandbox Image Build and Configuration

This component defines implementation requirements for the local
IterOn sandbox image.

## Build Inputs

### SBD-001

Where the local sandbox image is built, the Dockerfile shall use
`node:22-bookworm-slim`
([DR-001 §1](../decisions/001-sandbox-architecture.md#1-oci-container-as-the-sandbox-boundary)).

### SBD-002

Where agent runtimes are installed, the build shall install
Claude Code, Gemini CLI, and OpenCode via npm and install Codex
from a pinned standalone Linux musl release binary
([DR-001 Context](../decisions/001-sandbox-architecture.md#context)).

### SBD-003

Where agent names are resolved for CLI sessions, the mapping
shall be:
`claude-code -> claude`,
`codex-cli -> codex`,
`gemini-cli -> gemini`,
`opencode -> opencode`
([DR-002 Workspace Model](../decisions/002-iteron-cli-commands.md#workspace-model)).

## Runtime Defaults

### SBD-004

Where the image is built, runtime defaults shall include user
`iteron` (`uid=1000`, `gid=1000`), `tini` as PID 1, and `bash`
as the default command
([DR-001 §1](../decisions/001-sandbox-architecture.md#1-oci-container-as-the-sandbox-boundary)).

### SBD-005

Where the image is built, it shall remove SUID/SGID bits and
provision default config files for agents and tmux at:
`/home/iteron/.claude.json`,
`/home/iteron/.claude/settings.json`,
`/home/iteron/.codex/config.toml`,
`/home/iteron/.gemini/settings.json`,
`/home/iteron/.config/opencode/opencode.json`, and
`/home/iteron/.tmux.conf`
([DR-001 §1](../decisions/001-sandbox-architecture.md#1-oci-container-as-the-sandbox-boundary),
[DR-001 §3](../decisions/001-sandbox-architecture.md#3-authentication)).

## Build Script

### SBD-006

Where `scripts/build-image.sh` runs a native build, it shall
select a functional runtime (Podman or Docker) and build
`iteron-sandbox:<tag>` from `image/`.

### SBD-007

Where `scripts/build-image.sh` runs in multi-arch mode, the
script shall require `--push` and publish a
`linux/amd64` + `linux/arm64` manifest.

## Image Size

### SBD-008

Where a sandbox image is published, the release process shall
enforce a per-architecture compressed image size budget of at
most 700 MiB, measured as the sum of
compressed layer sizes from the registry manifest for each target
platform.

## Headless Authentication

### SBD-010

Where the sandbox image is built, container defaults shall set
`NO_BROWSER=true` for headless Gemini OAuth
([DR-001 §3](../decisions/001-sandbox-architecture.md#3-authentication)).

### SBD-011

Where IterOn resolves host OpenCode credentials, the supported
source path shall be
`$XDG_DATA_HOME/opencode/auth.json` when `XDG_DATA_HOME` is set,
otherwise `~/.local/share/opencode/auth.json`
([DR-001 §3](../decisions/001-sandbox-architecture.md#3-authentication)).

### SBD-012

Where the supported host OpenCode credential file exists at
container start, launch behavior shall include a mapped credential
file at `/home/iteron/.local/share/opencode/auth.json` that is
readable and writable by the container runtime user, including
credential refresh
([DR-001 §3](../decisions/001-sandbox-architecture.md#3-authentication)).

### SBD-013

Where the supported host OpenCode credential file is absent at
container start, launch behavior shall omit any OpenCode
credential file mapping
([DR-001 §3](../decisions/001-sandbox-architecture.md#3-authentication)).

## Autonomous Execution Validation

### SBD-014

Where autonomous execution is validated, the validation fixture
shall be deterministic and include a single known defect with a
fixed oracle that fails before agent edits and passes after a
correct fix.

### SBD-015

Where autonomous execution is validated for supported agents
(`claude`, `codex`, `gemini`, `opencode`), each agent run shall
use a fresh isolated fixture workspace seeded from the same
fixture baseline.

### SBD-016

Where an autonomous agent run is evaluated, success criteria shall
require: agent command exit success within a bounded run time,
oracle test success after the run, and no interactive permission
approval prompt in captured output.

### SBD-017

Where autonomous-run diagnostics are emitted, values from
configured authentication secrets shall be redacted in diagnostic
output.

### SBD-018

Where an agent requires workspace trust preconditions for
non-interactive editing, the fixture baseline shall satisfy those
preconditions without manual operator intervention.

### SBD-019

Where autonomous execution validation defines the repair task, the
task contract shall require preserving fixture oracle definitions
while repairing the known defect under test.

### SBD-020

Where an autonomous agent run fails any autonomous success
criterion, validation output shall emit failure diagnostics that
include the run exit status and a bounded excerpt of captured run
output.
