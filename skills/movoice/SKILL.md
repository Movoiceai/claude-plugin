---
name: movoice
description: Use Movoice AI to build voice agents, place and review AI phone calls, and manage contacts and bookings. Use when the user asks to create or change a calling agent, call or follow up with someone, check how calls went, read a transcript, or book, move or cancel an appointment through Movoice.
---

# Using Movoice AI

Movoice AI runs AI phone agents for businesses (Indian and international numbers, many Indian languages). The `movoice` MCP server in this plugin gives you the tools below. Every tool acts on the signed-in business's own Movoice account.

## Before you act

- **Reading is free.** `list_agents`, `get_agent`, `list_calls`, `get_call`, `get_transcript`, `get_analytics`, `list_phone_numbers`, `list_voices`, `list_contacts`, `get_availability`, `list_appointments`, `get_appointment`, `get_account` only read.
- **Ask first, every time, before anything that calls someone, sends a message, spends balance, or changes or deletes data**: `start_call`, `send_sms`, `send_whatsapp`, `hangup_call`, `create_agent`, `update_agent`, `delete_agent`, `start_agent_test_run`, `create_contact`, `update_contact`, `delete_contact`, `book_appointment`, `cancel_appointment`, `reschedule_appointment`. Say exactly what will happen (which agent, which number, which person, what it costs if known) and wait for a clear yes.
- **Only call people who expect it.** Use calls for service, bookings, reminders and follow-ups with people who gave the business their number. Never use Movoice for cold telemarketing. Indian numbers follow India's calling rules (DND and calling hours); if a call is refused for that reason, tell the user plainly instead of retrying.
- **Phone numbers** go in international form, for example `+919876543210`.

## Common jobs

1. **"Create an agent that speaks Hindi and books site visits."** Call `list_voices` if the user cares about the voice, then `create_agent` with a clear `prompt`, a short `welcomeMessage` and `language` (for example `hi-IN`). Leave the voice out to get the language's own voice. Show the user the agent's name and first line before creating it.
2. **"Call Rahul with my Sales agent."** Find the agent with `list_agents`, confirm the number and agent with the user, then `start_call`. Afterwards use `get_call` and `get_transcript` to report how it went.
3. **"How did yesterday's calls go?"** Use `list_calls` (and `get_analytics` for totals), then summarise: how many, how many answered, what people asked for, who needs a follow-up.
4. **"Test my agent before it calls customers."** `start_agent_test_run`, then `get_agent_test_run` for the result.
5. **Bookings.** `get_availability` for free times, then `book_appointment`, `reschedule_appointment` or `cancel_appointment` after the user agrees. The customer is told by Movoice.

## When something fails

Read the tool's error message and tell the user what it means in plain words. Common ones: the API add-on is not on the plan (the owner adds it in Movoice Billing), the account's identity check is not done yet (needed before calls), a permission is missing on the key (the owner ticks it on Movoice › Developer), or India's calling rules blocked the number.

Docs: https://docs.movoice.ai · Account and keys: https://app.movoice.ai/admin/developer
