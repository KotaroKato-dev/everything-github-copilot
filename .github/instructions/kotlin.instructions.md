---
applyTo: "**/*.kt,**/*.kts"
---

# Kotlin Coding Style

## Formatting

- **ktlint** or **Detekt** for style enforcement
- Official Kotlin code style (`kotlin.code.style=official`)

## Immutability

- Prefer `val` over `var` — default to `val` and only use `var` when mutation is required
- Use `data class` for value types; use immutable collections in public APIs
- Copy-on-write for state updates: `state.copy(field = newValue)`

## Null Safety

- Never use `!!` — prefer `?.`, `?:`, `requireNotNull()`, or `checkNotNull()`
- Use `?.let {}` for scoped null-safe operations
- Return nullable types from functions that can legitimately have no result

## Sealed Types

Use sealed classes/interfaces to model closed state hierarchies. Always use exhaustive `when` with sealed types — no `else` branch.

## Extension Functions

- Place in a file named after the receiver type (e.g., `StringExt.kt`)
- Keep scope limited — don't add extensions to `Any`

## Scope Functions

- `let` — null check + transform
- `run` — compute a result using receiver
- `apply` — configure an object
- `also` — side effects
- Avoid deep nesting of scope functions (max 2 levels)

## Error Handling

- Use `Result<T>` or custom sealed types
- Use `runCatching {}` for wrapping throwable code
- Never catch `CancellationException` — always rethrow it
- Avoid `try-catch` for control flow

## Naming

- `camelCase` for functions and properties
- `PascalCase` for classes, interfaces, objects, and type aliases
- `SCREAMING_SNAKE_CASE` for constants
