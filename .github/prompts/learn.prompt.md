---
agent: agent
description: "Extract reusable patterns from the current session and save them as skills or notes for future use."
tools: ['codebase', 'editFiles', 'fetch']
---

# Learn — Extract Reusable Patterns

Analyze the current session and extract any patterns worth saving.

## What to Extract

1. **Error Resolution Patterns** — What error occurred? What was the root cause? What fixed it?
2. **Debugging Techniques** — Non-obvious debugging steps, tool combinations that worked
3. **Workarounds** — Library quirks, API limitations, version-specific fixes
4. **Project-Specific Patterns** — Codebase conventions discovered, architecture decisions

## Process

1. Review the session for extractable patterns
2. Identify the most valuable/reusable insight
3. Draft a concise pattern description
4. Ask user to confirm before saving
5. Save to appropriate location

## Notes

- Don't extract trivial fixes (typos, simple syntax errors)
- Don't extract one-time issues (specific API outages, etc.)
- Focus on patterns that will save time in future sessions
- Keep skills focused — one pattern per skill
