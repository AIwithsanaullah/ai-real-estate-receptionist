# Setup Guide

This is a platform-neutral implementation checklist. It is not a ready-to-import n8n workflow.

## 1. Define the scope

- Select one channel for the first test (website chat, voice, or an approved messaging provider).
- Decide which property fields are approved for AI answers.
- Define when the system must transfer to a human.
- Decide whether the first version only qualifies enquiries or also supports bookings.
- Confirm privacy, consent, retention, and access requirements with the business.

## 2. Prepare the data

Create a small synthetic property catalogue with stable IDs and fields such as title, area, type, price, availability status, and approved description. Mark unknown values as unknown. Do not use real customer data in public tests.

## 3. Build the workflow

Suggested stages:
1. Receive the enquiry.
2. Validate the event and identify the conversation.
3. Classify intent.
4. Retrieve matching property facts from the approved source.
5. Draft a response under the system prompt.
6. Validate the response and decide whether to answer or escalate.
7. If booking is enabled, check calendar availability and ask for confirmation.
8. Save a minimal lead record and operational outcome.
9. Log errors without exposing secrets or unnecessary personal data.

## 4. Configure integrations privately

Add provider credentials only through the platform's credential manager or environment secrets. Do not commit API keys, webhook secrets, phone numbers, or exported customer conversations.

For n8n, configure credentials and node parameters in the n8n instance. This repository does not include provider-specific node IDs or an importable workflow JSON.

## 5. Acceptance tests

- Property exists and all requested fields are present.
- Property does not exist in the approved source.
- Price or availability is missing.
- User gives contradictory details.
- Calendar has no available slots.
- User changes their mind before booking.
- Calendar or CRM API fails.
- Duplicate enquiry arrives.
- User asks for a human or opts out.
- User asks for another customer's data.

## 6. Before launch

- Run tests with synthetic data.
- Confirm every factual answer is grounded in the approved source.
- Verify booking and human-handoff paths end to end.
- Check permissions and retention settings.
- Monitor errors and provide a manual fallback.
- Do not describe the system as production-ready until the actual integrations have been tested.
