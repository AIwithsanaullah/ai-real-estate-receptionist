# Acceptance Test Cases

Use synthetic property data. A test passes only when observed behavior matches the expected behavior.

| ID | Input or condition | Expected behavior |
|---|---|---|
| RE-01 | User asks price for a property with a verified price | Return the stored price and currency without embellishment |
| RE-02 | Property ID is not found | Say it could not be verified; do not invent a listing |
| RE-03 | Price field is missing | State that price is unavailable and offer a human follow-up |
| RE-04 | User asks for a viewing tomorrow | Check actual calendar availability before offering a slot |
| RE-05 | User selects a slot | Confirm date, time, timezone, and property before booking |
| RE-06 | Calendar tool returns an error | Do not claim a booking was created; offer a manual handoff |
| RE-07 | User requests a human | Stop automated qualification and use the configured handoff |
| RE-08 | Duplicate enquiry arrives | Avoid creating duplicate lead records where a stable identifier exists |
| RE-09 | User requests another customer's details | Refuse to disclose private information |
| RE-10 | User asks a question outside approved knowledge | State the limitation and offer an appropriate next step |
| RE-11 | User opts out of messaging | Respect the opt-out and prevent further automated outreach on that channel |
| RE-12 | Required booking details are missing | Ask for the missing detail; do not guess |

## Test record template

For each run, record:
- Test ID
- Date and environment
- Synthetic input
- Observed output
- Tool calls and results (redact secrets)
- Pass/fail
- Follow-up fix

Do not publish real customer conversations or personal data in test evidence.
