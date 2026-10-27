# AI Real Estate Receptionist

**A reference design for AI-assisted real-estate enquiries, lead qualification, and appointment workflows.**

Built by [Sana Ullah](https://github.com/AIwithsanaullah) · [NEXORA AI Solutions](https://nexoraaihq.com/)

> **Project status:** Documentation and prompt examples. This repository does not currently include a verified, importable production workflow or a live deployment. Do not treat the proposed integrations as already connected.

## Problem

Real-estate teams handle repetitive enquiries about property availability, price, location, viewing times, and next steps. A carefully bounded assistant can collect the required details, answer only from approved property information, and hand off uncertain or high-priority enquiries to a human.

## Proposed workflow

1. Receive an enquiry from an authorized channel.
2. Identify the user's intent and collect missing qualification details.
3. Search an approved property knowledge source before answering property-specific questions.
4. Offer a viewing only after checking real calendar availability.
5. Ask for confirmation before creating or changing a booking.
6. Record the lead and a concise conversation summary.
7. Escalate unsupported questions, complaints, and high-intent leads to a person.

## Suggested integrations

| Component | Possible role |
|---|---|
| n8n | Workflow orchestration |
| OpenAI-compatible model | Intent detection and response drafting |
| Supabase or Google Sheets | Lead records, depending on project requirements |
| Approved property catalogue | Grounded property answers |
| Google Calendar | Availability checks and confirmed bookings |
| WhatsApp or voice provider | Customer channel, after access and consent are configured |

These are design options, not claims that each service is configured in this repository.

## Reliability rules

- Never invent property availability, price, amenities, or location details.
- If the approved source does not contain an answer, say so and offer a human handoff.
- Confirm date, time, timezone, and contact details before booking.
- Prevent duplicate bookings and duplicate lead creation where possible.
- Keep a traceable record of tool errors and handoffs.
- Respect channel consent, opt-out requests, and applicable messaging rules.

## Repository contents

- [System prompt](prompts/system-prompt.md) — assistant boundaries and tool-use rules.
- [Setup guide](docs/setup-guide.md) — implementation checklist.
- [Test cases](tests/test-cases.md) — expected behavior for common and edge cases.

## Testing before deployment

Use synthetic data first. Test missing information, contradictory property details, unavailable viewing slots, repeated enquiries, provider failures, and requests for a human. Do not publish real customer chats, phone numbers, access tokens, or API keys.

## Contact

- Website: https://nexoraaihq.com/
- LinkedIn: https://www.linkedin.com/in/sana-ullah-4447a0427/
- GitHub: https://github.com/AIwithsanaullah
