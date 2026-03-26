---
agent: agent
description: "Sync documentation with the codebase. Generate script references, environment docs, and flag stale documentation."
tools: ['codebase', 'editFiles', 'fetch']
---

# Update Documentation

Sync documentation with the codebase, generating from source-of-truth files.

## What This Prompt Does

1. **Generate Script Reference** — Extract commands from package.json / Makefile / etc.
2. **Generate Environment Docs** — Document variables from .env.example
3. **Update Contributing Guide** — Development setup, scripts, testing procedures
4. **Staleness Check** — Flag docs not modified in 90+ days

## Sources of Truth

| Source | Generates |
|--------|-----------|
| `package.json` scripts | Available commands reference |
| `.env.example` | Environment variable documentation |
| `openapi.yaml` / route files | API endpoint reference |
| Source code exports | Public API documentation |
| `Dockerfile` / `docker-compose.yml` | Infrastructure setup docs |

## Workflow

1. Identify sources of truth in the project
2. Generate or update documentation from those sources
3. Check for stale documentation
4. Show summary of updates, flags, and skips

## Rules

- Generate from source of truth — don't invent information
- Flag uncertain docs for manual review
- Keep documentation concise and actionable
