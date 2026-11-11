# DRCT Sandbox API Coverage

The private automation project separates DRCT endpoint checks from its booking journey. These tests target the provider's sandbox, not the WebMCP demo or a production airline system.

## Specifications

| Specification | Purpose | Live or offline |
| --- | --- | --- |
| `drct.api.spec.ts` | Ping, offer search, invalid-offer pricing, and two order-creation examples: direct setup and a reusable priced-offer fixture. | Sandbox; order creation is opt-in. |
| `orders.api.spec.ts` | List existing orders and check basic fields. | Sandbox; an empty list is valid. |
| `tickets.api.spec.ts` | List reporting tickets and check basic fields. | Sandbox; an empty list does not prove issuance. |
| `client-contract.api.spec.ts` | Check documented request methods, paths, headers, and selected payloads with a mocked request context. | Offline; does not validate provider response schemas. |
| `booking-journey.api.spec.ts` | Connect search, pricing, order creation and retrieval, issuance, and ticket reporting. | Sandbox; booking and ticketing require separate opt-ins. |

## Journey and Safety

The journey searches a future itinerary, prices an offer, creates an order with synthetic passenger details, and retrieves it. It then issues the order, waits for ticket numbers, and matches those numbers and the booking locator against reporting. The implementation uses idempotency keys, bounded polling, and no automatic retry after uncertain issuance. It does not automatically accept a changed price.

The fixture restricts live tests to the official HTTPS sandbox. Order creation requires `DRCT_RUN_BOOKING_TESTS=true`; the full journey also requires `DRCT_RUN_TICKETING_TESTS=true`. The full journey has **not yet been run end to end**. Ticket issuance is a payment operation in production, which this test fixture does not target.

The latest recorded DRCT validation passed five live read-only sandbox checks and one offline client check; three booking/ticketing tests were skipped. TypeScript type-check passed. The client also exposes optional servicing operations, but these do not have live end-to-end coverage.

References: [DRCT API documentation](https://docs.drct.aero/) and [DRCT OpenAPI specification](https://docs.drct.aero/openapi.yaml).