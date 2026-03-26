---
agent: agent
description: "Comprehensive security and quality review of uncommitted changes. Blocks commit if CRITICAL or HIGH issues found."
tools: ['codebase', 'fetch', 'findTestFiles']
---

# Code Review

Run a comprehensive security and quality review of uncommitted changes.

## What This Prompt Does

1. Get changed files via `git diff`
2. Check for security issues, code quality, and best practices
3. Generate report with severity levels
4. Block commit if CRITICAL or HIGH issues found

## Security Issues (CRITICAL)

- Hardcoded credentials, API keys, tokens
- SQL injection vulnerabilities
- XSS vulnerabilities
- Missing input validation
- Insecure dependencies
- Path traversal risks

## Code Quality (HIGH)

- Functions > 50 lines
- Files > 800 lines
- Nesting depth > 4 levels
- Missing error handling
- `console.log` statements
- TODO/FIXME comments
- Missing JSDoc for public APIs

## Best Practices (MEDIUM)

- Mutation patterns (use immutable instead)
- Missing tests for new code
- Accessibility issues (a11y)

## Output

For each issue found:
- **Severity**: CRITICAL, HIGH, MEDIUM, LOW
- **File location and line numbers**
- **Issue description**
- **Suggested fix**

Never approve code with security vulnerabilities.
