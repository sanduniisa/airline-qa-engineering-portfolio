# Flight Search Test Cases

These cases describe observable behavior to exercise on the WebMCP Airline demo and modeled API suite. Confirm the live demo's current controls and API contract before treating any API expectation as authoritative.

| ID | Scenario | Expected check | Coverage note |
| --- | --- | --- | --- |
| FS-01 | Search with valid origin, destination, and date | Results are presented for the requested criteria; no uncaught UI error occurs. | UI smoke scenario. |
| FS-02 | Submit with a missing required value | The form identifies the required input and does not proceed as if the search succeeded. | Validate actual demo behavior; avoid asserting exact copy. |
| FS-03 | Use an invalid origin or destination code | The request is rejected or a clear validation state is shown; the test does not interpret an empty response as a valid itinerary. | API negative cases are modeled. |
| FS-04 | Filter results by airline | Every displayed result after filtering matches the selected carrier, where the demo provides that filter. | Confirm filter availability in current UI. |
| FS-05 | Filter by a price range | Displayed result prices fall within the requested bounds, subject to documented currency/rounding behavior. | Modeled API case; provider currency rules may differ. |
| FS-06 | Search for multiple passengers | The submitted passenger count is preserved or a validation message explains unsupported input. | API expectation requires confirmation against the live contract. |
| FS-07 | Search with no matching options | A stable empty state is shown and the user can change criteria. | If the demo cannot produce this state deterministically, cover with a controlled fixture in future work. |

## Data and assertions

Use synthetic airport codes, dates, and passenger counts. Avoid real names, contact details, identity documents, or payment data. Assert meaningful invariants such as criteria preservation, result structure, and filter behavior rather than fixed flight availability, which may change.

## Limitations

The modeled `POST /flights/search` returned HTTP 405 in a prior check, and there is no checked-in official OpenAPI contract. Treat API case coverage as provisional. Do not infer booking or ticket availability from search results.
