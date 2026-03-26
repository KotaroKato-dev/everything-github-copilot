---
applyTo: "**/*.go,**/go.mod,**/go.sum"
---

# Go Coding Style

## Formatting

- **gofmt** and **goimports** are mandatory — no style debates

## Design Principles

- Accept interfaces, return structs
- Keep interfaces small (1-3 methods)

## Error Handling

Always wrap errors with context:

```go
if err != nil {
    return fmt.Errorf("failed to create user: %w", err)
}
```

- Never ignore errors without explicit justification
- Use sentinel errors or custom error types for specific cases
- Handle errors at the appropriate level

## Naming

- Use short, descriptive variable names
- Receivers: 1-2 letter abbreviation of the type
- Interfaces: single-method interfaces named with `-er` suffix
- Exported names need no package prefix

## Concurrency

- Prefer channels for communication between goroutines
- Use `sync.Mutex` for protecting shared state
- Always handle goroutine lifecycle (avoid leaks)
