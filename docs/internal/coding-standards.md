# Coding standards

Use these conventions for TypeScript implementation. [Web](web.md), [Agent runtime](agent-runtime.md), and [Contracts](contracts.md) own area-specific rules.

## Readable code

- Prefer straightforward control flow, early returns, and clear names over micro-optimizations.
- Extract constants for magic numbers and strings. Keep inline styles minimal; use classes or computed style helpers.
- Use `import type`, double-quoted strings, and `const` unless reassignment is needed.
- Use kebab-case for files and folders.
- Inline single-line helpers with only one call site.
- Reuse existing shared logic. Extract a module when behavior is genuinely shared, not to anticipate hypothetical reuse.

## Imports and logging

- Use package or path aliases such as `@/...`, `@assets/...`, and `@supernova/...`. Do not use relative TypeScript imports (`./` or `../`) or `.ts`/`.tsx` extensions.
- Follow area-specific import rules when code is consumed by another workspace. Agent runtime source imports must use `@supernova/agent-runtime/...` where they need to typecheck from dependent packages.
- Do not create local `index.ts` barrels. The deliberate exception is the public `schemas` and `procedures` exports in [Contracts](contracts.md#exports).
- Keep logging minimal and purposeful. Remove noisy debugging output introduced during the work.

## Implementation layout

These rules apply to implementation logic regardless of its folder: operations, helpers, mappers, resolvers, builders, state holders, and lifecycle coordinators.

- Order function declarations as non-exported functions, then exported functions.
- Add short TSDoc comments to exported functions, exported classes, and their public methods. Document non-exported behavior when it is not trivial.

Component declaration order belongs in [Web](web.md#components-and-hooks); schema declaration order belongs in [Contracts](contracts.md#schema-organization).
