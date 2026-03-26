---
agent: agent
description: "Safely identify and remove dead code with test verification at every step."
tools: ['codebase', 'terminal', 'editFiles', 'findTestFiles']
---

# Refactor Clean

Safely identify and remove dead code with test verification at every step.

## Step 1: Detect Dead Code

Run analysis tools based on project type:
- **JavaScript/TypeScript**: `npx knip`, `npx depcheck`, `npx ts-prune`
- **Python**: `vulture src/`
- **Go**: `deadcode ./...`
- **Rust**: `cargo +nightly udeps`

## Step 2: Categorize Findings

| Tier | Examples | Action |
|------|----------|--------|
| **SAFE** | Unused utilities, test helpers, internal functions | Delete with confidence |
| **CAUTION** | Components, API routes, middleware | Verify no dynamic imports or external consumers |
| **DANGER** | Config files, entry points, type definitions | Investigate before touching |

## Step 3: Safe Deletion Loop

For each SAFE item:
1. Run full test suite — establish baseline (all green)
2. Delete the dead code
3. Re-run test suite — verify nothing broke
4. If tests fail — immediately revert and skip this item
5. If tests pass — move to next item

## Rules

- Never delete without running tests first
- One deletion at a time — atomic changes make rollback easy
- Skip if uncertain — better to keep dead code than break production
- Don't refactor while cleaning — separate concerns
