---
applyTo: "**/*.ts,**/*.tsx,**/*.js,**/*.jsx"
---

# TypeScript/JavaScript Coding Style

## Types and Interfaces

- Add parameter and return types to exported functions, shared utilities, and public class methods
- Let TypeScript infer obvious local variable types
- Extract repeated inline object shapes into named types or interfaces
- Use `interface` for object shapes that may be extended or implemented
- Use `type` for unions, intersections, tuples, mapped types, and utility types
- Prefer string literal unions over `enum` unless required for interoperability

### Avoid `any`

- Avoid `any` in application code
- Use `unknown` for external or untrusted input, then narrow it safely
- Use generics when a value's type depends on the caller

### React Props

- Define component props with a named `interface` or `type`
- Type callback props explicitly
- Do not use `React.FC` unless there is a specific reason

## Immutability

- Use spread operator for immutable updates: `{ ...obj, field: newValue }`
- Never mutate function arguments; return new copies

## Error Handling

- Use async/await with try-catch and narrow `unknown` errors safely
- Always log error context; throw new `Error` with meaningful messages
- Never silently swallow errors

## Input Validation

- Use Zod (or similar) for schema-based validation
- Infer types from the schema where possible

## Console.log

- No `console.log` statements in production code
- Use proper logging libraries instead

## Formatting

- Use Prettier and ESLint
- `const` by default, `let` only when reassignment is needed, never `var`
- Use `===` strict equality
