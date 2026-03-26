---
agent: agent
description: "Run comprehensive verification on the current codebase: build, types, lint, tests, secrets, and git status."
tools: ['codebase', 'terminal', 'findTestFiles']
---

# Verify

Run comprehensive verification on the current codebase state.

## Verification Order

1. **Build Check** — Run the build command; if it fails, report errors and STOP
2. **Type Check** — Run TypeScript/type checker; report all errors with file:line
3. **Lint Check** — Run linter; report warnings and errors
4. **Test Suite** — Run all tests; report pass/fail count and coverage percentage
5. **Console.log Audit** — Search for console.log in source files
6. **Git Status** — Show uncommitted changes

## Output Format

```
VERIFICATION: [PASS/FAIL]

Build:    [OK/FAIL]
Types:    [OK/X errors]
Lint:     [OK/X issues]
Tests:    [X/Y passed, Z% coverage]
Secrets:  [OK/X found]
Logs:     [OK/X console.logs]

Ready for PR: [YES/NO]
```

## Modes

- **quick** — Only build + types
- **full** — All checks (default)
- **pre-commit** — Checks relevant for commits
- **pre-pr** — Full checks plus security scan
