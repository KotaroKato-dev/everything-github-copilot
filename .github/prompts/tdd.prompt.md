---
agent: agent
description: "Enforce test-driven development workflow. Scaffold interfaces, generate tests FIRST, then implement minimal code to pass. Ensure 80%+ coverage."
tools: ['codebase', 'terminal', 'editFiles', 'fetch', 'findTestFiles']
---

# TDD Workflow

Invoke the **tdd-guide** agent to enforce test-driven development methodology.

## What This Prompt Does

1. **Scaffold Interfaces** — Define types/interfaces first
2. **Generate Tests First** — Write failing tests (RED)
3. **Implement Minimal Code** — Write just enough to pass (GREEN)
4. **Refactor** — Improve code while keeping tests green (REFACTOR)
5. **Verify Coverage** — Ensure 80%+ test coverage

## When to Use

- Implementing new features
- Adding new functions/components
- Fixing bugs (write test that reproduces bug first)
- Refactoring existing code
- Building critical business logic

## TDD Cycle

```
RED → GREEN → REFACTOR → REPEAT

RED:      Write a failing test
GREEN:    Write minimal code to pass
REFACTOR: Improve code, keep tests passing
REPEAT:   Next feature/scenario
```

## Workflow

1. Define interfaces for inputs/outputs
2. Write tests that will FAIL (because code doesn't exist yet)
3. Run tests and verify they fail for the right reason
4. Write minimal implementation to make tests pass
5. Run tests and verify they pass
6. Refactor code while keeping tests green
7. Check coverage and add more tests if below 80%
