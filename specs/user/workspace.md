<!-- SPDX-License-Identifier: Apache-2.0 -->
<!-- SPDX-FileCopyrightText: 2026 SubLang International <https://sublang.ai> -->

# WORKSPACE: User-Facing Workspace Behavior

This component defines user-visible behavior of IterOn workspace
commands.

## Opening Sessions

### WSX-001

Where a user runs `iteron open [agent] [workspace] [-- <args>]`,
the CLI shall create or attach to a workspace session in the
sandbox container, and positional argument resolution shall
follow ([DR-002 §4](../decisions/002-iteron-cli-commands.md#4-iteron-open-agent-workspace----args)):

- 0 args: default shell in `~`
- 1 arg matching a configured agent: configured agent binary in `~`
- 1 arg not matching a configured agent: default shell in
  `~/<workspace>`
- 2 args: first token as command/agent, second token as workspace
- 2 args where workspace is `~`: home directory
- 2 args where first token is not a configured agent: first token
  treated as command name
- Arguments after the first `--` are forwarded to the resolved command

### WSX-002

Where a user runs `iteron open <agent> <workspace>` and then
detaches (Ctrl-B D), when the user runs the same command again,
the CLI shall reattach to the existing session without creating
a duplicate
([DR-002 §4](../decisions/002-iteron-cli-commands.md#4-iteron-open-agent-workspace----args)).

## Listing Sessions

### WSX-003

Where a user runs `iteron ls`, the CLI shall display a tree
view grouping running sessions by workspace, showing command
name, attached/detached status, and uptime for each session
([DR-002 §5](../decisions/002-iteron-cli-commands.md#5-iteron-ls)).

## Removing Workspaces

### WSX-004

Where a user runs `iteron rm <workspace>`, the CLI shall kill
all sessions in that workspace and remove the workspace
directory. When active sessions exist, the CLI shall prompt
for confirmation. The CLI shall refuse `iteron rm ~` and shall
exit non-zero when workspace argument is missing
([DR-002 §6](../decisions/002-iteron-cli-commands.md#6-iteron-rm-workspace)).

## Error Handling

### WSX-005

Where the sandbox container is not running, when a user runs
`iteron open`, `iteron ls`, or `iteron rm`, the CLI shall
exit non-zero with a message indicating the container is not
running and suggesting `iteron start`
([DR-002 §4](../decisions/002-iteron-cli-commands.md#4-iteron-open-agent-workspace----args)).
