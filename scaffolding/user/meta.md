# META: Specification Format

This component defines how to write specifications using [EARS](https://alistairmavin.com/ears/) syntax.

## File Format

### META-001

Each specification file shall be named `<kebab-case-component>.md`.

### META-002

Each item ID shall follow the format `<COMP>-NNN` (e.g., META-001, AUTH-017).

### META-003

Each item ID shall be a markdown heading for anchor linking.

### META-004

Each item shall be self-contained and not rely on surrounding section headings for context.

### META-005

Item IDs shall not be modified once assigned; new items shall use higher IDs.

## EARS Patterns

### META-006

Each item shall use one of the following EARS patterns:

| Pattern | Template |
| ------- | -------- |
| Ubiquitous | The `<system>` shall `<action>`. |
| Event-driven | When `<trigger>`, the `<system>` shall `<action>`. |
| State-driven | While `<state>`, the `<system>` shall `<action>`. |
| Optional | Where `<feature>`, the `<system>` shall `<action>`. |
| Unwanted | If `<condition>`, then the `<system>` shall `<action>`. |
