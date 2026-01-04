# REQ-000: Requirements Format

This document defines how to write user-facing requirements using EARS syntax.

## ID Format

- **File**: `NNN-<kebab-case-title>.md`
- **Items**: `REQ-NNN-NN` (e.g., REQ-001-01, REQ-001-02)

## EARS Syntax

EARS (Easy Approach to Requirements Syntax) provides five patterns:

| Pattern | Template | Use When |
|---------|----------|----------|
| Ubiquitous | The `<system>` shall `<action>`. | Always applies |
| Event-driven | When `<trigger>`, the `<system>` shall `<action>`. | Response to event |
| State-driven | While `<state>`, the `<system>` shall `<action>`. | During a condition |
| Optional | Where `<feature>`, the `<system>` shall `<action>`. | Configurable behavior |
| Unwanted | If `<condition>`, then the `<system>` shall `<action>`. | Error handling |

## Examples

**REQ-001-01** (Ubiquitous): The system shall display an error message when input validation fails.

**REQ-001-02** (Event-driven): When the user clicks "Submit", the system shall save the form data.

**REQ-001-03** (State-driven): While offline mode is active, the system shall queue requests locally.

**REQ-001-04** (Optional): Where dark mode is enabled, the system shall use the dark color scheme.

**REQ-001-05** (Unwanted): If the network connection times out, then the system shall retry up to 3 times.

## Template

```markdown
# REQ-NNN: <Title>

## Overview
Brief description of this requirement group.

## Requirements

**REQ-NNN-01** (<pattern>): The system shall ...

**REQ-NNN-02** (<pattern>): When ..., the system shall ...
```
