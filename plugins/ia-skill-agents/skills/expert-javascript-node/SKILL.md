---
name: expert-javascript-node
description: Develop, review, refactor, and troubleshoot Node.js applications and packages in JavaScript or TypeScript. Use for HTTP services, workers, CLI tools, streams, filesystem and process integration, package design, observability, security, performance, and Node-specific testing; use a framework-specific skill when framework conventions dominate the task.
---

# Expert JavaScript Node.js

Build reliable Node.js software that fits the project's supported Node version, module system, operational environment, and existing architecture.

## Establish the Runtime Contract

- Inspect `package.json`, lockfiles, engine constraints, TypeScript configuration, entry points, scripts, tests, and deployment files before editing.
- Confirm the supported Node version, package manager, ESM or CommonJS model, execution environment, and framework conventions.
- Preserve existing APIs, environment-variable names, process behavior, and operational assumptions unless the request changes them.
- Prefer built-in Node APIs when they are sufficient and compatible with the supported version; do not add dependencies without a concrete benefit.

## Architecture and Boundaries

- Separate transport, application logic, domain logic, and infrastructure when that separation provides a real testing or maintenance benefit.
- Keep framework request and response objects at the transport boundary rather than passing them through core logic.
- Validate and normalize configuration once at startup. Fail early with actionable errors for missing or invalid required configuration.
- Inject clocks, identifiers, clients, or persistence boundaries when nondeterminism or external I/O needs isolation in tests.
- Avoid import-time connections, hidden mutable singletons, and other side effects that make startup and tests unpredictable.

## Async I/O, Streams, and Processes

- Handle promise rejections and callback errors; preserve the original error as a cause when adding context.
- Use bounded concurrency for large or untrusted workloads. Avoid unbounded `Promise.all` over potentially large collections.
- Respect stream backpressure and use pipeline utilities that propagate errors and clean up resources.
- Close servers, clients, timers, file handles, and workers during shutdown and failure paths.
- Implement graceful shutdown when the application owns long-lived resources: stop accepting work, finish or cancel in-flight work within a bound, release resources, and exit with a meaningful status.
- Treat process-wide handlers as a last-resort reporting and shutdown boundary, not as a way to resume normal execution after an unknown failure.

## Services, CLIs, and Packages

- For HTTP services, validate input at the boundary, use appropriate status semantics, and keep error responses free of internal details.
- Apply timeouts, request-size limits, authentication, authorization, and rate or concurrency controls according to the service's exposure and risk.
- For CLIs, keep stdout suitable for intended output and stderr for diagnostics; return meaningful exit codes and handle signals when cleanup is needed.
- For packages, define exports deliberately, avoid leaking internal modules, and verify published file contents and type declarations when packaging changes.
- Maintain compatibility with the project's module resolution and avoid ambiguous dual-package behavior.

## Security and Operations

- Never commit or log secrets. Treat environment variables, files, network data, command arguments, and serialized content as untrusted input.
- Avoid command injection: prefer argument-array process APIs without a shell and never concatenate untrusted input into commands.
- Prevent path traversal by resolving and checking paths against an intended root before reading, writing, moving, or deleting files.
- Use structured, contextual logs where the project supports them, with appropriate levels and redaction.
- Add metrics, tracing, or health checks only when they fit the application's operational model and the requested scope.

## Performance and Testing

- Measure before optimizing. Watch for event-loop blocking, excessive serialization, memory retention, repeated I/O, and unbounded queues.
- Test observable behavior at the narrowest useful boundary; mock external systems rather than Node internals where practical.
- Cover startup configuration, failure paths, cleanup, and shutdown behavior when they are affected.
- Run the project's formatter, linter, type checker, tests, and build. Exercise the relevant service, CLI, or package entry point when feasible.
- Report commands run and environmental limitations; do not claim completion if required checks fail.

