---
agent: agent
description: "Incrementally fix build and type errors with minimal, safe changes. Detects build system, parses errors, and fixes one at a time."
tools: ['codebase', 'terminal', 'editFiles', 'findTestFiles']
---

# Build Fix

Incrementally fix build and type errors with minimal, safe changes.

## Step 1: Detect Build System

| Indicator | Build Command |
|-----------|---------------|
| `package.json` with `build` script | `npm run build` or `pnpm build` |
| `tsconfig.json` (TypeScript only) | `npx tsc --noEmit` |
| `Cargo.toml` | `cargo build 2>&1` |
| `pom.xml` | `mvn compile` |
| `build.gradle` | `./gradlew compileJava` |
| `go.mod` | `go build ./...` |
| `pyproject.toml` | `python -m compileall -q .` or `mypy .` |

## Step 2: Parse and Group Errors

1. Run the build command and capture stderr
2. Group errors by file path
3. Sort by dependency order (fix imports/types before logic errors)
4. Count total errors for progress tracking

## Step 3: Fix Loop (One Error at a Time)

For each error:
1. Read the file — see error context (10 lines around the error)
2. Diagnose — identify root cause (missing import, wrong type, syntax error)
3. Fix minimally — the smallest change that resolves the error
4. Re-run build — verify the error is gone and no new errors introduced
5. Move to next — continue with remaining errors

## Guardrails

Stop and ask the user if:
- A fix introduces more errors than it resolves
- The same error persists after 3 attempts
- The fix requires architectural changes
- Build errors stem from missing dependencies

## Recovery Strategies

| Situation | Action |
|-----------|--------|
| Missing module/import | Check if package is installed; suggest install command |
| Type mismatch | Read both type definitions; fix the narrower type |
| Circular dependency | Identify cycle with import graph; suggest extraction |
| Version conflict | Check package version constraints |
| Build tool misconfiguration | Read config file; compare with working defaults |
