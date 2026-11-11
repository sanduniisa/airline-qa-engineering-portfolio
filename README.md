# AeroTest AI Engineering Portfolio

A public portfolio of airline-domain quality engineering practices with TypeScript and Playwright. The implementation is maintained in the private `airline-integrated-qa-automation` repository; this repository contains documentation and sanitized examples only.

## Portfolio Contents

- [Architecture overview](docs/architecture/OVERVIEW.md)
- [Airline domain glossary](docs/airline-domain/GLOSSARY.md)
- [Demo and sandbox targets](docs/environments/targets.md)
- [Test strategy](docs/test-strategy/STRATEGY.md)
- [Flight-search test cases](docs/test-cases/flight-search.md)
- [Passenger-journey test cases](docs/test-cases/passenger-journey.md)
- [DRCT API test coverage](docs/test-cases/drct-api.md)
- [Engineering decisions](docs/case-study/engineering-decisions.md)

## Current Implementation Scope

- WebMCP Airline demo: browser-based flight-search checks.
- DRCT sandbox: separate offer, order and ticket-reporting checks, offline client checks, and an opt-in booking-to-ticket scenario.
- Reservations and ticketing is the current capability; DCS is planned for later.

The WebMCP demo has no verified REST contract for the modeled routes and has no active API specs. The DRCT ticketing journey is implemented but has not yet been run end to end. Recent DRCT validation passed five live read-only sandbox checks and one offline client check; three booking/ticketing tests were skipped. TypeScript type-check passed.

This is a practice and portfolio project, not a production airline system or verified provider integration. Planned capabilities are labeled as future work.

## Engineering Principles

- Use synthetic passenger and payment data only.
- Keep provider sandboxes isolated and follow their access rules.
- Do not publish credentials, `.env` files, raw traces, or unsanitized test artifacts.
- Deterministic assertions decide test outcomes. Any future AI recommendations require human review and do not silently modify code or pass/fail results.

## Technology Direction

Current implementation uses TypeScript, Playwright Test, and Playwright APIRequestContext. One offline client test uses a mock request context; comprehensive network mocking, Zod schema validation, BDD, and AI-assisted analysis are future work.

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
