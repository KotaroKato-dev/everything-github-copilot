---
agent: agent
description: "Restate requirements, assess risks, and create step-by-step implementation plan. WAIT for user CONFIRM before touching any code."
tools: ['codebase', 'fetch']
---

# Implementation Plan

Invoke the **planner** agent to create a comprehensive implementation plan before writing any code.

## What This Prompt Does

1. **Restate Requirements** — Clarify what needs to be built
2. **Identify Risks** — Surface potential issues and blockers
3. **Create Step Plan** — Break down implementation into phases
4. **Wait for Confirmation** — MUST receive user approval before proceeding

## When to Use

- Starting a new feature
- Making significant architectural changes
- Working on complex refactoring
- Multiple files/components will be affected
- Requirements are unclear or ambiguous

## Workflow

1. Analyze the request and restate requirements in clear terms
2. Break down into phases with specific, actionable steps
3. Identify dependencies between components
4. Assess risks and potential blockers
5. Estimate complexity (High/Medium/Low)
6. Present the plan and WAIT for explicit confirmation

**CRITICAL**: Do NOT write any code until the user explicitly confirms the plan with "yes", "proceed", or similar affirmative response.
