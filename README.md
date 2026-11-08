# AeroTest AI Engineering Portfolio

A public portfolio of airline-domain quality engineering practices with TypeScript and Playwright. The implementation is maintained in the private `airline-integrated-qa-automation` repository; this repository contains documentation and sanitized examples only.

## Portfolio Contents

- [Architecture overview](docs/architecture/OVERVIEW.md)
- [Airline domain glossary](docs/airline-domain/GLOSSARY.md)
- [Demo and sandbox targets](docs/environments/targets.md)
- [Test strategy](docs/test-strategy/STRATEGY.md)
- [Flight-search test cases](docs/test-cases/flight-search.md)
- [Passenger-journey test cases](docs/test-cases/passenger-journey.md)
- [Engineering decisions](docs/case-study/engineering-decisions.md)

## Current Implementation Scope

- WebMCP Airline demo: browser-based flight-search checks.
- DRCT sandbox: API checks for ping, offer search, and invalid offer pricing.
- Reservations and ticketing is the current capability; DCS is planned for later.

The WebMCP demo has no verified REST contract for the modeled routes. Its API wrappers remain provisional and have no active API specs. DRCT coverage stops before order creation, ticket issuance, and payment processing. The latest local validation recorded 12 tests passing, 0 failing, with TypeScript type-check passing.

This is a practice and portfolio project, not a production airline system or verified provider integration. Planned capabilities are labeled as future work.

## Engineering Principles

- Use synthetic passenger and payment data only.
- Keep provider sandboxes isolated and follow their access rules.
- Do not publish credentials, `.env` files, raw traces, or unsanitized test artifacts.
- Deterministic assertions decide test outcomes. Any future AI recommendations require human review and do not silently modify code or pass/fail results.

## Technology Direction

Current implementation uses TypeScript, Playwright Test, and Playwright APIRequestContext. Zod schema validation, BDD, network mocking, and AI-assisted analysis are planned unless a document explicitly identifies a completed implementation.

## Documentation Layout

```text
docs/
  architecture/
  airline-domain/
  environments/
  test-strategy/
  test-cases/
  case-study/
```

See the private implementation repository's README for setup and run commands.
