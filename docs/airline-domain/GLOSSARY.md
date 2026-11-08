# Airline Domain Glossary

This glossary establishes the terms used in the portfolio's test scenarios. Provider-specific meanings may differ; the demo behavior is not a substitute for an airline's commercial or operational rules.

| Term | Meaning in this portfolio |
| --- | --- |
| Airport code | IATA-style three-letter identifier used as a search origin or destination in examples. |
| Origin / destination | The departure and arrival airport codes for a requested itinerary. |
| Flight | A scheduled air-service option shown in a search result. It is not necessarily a bookable inventory item. |
| Itinerary | The selected travel plan. Current UI examples focus on a simple one-way search and a simulated booking flow. |
| Passenger | A traveler represented with synthetic test data. No real passenger data belongs in this repository. |
| Offer | A priced travel proposal returned by a provider API. A search result or offer is not an order or ticket. |
| Booking | A reservation-like object in the demo's simulated flow or modeled API tests. Semantics depend on the target system. |
| Payment processing | A modeled/demo operation. The portfolio does not process real payments. |
| Order | A provider-side purchase record, generally created after acceptance/payment according to provider rules. No DRCT order creation is currently tested. |
| Ticket | A travel document issued after required provider steps. Ticket issuance is outside current scope. |
| Sandbox | A provider-controlled non-production environment. It may have different availability, limits, and behavior from production. |
| Contract test | A check against a known interface contract. The WebMCP route expectations here are provisional and are not backed by a published OpenAPI specification. |
| UI smoke test | A short browser test that checks a key screen or interaction path, not exhaustive business correctness. |
| Deterministic assertion | An explicit expected condition evaluated by the test runner; it is the authority for pass/fail. |

## State distinction

Search results, offers, bookings, orders, payments, and tickets are separate concepts. Passing a search or pricing test does not prove that a reservation, order, payment, or ticket can be completed.
