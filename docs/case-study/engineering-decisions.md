# Engineering Decisions and Lessons

## Keep the public portfolio documentation-first

The implementation belongs in a separate private repository. Publishing architecture and test-design documents provides a reviewable portfolio while reducing accidental exposure of credentials, proprietary implementation details, and raw test data. Public examples should remain synthetic and small.

## Separate the demo from the provider sandbox

The WebMCP Airline demo is used for browser practice and modeled booking/API behavior. DRCT is a separate API sandbox with a narrower current scope. Separate configuration prevents assumptions, credentials, and failure modes from bleeding across targets.

## Be precise about API confidence

The WebMCP routes are not supported by a checked-in official OpenAPI contract. A modeled search POST returned HTTP 405, so labeling these cases as authoritative contract tests would overstate confidence. The practical decision is to document that uncertainty, verify the current interface before expanding coverage, and prefer published provider documentation when available.

## Use deterministic checks as the authority

Test code should decide pass/fail using explicit assertions. AI may help summarize failures or suggest likely causes in future work, but it should not change code, suppress tests, or trigger booking/payment actions autonomously. This keeps results explainable and reviewable.

## Avoid overstating lifecycle coverage

A search result, priced offer, simulated booking, provider order, payment settlement, and ticket issuance are distinct states. DRCT coverage currently stops at ping, offer search, and invalid offer pricing. It does not create orders or issue tickets. This limitation is documented rather than bridged with an unverified claim.

## Prefer incremental risk-based coverage

Begin with stable UI smoke tests and targeted API behavior checks. Add schema validation, broader accessibility coverage, CI secret management, and lifecycle operations only when the contract, permissions, and cleanup strategy are clear. A larger test count is not useful if the assertions target unstable or misunderstood behavior.

## Lessons

- A working test harness does not prove that the target API contract is correct.
- Sandbox success is not evidence of production readiness.
- Test reports, screenshots, and traces can contain sensitive data and need review before publication.
- Explicit boundaries make a portfolio more credible than presenting planned work as completed.
