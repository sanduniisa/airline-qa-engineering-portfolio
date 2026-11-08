# Test Targets and Environments

The project uses two deliberately separate targets. Their behavior and risk are not interchangeable.

## WebMCP Airline demo

- URL: https://webmcp-airline.vercel.app/
- Purpose: browser UI practice for flight search and a simulated booking flow, plus API test wrappers for flight and booking-related behaviors.
- Contract status: no official OpenAPI contract is checked into this portfolio. The test routes are modeled expectations; a modeled `POST /flights/search` returned HTTP 405 in a prior check. Treat route/method coverage as provisional and confirm behavior against the current demo before expanding it.
- Data: use synthetic traveler details only. Do not enter real payment or passenger data.

## DRCT API sandbox

- Base URL: https://sandbox-api.drct.aero
- Purpose: isolated provider sandbox checks.
- Current coverage: ping, offer search, and invalid offer pricing.
- Out of scope: order creation, payment, ticket issuance, and any production endpoint.
- Secrets: provide credentials only through local environment configuration. Never commit keys, `.env` files, request headers containing secrets, or credential-bearing logs.

## Environment handling

1. Keep demo and provider-sandbox configuration separate.
2. Use non-production credentials and data only.
3. Avoid destructive or purchase-like operations unless specifically authorized by the sandbox owner.
4. Capture only sanitized diagnostics. Review traces, screenshots, and reports before any publication.
5. Re-check provider terms, endpoint documentation, and rate limits before running tests; sandbox behavior can change.

A successful sandbox response demonstrates only the tested sandbox interaction. It does not establish production readiness, full airline integration, inventory availability, or ticketing capability.
