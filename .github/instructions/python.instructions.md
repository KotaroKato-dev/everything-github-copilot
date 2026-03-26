---
applyTo: "**/*.py,**/*.pyi"
---

# Python Coding Style

## Standards

- Follow **PEP 8** conventions
- Use **type annotations** on all function signatures

## Immutability

Prefer immutable data structures:
- Use `@dataclass(frozen=True)` for value types
- Use `NamedTuple` for simple immutable containers
- Return new copies instead of mutating

## Formatting

- **black** for code formatting
- **isort** for import sorting
- **ruff** for linting

## Error Handling

- Use specific exception types
- Always include context in error messages
- Never use bare `except:` — catch specific exceptions

## Type Annotations

- Annotate all function parameters and return types
- Use `Optional[T]` for nullable values
- Use `TypeVar` and `Generic` for generic functions and classes
