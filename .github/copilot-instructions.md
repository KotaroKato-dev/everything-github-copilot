# Project Instructions for GitHub Copilot

This is a **production-ready AI coding plugin** providing 28 specialized agents, 125 skills, 60 commands, and automated workflows for software development.

## Core Principles

1. **Agent-First** — Delegate to specialized agents for domain tasks
2. **Test-Driven** — Write tests before implementation, 80%+ coverage required
3. **Security-First** — Never compromise on security; validate all inputs
4. **Immutability** — Always create new objects, never mutate existing ones
5. **Plan Before Execute** — Plan complex features before writing code

## Coding Style

### Immutability (CRITICAL)

ALWAYS create new objects, NEVER mutate existing ones:

```
WRONG:  modify(original, field, value) → changes original in-place
CORRECT: update(original, field, value) → returns new copy with change
```

Rationale: Immutable data prevents hidden side effects, makes debugging easier, and enables safe concurrency.

### File Organization

MANY SMALL FILES > FEW LARGE FILES:
- High cohesion, low coupling
- 200–400 lines typical, 800 max
- Extract utilities from large modules
- Organize by feature/domain, not by type

### Error Handling

ALWAYS handle errors comprehensively:
- Handle errors explicitly at every level
- Provide user-friendly error messages in UI-facing code
- Log detailed error context on the server side
- Never silently swallow errors

### Input Validation

ALWAYS validate at system boundaries:
- Validate all user input before processing
- Use schema-based validation where available
- Fail fast with clear error messages
- Never trust external data (API responses, user input, file content)

### Code Quality Checklist

Before marking work complete:
- [ ] Code is readable and well-named
- [ ] Functions are small (<50 lines)
- [ ] Files are focused (<800 lines)
- [ ] No deep nesting (>4 levels)
- [ ] Proper error handling
- [ ] No hardcoded values (use constants or config)
- [ ] No mutation (immutable patterns used)

## Security Guidelines

### Mandatory Security Checks

Before ANY commit:
- [ ] No hardcoded secrets (API keys, passwords, tokens)
- [ ] All user inputs validated
- [ ] SQL injection prevention (parameterized queries)
- [ ] XSS prevention (sanitized HTML)
- [ ] CSRF protection enabled
- [ ] Authentication/authorization verified
- [ ] Rate limiting on all endpoints
- [ ] Error messages don't leak sensitive data

### Secret Management

- NEVER hardcode secrets in source code
- ALWAYS use environment variables or a secret manager
- Validate that required secrets are present at startup
- Rotate any secrets that may have been exposed

### Security Response Protocol

If a security issue is found:
1. STOP immediately
2. Use the **security-reviewer** agent
3. Fix CRITICAL issues before continuing
4. Rotate any exposed secrets
5. Review entire codebase for similar issues

## Testing Requirements

### Minimum Test Coverage: 80%

Test Types (ALL required):
1. **Unit Tests** — Individual functions, utilities, components
2. **Integration Tests** — API endpoints, database operations
3. **E2E Tests** — Critical user flows

### Test-Driven Development (Mandatory)

1. Write test first (RED) — test should FAIL
2. Write minimal implementation (GREEN) — test should PASS
3. Refactor (IMPROVE) — verify coverage 80%+

### Troubleshooting Test Failures

1. Check test isolation
2. Verify mocks are correct
3. Fix implementation, not tests (unless tests are wrong)

## Git Workflow

### Commit Message Format

```
<type>: <description>

<optional body>
```

Types: `feat`, `fix`, `refactor`, `docs`, `test`, `chore`, `perf`, `ci`

### Pull Request Workflow

1. Analyze full commit history (not just latest commit)
2. Use `git diff [base-branch]...HEAD` to see all changes
3. Draft comprehensive PR summary
4. Include test plan
5. Push with `-u` flag if new branch

## Architecture Patterns

### API Response Format

Use a consistent envelope for all API responses:
- Include a success/status indicator
- Include the data payload (nullable on error)
- Include an error message field (nullable on success)
- Include metadata for paginated responses (total, page, limit)

