# Test Strategy

## Objective

Provide maintainable, risk-focused checks for the current airline demo and a separately configured provider sandbox. The suite is for learning and portfolio demonstration, not production certification.

## Scope

- UI: basic flight search interaction and the demo's simulated booking path.
- Modeled WebMCP API behaviors: flight search/filtering and booking-related operations such as cancellation/payment, with contract limitations called out in `../environments/targets.md`.
- DRCT sandbox: connectivity/ping, offer search, and invalid offer pricing only.

Not currently covered: real reservation fulfillment, provider order creation, live payment, ticket issuance, production integrations, exhaustive accessibility, load/performance qualification, or a published WebMCP contract.

## Test design

1. Prefer observable user outcomes and stable accessible locators for UI checks.
2. Keep scenarios independent; do not rely on test execution order or shared mutable bookings.
3. Use synthetic data and environment-specific configuration.
4. Check positive paths and high-value negative/validation paths.
5. Assert response status, essential response shape, and meaningful business invariants without overfitting to incidental fields.
6. Treat external sandbox failures separately from application regressions; retain enough sanitized diagnostics to investigate.
7. Keep API and browser tests isolated by target and configuration.

## Test levels

| Level | Purpose | Current examples |
| --- | --- | --- |
| UI smoke | Verify primary browser interactions | Flight search and simulated booking flow |
| API behavior | Exercise modeled demo endpoints | Search/filter and booking/payment behaviors |
| Sandbox integration | Verify limited non-production provider behavior | Ping, offer search, invalid offer pricing |

## Reliability and reporting

Use explicit waits for user-visible state, avoid fixed sleeps, and keep retries from masking flaky assertions. Reports and traces are diagnostic artifacts, not proof by themselves; inspect and sanitize before sharing. A test failure should include the target, operation, and safe response context without exposing credentials or personal data.

## Contract and AI boundaries

The WebMCP API cases are expectations rather than verified contract tests until an authoritative schema or stable provider documentation is available. If AI analysis is introduced, it may summarize patterns or suggest investigation steps, but deterministic assertions remain the pass/fail authority. Do not let an AI agent execute purchases, modify source, or suppress failures automatically.

## Future work

Prioritize a verified contract, schema-based response validation, broader accessibility checks, CI execution with protected secrets, and carefully scoped sandbox lifecycle tests only after permissions and cleanup behavior are established.
