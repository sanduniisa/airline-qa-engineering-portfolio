# AeroTest AI Engineering Portfolio

A public portfolio showing airline-domain quality engineering practices with TypeScript and Playwright. The complete implementation remains in the private `airline-integrated-qa-automation` repository; this repository contains documentation and sanitized examples only.

## Portfolio contents

- [Architecture overview](docs/architecture/OVERVIEW.md)
- [Airline domain glossary](docs/airline-domain/GLOSSARY.md)
- [Demo and sandbox targets](docs/environments/targets.md)
- [Test strategy](docs/test-strategy/STRATEGY.md)
- [Flight-search test cases](docs/test-cases/flight-search.md)
- [Passenger-journey test cases](docs/test-cases/passenger-journey.md)
- [Engineering decisions](docs/case-study/engineering-decisions.md)

## Current scope

The private implementation has Playwright UI automation for basic flight search and a simulated booking flow, WebMCP API test wrappers for flight/booking/payment behaviors, and a separate DRCT sandbox suite for ping, offer search, and invalid offer pricing. The WebMCP API routes are local test expectations rather than an official published contract; a modeled flight-search POST previously returned HTTP 405. DRCT tests do not create orders or issue tickets.

This is a practice and portfolio project, not a production airline system or verified airline-provider integration. Planned capabilities are labeled as future work, not current features.

## Principles

- Use synthetic passenger and payment data only.
- Keep provider sandboxes isolated and follow their access rules.
- Do not publish credentials, `.env` files, raw traces, or unsanitized test artifacts.
- Deterministic assertions decide test outcomes. AI recommendations, if added, require human review and do not silently modify code or pass/fail results.

## Technology direction

TypeScript, Playwright Test, Playwright `APIRequestContext`, and GitHub Actions as implementation evolves. Zod schema validation, BDD, network mocking, and AI-assisted analysis are planned capabilities unless a document explicitly identifies a completed implementation.

## Repository structure

```text
docs/
  architecture/
  airline-domain/
  environments/
  test-strategy/
  test-cases/
  case-study/
```

See the project guide in the private implementation repository for the staged roadmap. This public repository intentionally does not duplicate its source code.
