# Test Strategy

## Objective

Provide maintainable, risk-focused checks for the current airline demo and a separately configured provider sandbox. The suite is for learning and portfolio demonstration, not production certification.

## Scope

- UI: basic flight search interaction and the demo's simulated booking path.
- WebMCP has no verified REST contract or active API tests.
- DRCT sandbox: ping, offer search, invalid offer pricing, and order and ticket-reporting lists; an opt-in booking-to-ticket journey is implemented but not yet run end to end.

Not currently demonstrated: real reservation fulfillment, live payment, real ticket issuance, production integrations, exhaustive accessibility, load/performance qualification, or a published WebMCP contract.

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
| Offline client check | Verify request wiring without a provider call | DRCT paths, headers, and selected payloads |
| Sandbox integration | Verify non-production provider behavior | Ping, offer search, invalid offer pricing, order/ticket lists |
| Sandbox journey | Connect lifecycle operations | Opt-in search through ticket reporting; not yet run end to end |

## Reliability and reporting

Use explicit waits for user-visible state, avoid fixed sleeps, and keep retries from masking flaky assertions. Reports and traces are diagnostic artifacts, not proof by themselves; inspect and sanitize before sharing. A test failure should include the target, operation, and safe response context without exposing credentials or personal data.

## Contract and AI boundaries

WebMCP API cases are not active until an authoritative contract is available. The DRCT offline client test checks request wiring, not live provider response schemas. If AI analysis is introduced, it may summarize patterns or suggest investigation steps, but deterministic assertions remain the pass/fail authority. Do not let an AI agent execute purchases, modify source, or suppress failures automatically.

## Future work

Prioritize a verified WebMCP contract, schema-based response validation, broader accessibility checks, CI execution with protected secrets, and validated sandbox lifecycle execution with appropriate permissions and cleanup policies.
