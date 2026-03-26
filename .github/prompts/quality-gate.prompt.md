---
agent: agent
description: "Run the ECC quality pipeline on demand: formatter checks, lint/type checks, and produce a remediation list."
tools: ['codebase', 'terminal', 'findTestFiles']
---

# Quality Gate

Run the quality pipeline on demand for a file or project scope.

## Usage

Provide a target path (defaults to current directory) and optional flags:
- `--fix` — Allow auto-format/fix where configured
- `--strict` — Fail on warnings where supported

## Pipeline

1. Detect language/tooling for target
2. Run formatter checks
3. Run lint/type checks when available
4. Produce a concise remediation list

## Output

For each issue:
- File and line number
- Issue description
- Severity (error/warning)
- Suggested fix (if `--fix` is not used)
