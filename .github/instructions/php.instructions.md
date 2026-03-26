---
applyTo: "**/*.php,**/composer.json"
---

# PHP Coding Style

## Standards

- Follow **PSR-12** formatting and naming conventions
- Prefer `declare(strict_types=1);` in application code
- Use scalar type hints, return types, and typed properties everywhere

## Immutability

- Prefer immutable DTOs and value objects for data crossing service boundaries
- Use `readonly` properties or immutable constructors for request/response payloads
- Keep arrays for simple maps; promote business-critical structures into explicit classes

## Formatting

- Use **PHP-CS-Fixer** or **Laravel Pint** for formatting
- Use **PHPStan** or **Psalm** for static analysis
- Keep Composer scripts checked in

## Imports

- Add `use` statements for all referenced classes, interfaces, and traits
- Avoid relying on the global namespace

## Error Handling

- Throw exceptions for exceptional states; avoid returning `false`/`null` as hidden error channels
- Convert framework/request input into validated DTOs before it reaches domain logic
