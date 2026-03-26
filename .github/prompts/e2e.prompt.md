---
agent: agent
description: "Generate and run end-to-end tests with Playwright. Creates test journeys, runs tests, captures screenshots/videos/traces, and identifies flaky tests."
tools: ['codebase', 'terminal', 'editFiles', 'fetch', 'findTestFiles']
---

# E2E Testing

Invoke the **e2e-runner** agent to generate, maintain, and execute end-to-end tests using Playwright.

## What This Prompt Does

1. **Generate Test Journeys** — Create Playwright tests for user flows
2. **Run E2E Tests** — Execute tests across browsers
3. **Capture Artifacts** — Screenshots, videos, traces on failures
4. **Identify Flaky Tests** — Quarantine unstable tests

## When to Use

- Testing critical user journeys (login, trading, payments)
- Verifying multi-step flows work end-to-end
- Testing UI interactions and navigation
- Validating integration between frontend and backend
- Preparing for production deployment

## Workflow

1. Analyze user flow and identify test scenarios
2. Generate Playwright test using Page Object Model pattern
3. Run tests across multiple browsers (Chrome, Firefox, Safari)
4. Capture failures with screenshots, videos, and traces
5. Generate report with results and artifacts
6. Identify flaky tests and recommend fixes
