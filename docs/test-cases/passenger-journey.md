# Passenger Journey Test Cases

This document describes a simulated UI/API flow. It does not represent a complete airline order, payment, or ticket lifecycle.

| ID | Stage | Scenario | Expected check |
| --- | --- | --- | --- |
| PJ-01 | Search | Select a valid demo flight and continue | The selected option remains identifiable in the next simulated step. |
| PJ-02 | Passenger details | Submit synthetic passenger details | Required fields are validated and accepted values are carried forward. |
| PJ-03 | Validation | Omit a required passenger field or use an invalid format | The flow remains at the appropriate step and exposes a useful validation state. |
| PJ-04 | Booking | Submit the simulated booking request | A success response/state includes a stable booking reference or equivalent demo identifier. |
| PJ-05 | Cancellation | Cancel a known synthetic demo booking, where supported | The operation reports the expected modeled outcome and does not affect unrelated data. |
| PJ-06 | Payment | Exercise the modeled payment-processing behavior with test values only | The response is interpreted as demo behavior, never as a real charge or financial settlement. |
| PJ-07 | Failure handling | Use an invalid booking/flight identifier | The API reports a controlled error; the UI does not show false success. |

## Safety and data

All passenger values must be fabricated and non-identifying. Do not use real card numbers, personal contacts, passport details, or production credentials. Avoid lifecycle operations that create durable external state unless the target owner authorizes them and cleanup is understood.

## Interpretation

A successful simulated booking or modeled payment response validates only that specific demo path. It does not prove provider reservation, order acceptance, financial settlement, ticket issuance, or airline operational readiness. DRCT sandbox coverage is separate and currently stops at ping, offer search, and invalid offer pricing.
