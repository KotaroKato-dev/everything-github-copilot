---
applyTo: "**/*.rs"
---

# Rust Coding Style

## Formatting

- **rustfmt** for enforcement — always run `cargo fmt` before committing
- **clippy** for lints — `cargo clippy -- -D warnings` (treat warnings as errors)

## Immutability

- Use `let` by default; only use `let mut` when mutation is required
- Prefer returning new values over mutating in place
- Use `Cow<'_, T>` when a function may or may not need to allocate

## Ownership and Borrowing

- Borrow (`&T`) by default; take ownership only when you need to store or consume
- Never clone to satisfy the borrow checker without understanding the root cause
- Accept `&str` over `String`, `&[T]` over `Vec<T>` in function parameters
- Use `impl Into<String>` for constructors that need to own a `String`

## Error Handling

- Use `Result<T, E>` and `?` for propagation — never `unwrap()` in production code
- Libraries: define typed errors with `thiserror`
- Applications: use `anyhow` for flexible error context
- Add context with `.with_context(|| format!("failed to ..."))?`
- Reserve `unwrap()` / `expect()` for tests and truly unreachable states

## Naming

- `snake_case` for functions, methods, variables, modules, crates
- `PascalCase` for types, traits, enums, type parameters
- `SCREAMING_SNAKE_CASE` for constants and statics

## Iterators Over Loops

Prefer iterator chains for transformations; use loops for complex control flow.

## Visibility

- Default to private; use `pub(crate)` for internal sharing
- Only mark `pub` what is part of the crate's public API