### Repository Pattern

Encapsulate data access behind a consistent interface:
- Define standard operations: `findAll`, `findById`, `create`, `update`, `delete`
- Concrete implementations handle storage details
- Business logic depends on the abstract interface, not the storage mechanism

### Skeleton Projects

When implementing new functionality:
1. Search for battle-tested templates or libraries
2. Evaluate options for security, extensibility, and relevance
3. Clone best match as foundation
4. Iterate within proven structure

## Development Workflow

1. **Research & Reuse** — Search for existing implementations before writing new code
2. **Plan First** — Use the planner agent for complex features; generate planning docs
3. **TDD Approach** — Write tests first; implement to pass; refactor
4. **Code Review** — Use the code-reviewer agent immediately after writing code
5. **Commit & Push** — Conventional commits format; comprehensive PR summaries

## Available Agents

| Agent | Purpose | When to Use |
|-------|---------|-------------|
| planner | Implementation planning | Complex features, refactoring |
| architect | System design | Architectural decisions |
| tdd-guide | Test-driven development | New features, bug fixes |
| code-reviewer | Code review | After writing code |
| security-reviewer | Security analysis | Before commits, sensitive code |
| build-error-resolver | Fix build errors | When build fails |
| e2e-runner | E2E testing | Critical user flows |
| refactor-cleaner | Dead code cleanup | Code maintenance |
| doc-updater | Documentation | Updating docs |
| docs-lookup | Documentation lookup | Library/API questions |
| cpp-reviewer | C++ code review | C++ projects |
| cpp-build-resolver | C++ build errors | C++ build failures |
| go-reviewer | Go code review | Go projects |
| go-build-resolver | Go build errors | Go build failures |
| kotlin-reviewer | Kotlin code review | Kotlin/Android/KMP projects |
| kotlin-build-resolver | Kotlin/Gradle build errors | Kotlin build failures |
| database-reviewer | PostgreSQL specialist | Schema design, query optimization |
| python-reviewer | Python code review | Python projects |
| java-reviewer | Java/Spring Boot review | Java/Spring Boot projects |
| java-build-resolver | Java/Maven/Gradle errors | Java build failures |
| chief-of-staff | Communication triage | Multi-channel messaging |
| loop-operator | Autonomous loop execution | Safe loop monitoring |
| harness-optimizer | Config tuning | Reliability, cost, throughput |
| rust-reviewer | Rust code review | Rust projects |
| rust-build-resolver | Rust build errors | Rust build failures |
| pytorch-build-resolver | PyTorch errors | PyTorch build/training |
| typescript-reviewer | TypeScript/JS review | TypeScript/JavaScript projects |
| flutter-reviewer | Flutter/Dart review | Flutter projects |

## Agent Orchestration

Use agents proactively without explicit user prompt:
- Complex feature requests → **planner**
- Code just written/modified → **code-reviewer**
- Bug fix or new feature → **tdd-guide**
- Architectural decision → **architect**
- Security-sensitive code → **security-reviewer**

Use parallel execution for independent operations — launch multiple agents simultaneously.

## Performance

### Build Troubleshooting

If build fails:
1. Use **build-error-resolver** agent
2. Analyze error messages
3. Fix incrementally
4. Verify after each fix

### Context Management

- Avoid exceeding context limits for large refactoring and multi-file features
- Lower context sensitivity tasks: single-file edits, documentation updates, simple bug fixes

## Project Structure

```
agents/          — 28 specialized subagents
skills/          — 125 workflow skills and domain knowledge
commands/        — 60 slash commands
hooks/           — Trigger-based automations
rules/           — Always-follow guidelines (common + per-language)
scripts/         — Cross-platform Node.js utilities
mcp-configs/     — 14 MCP server configurations
tests/           — Test suite
```

## Success Metrics

- All tests pass with 80%+ coverage
- No security vulnerabilities
- Code is readable and maintainable
- Performance is acceptable
- User requirements are met
