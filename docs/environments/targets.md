# Test Targets and Environments

The project uses two deliberately separate targets. Their behavior and risk are not interchangeable.

## WebMCP Airline demo

- URL: https://webmcp-airline.vercel.app/
- Purpose: browser UI practice for flight search and a simulated booking flow.
- Contract status: no verified REST contract or active API specs; a previously modeled `POST /flights/search` returned HTTP 405.
- Data: use synthetic traveler details only. Do not enter real payment or passenger data.

## DRCT API sandbox

- Base URL: https://sandbox-api.drct.aero
- Purpose: isolated provider sandbox checks.
- Current coverage: ping, offer search, invalid offer pricing, and order and ticket-reporting lists. Two order-creation examples and a search-to-ticket journey are implemented behind explicit opt-ins; the full journey has not been run end to end.
- Safety: tests restrict the target to the official sandbox host. Order creation requires `DRCT_RUN_BOOKING_TESTS=true`; the ticketing journey additionally requires `DRCT_RUN_TICKETING_TESTS=true`. Production endpoints and real payment are out of scope.
- Secrets: provide credentials only through local environment configuration. Never commit keys, `.env` files, request headers containing secrets, or credential-bearing logs.

## Environment handling

1. Keep demo and provider-sandbox configuration separate.
2. Use non-production credentials and data only.
3. Avoid destructive or purchase-like operations unless specifically authorized by the sandbox owner.
4. Capture only sanitized diagnostics. Review traces, screenshots, and reports before any publication.
5. Re-check provider terms, endpoint documentation, and rate limits before running tests; sandbox behavior can change.

A successful sandbox response demonstrates only the tested sandbox interaction. It does not establish production readiness, full airline integration, inventory availability, or ticketing capability.
