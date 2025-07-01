---
description: Typescript rules for NodeJS 
globs: 
  - "*.ts"
alwaysApply: false
---

# TypeScript Node.js Backend Rules

- For functions with more than 3 arguments, define an interface for the parameters.
- Always define an interface or type for returned objects; avoid inline structures.
- Avoid using require() in TypeScript modules, use `import type` for type-only imports.
- Wrap all external async calls in try/catch or handle rejection explicitly.
- Avoid direct access to global objects (global, process, or setTimeout) wrap them in utility functions.
- Avoid complex inline union/intersection types; use descriptive named types.
- Enable `"strict": true` in `tsconfig.json`.
- Prefer `type` over `interface` unless you need extension or merging.
- Avoid using `any`; prefer `unknown` or more specific types.
- Use enums or literal types for sets of constants.
- Do not expose sensitive environment variables (`process.env.*`) in logs or responses.
- Prefer composition over inheritance in backend service design.
- Avoid top-level `await` in modules; place it inside async functions.
- Implement custom error classes that extend `Error`.
- Use structured logging instead of `console.log` in production.
- Batch similar async operations using `Promise.all` or equivalent.
- Avoid using await inside Array.prototype.forEach, as it does not wait for the asynchronous operations to complete. Use for...of or Promise.all with map instead.
- Document complex business logic and algorithms with comments or JSDoc.
- Ensure that error messages returned to clients do not expose internal implementation details.
- Always annotate the return types of exported functions explicitly to ensure consistent interfaces.
- Organize imports by category (Node.js built-ins, third-party modules, internal modules) and sort them alphabetically.