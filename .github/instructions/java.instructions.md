---
applyTo: "**/*.java"
---

# Java Coding Style

## Formatting

- **google-java-format** or **Checkstyle** for enforcement
- One public top-level type per file
- Member order: constants, fields, constructors, public methods, protected, private

## Immutability

- Prefer `record` for value types (Java 16+)
- Mark fields `final` by default
- Return defensive copies from public APIs: `List.copyOf()`, `Map.copyOf()`
- Return new instances rather than mutating existing ones

## Modern Java Features

- **Records** for DTOs and value types (Java 16+)
- **Sealed classes** for closed type hierarchies (Java 17+)
- **Pattern matching** with `instanceof` (Java 16+)
- **Text blocks** for multi-line strings (Java 15+)
- **Switch expressions** with arrow syntax (Java 14+)

## Optional Usage

- Return `Optional<T>` from finder methods that may have no result
- Use `map()`, `flatMap()`, `orElseThrow()` — never call `get()` without `isPresent()`
- Never use `Optional` as a field type or method parameter

## Error Handling

- Prefer unchecked exceptions for domain errors
- Create domain-specific exceptions extending `RuntimeException`
- Avoid broad `catch (Exception e)` unless at top-level handlers
- Include context in exception messages

## Streams

- Use streams for transformations; keep pipelines short (3-4 operations max)
- Prefer method references when readable
- Avoid side effects in stream operations

## Naming

- `PascalCase` for classes, interfaces, records, enums
- `camelCase` for methods, fields, parameters, local variables
- `SCREAMING_SNAKE_CASE` for `static final` constants
