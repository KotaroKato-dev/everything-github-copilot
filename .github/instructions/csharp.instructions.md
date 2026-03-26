---
applyTo: "**/*.cs,**/*.csx"
---

# C# Coding Style

## Standards

- Follow current .NET conventions and enable nullable reference types
- Prefer explicit access modifiers on public and internal APIs
- Keep files aligned with the primary type they define

## Types and Models

- Prefer `record` or `record struct` for immutable value-like models
- Use `class` for entities or types with identity and lifecycle
- Use `interface` for service boundaries and abstractions
- Avoid `dynamic` in application code; prefer generics or explicit models

## Immutability

- Prefer `init` setters, constructor parameters, and immutable collections for shared state
- Do not mutate input models in-place when producing updated state
- Use `with` expressions for record updates

## Async and Error Handling

- Prefer `async`/`await` over blocking calls like `.Result` or `.Wait()`
- Pass `CancellationToken` through public async APIs
- Throw specific exceptions and log with structured properties

## Formatting

- Use `dotnet format` for formatting and analyzer fixes
- Keep `using` directives organized and remove unused imports
- Prefer expression-bodied members only when they stay readable
