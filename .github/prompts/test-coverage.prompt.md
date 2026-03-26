---
agent: agent
description: "Analyze test coverage, identify gaps, and generate missing tests to reach 80%+ coverage."
tools: ['codebase', 'terminal', 'editFiles', 'findTestFiles']
---

# Test Coverage

Analyze test coverage, identify gaps, and generate missing tests to reach 80%+ coverage.

## Step 1: Detect Test Framework

| Indicator | Coverage Command |
|-----------|-----------------|
| `jest.config.*` | `npx jest --coverage` |
| `vitest.config.*` | `npx vitest run --coverage` |
| `pytest.ini` / `pyproject.toml` | `pytest --cov=src --cov-report=json` |
| `Cargo.toml` | `cargo llvm-cov --json` |
| `pom.xml` with JaCoCo | `mvn test jacoco:report` |
| `go.mod` | `go test -coverprofile=coverage.out ./...` |

## Step 2: Analyze Coverage

1. Run the coverage command
2. List files below 80% coverage, sorted worst-first
3. For each under-covered file, identify untested functions, missing branch coverage, and dead code

## Step 3: Generate Missing Tests

Priority order:
1. **Happy path** — Core functionality with valid inputs
2. **Error handling** — Invalid inputs, missing data, network failures
3. **Edge cases** — Empty arrays, null/undefined, boundary values
4. **Branch coverage** — Each if/else, switch case, ternary

### Rules

- Place tests adjacent to source (follow project convention)
- Use existing test patterns from the project
- Mock external dependencies
- Each test should be independent — no shared mutable state
- Name tests descriptively

## Step 4: Verify

1. Run full test suite — all tests must pass
2. Re-run coverage — verify improvement
3. If still below 80%, repeat for remaining gaps
