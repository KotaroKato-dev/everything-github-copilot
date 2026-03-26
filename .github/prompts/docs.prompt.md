---
agent: agent
description: "Look up current documentation for a library or topic. Returns summarized answers with relevant code snippets."
tools: ['codebase', 'fetch']
---

# Documentation Lookup

Look up up-to-date documentation for a library, framework, or API and return a summarized answer with relevant code snippets.

## Usage

Provide:
1. The library or product name (e.g., Next.js, Prisma, Supabase)
2. The specific question or task (e.g., "How do I set up middleware?")

## Workflow

1. Search for current documentation for the specified library
2. Find relevant sections addressing the user's question
3. Summarize the answer concisely
4. Include relevant code examples from the documentation
5. Mention the library version if relevant

## Output

A short, accurate answer backed by current docs, plus any code snippets that help. If documentation cannot be found, answer from knowledge with a note that docs may be outdated.
