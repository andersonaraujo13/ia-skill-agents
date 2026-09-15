---
name: expert-javascript-typescript
description: Develop, review, refactor, and troubleshoot JavaScript and TypeScript code across browser, library, tooling, and full-stack projects. Use for language-level design, typing, modules, asynchronous flows, testing, build configuration, code quality, and framework-agnostic application logic; use a runtime- or framework-specific skill when that is the primary concern.
---

# Expert JavaScript and TypeScript

Build correct, maintainable JavaScript and TypeScript while preserving the project's runtime, module system, conventions, and supported environments.

## Start From the Project

- Inspect `package.json`, lockfiles, TypeScript configuration, linting, formatting, test setup, and nearby code before editing.
- Determine the runtime targets, package manager, module format, strictness settings, and public API compatibility requirements.
- Follow established conventions unless the request explicitly calls for a migration or architectural change.
- Do not replace libraries, build tools, or configuration merely because another choice is newer or preferred.

## JavaScript and TypeScript

- Prefer clear data flow, small cohesive functions, and explicit boundaries over unnecessary abstraction.
- Use TypeScript's strict checks when supported by the project. Do not weaken compiler options to hide errors.
- Prefer inference for local values and explicit types at public APIs, integration boundaries, and places where intent is otherwise unclear.
- Avoid `any`; use `unknown` with validation or narrowing when input is not trusted or not yet known.
- Model meaningful states with discriminated unions, literal types, generics, and exhaustive checks when they simplify the domain.
- Avoid unsafe assertions and non-null assertions unless an invariant is established and cannot be expressed more safely.
- Preserve runtime behavior: types do not validate external input. Validate network, storage, environment, and user-provided data at runtime.
- Prefer immutable transformations when they improve predictability, but do not copy large structures without a concrete benefit.

## Modules and APIs

- Respect the existing ESM or CommonJS model, file extensions, package exports, and resolver configuration.
- Do not mix module systems accidentally or rely on transpiler behavior that differs from the target runtime.
- Keep exported APIs deliberate and minimal. Preserve backward compatibility unless a breaking change is requested.
- Avoid adding dependencies for behavior that is small, stable, and clear with platform APIs; reuse installed dependencies when appropriate.

## Asynchronous Code and Errors

- Use `async`/`await` where it makes control flow clearer, and handle promise rejection at an appropriate boundary.
- Run independent asynchronous work concurrently only when ordering and resource limits permit it.
- Preserve useful error context and causes. Do not silently swallow failures.
- Support cancellation, cleanup, timeouts, or bounded concurrency when the operation's lifetime or scale requires them.
- Do not expose secrets, tokens, personal data, or complete untrusted payloads in logs and errors.

## Browser and Shared Code

- Treat DOM input, storage, URLs, and remote responses as untrusted boundaries.
- Preserve accessibility and progressive enhancement when changing browser-facing behavior.
- Avoid assuming browser APIs exist in server, worker, test, or SSR environments; isolate environment-specific code.
- Keep shared modules free of unintended global state and import-time side effects.

## Testing and Verification

- Test observable behavior and important edge cases rather than implementation details.
- Add or update focused tests for changed logic, including rejection and invalid-input paths where relevant.
- Run the project's formatter, linter, type checker, tests, and build in proportion to the change.
- Report commands run and any checks that could not be completed; do not claim success when required verification failed.

