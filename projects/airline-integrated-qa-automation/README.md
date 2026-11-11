# Airline Integrated QA Automation

A Playwright and TypeScript test framework for airline reservation and ticketing workflows, combining browser UI automation with provider-specific API integration tests.

## Demonstrated coverage

- DRCT sandbox passenger journey: search and price an offer, create and retrieve an order, issue tickets, and reconcile ticket reporting.
- Browser-based flight search and booking flows.
- Contract-level checks for the DRCT API client's request wiring.
- Travelport TripServices Postman requests maintained as a separate provider integration reference.

The DRCT booking and ticketing journey is opt-in and requires sandbox credentials and explicit environment flags. The Travelport requests are examples/templates and do not imply that Travelport API access or bookings have been validated by this project.

## Security

No credentials, access tokens, PCCs, or organization identifiers are included. Configure credentials and provider-specific IDs in a private local Postman environment before running requests. Never use production credentials or real passenger data for these examples.

## Source project

The implementation is maintained in the private `airline-integrated-qa-automation` repository. These portfolio materials are a sanitized overview and runnable request references only.