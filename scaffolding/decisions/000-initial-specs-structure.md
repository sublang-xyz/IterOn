# DR-000: Initial Specs Structure

## Status

Accepted

## Context

Projects need a standardized structure for specifications to support iterative development and collaboration between AI and humans.

## Decision

Use `iteron init` to create:

```text
specs/
├── decisions/    # Decision Records (DRs)
├── iterations/   # Iteration Records (IRs)
├── user/         # User-facing specifications - what the system does
├── dev/          # System internal specs for development - how the system is built
└── tests/        # Test case specifications
```

### Initial Directories

| Directory | Format | Naming |
| --------- | ------- | ------ |
| decisions/ | [ADR](https://adr.github.io/) (Architectural Decision Record) | `NNN-<kebab-case-title>.md` |
| iterations/ | Goal, deliverables, tasks, verification | `NNN-<kebab-case-title>.md` |
| user/ | [EARS](https://alistairmavin.com/ears/) (Easy Approach to Requirements Syntax) | `<kebab-case-component>.md` |
| dev/ | [EARS](https://alistairmavin.com/ears/) (Easy Approach to Requirements Syntax) | `<kebab-case-component>.md` |
| tests/ | Test cases by feature | `<kebab-case-feature>.md` |

Subdirectories optional for user/, dev/, and tests/.

### Initial Files

| Path | Content |
| ---- | ------- |
| `decisions/000-initial-specs-structure.md` | This DR |
| `iterations/000-license-headers.md` | Initial IR |
| `user/meta-ears-format.md` | EARS syntax guide |
| `dev/rules.md` | Commit message format |
| `tests/consistent-structure.md` | Structure verification |

## Consequences

- Consistent structure across iterations
- Clear separation of user-facing and internal specs
- Test cases decoupled from iterations for traceability
