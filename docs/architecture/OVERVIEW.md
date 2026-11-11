# Architecture Overview

AeroTest AI is an airline-domain quality engineering portfolio demonstrating test design and automation practices with TypeScript and Playwright. The implementation is maintained separately in a private repository; this public repository contains documentation and sanitized examples only.

## Design Principles

- **Airline-first:** use domain language such as itinerary, segment, reservation/PNR, fare, ticket, check-in, and ancillary accurately.
- **Target isolation:** keep each demo or provider sandbox separate. Do not reuse credentials or test records across targets.
- **Deterministic assertions:** test results are decided by explicit assertions. AI suggestions, if introduced, must not change pass/fail outcomes or edit code without human approval.
- **Test pyramid:** use API tests for broad service behavior, UI tests for critical user flows, and a smaller number of end-to-end checks.
- **Secure by default:** synthetic data only; secrets remain outside source control and reports.

## Conceptual Layers

1. **Specifications:** Playwright tests express user and API behavior.
2. **Fixtures and configuration:** manage browser/API contexts, environment URLs, timeouts, and lifecycle.
3. **Adapters:** page objects and endpoint clients isolate target-specific locators, routes, authentication, and data formats.
4. **Domain and validation:** airline business rules and response validation should be explicit and independently testable.
5. **Evidence and reporting:** retain useful, sanitized reports, screenshots, traces, and diagnostics.

## Current Demonstration Scope

- UI: WebMCP Airline demo at https://webmcp-airline.vercel.app/ for basic flight search and a simulated booking journey.
- WebMCP API: there is no verified REST contract and no active API adapter or API specs; a previously modeled flight-search POST returned HTTP 405.
- DRCT: separate sandbox checks cover ping, search, invalid pricing, and order and ticket listing. An opt-in journey implements search through ticket reporting but has not been run end to end. A mocked request-context test checks client request wiring offline.

These are practice/demo targets, not production airline integrations. Current UI/API coverage does not demonstrate a complete real reservation, payment settlement, ticket issuance, or check-in lifecycle.

## Future Architecture

As the project grows, add target-specific adapters only after confirming the target documentation, access rules, supported operations, and data-reset behavior. Broader network mocking, schema validation, BDD, and AI components remain future work; do not describe planned capabilities as current features.
