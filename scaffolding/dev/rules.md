# RULE: Development Rules

This component defines development rules for the project.

## Git Commits

### RULE-001

The AI agent shall verify `user.name` and `user.email` are configured before committing.

### RULE-002

Each commit message shall use `<type>(<scope>)<!>: <subject>` format, where `<scope>` and `!` are optional.

### RULE-003

The commit type shall be one of: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `ci`, `build`, `perf`, or `chore`.

### RULE-004

The commit subject shall be imperative, ≤50 chars, with no trailing period.

### RULE-005

When a commit introduces a breaking change, the message shall include `!` before the colon.

### RULE-006

The commit body shall explain what/why (not how), wrap at 72 chars, and use bullets if clearer.

### RULE-007

When AI assists in authoring a commit, the message shall include a `Co-authored-by` trailer.
