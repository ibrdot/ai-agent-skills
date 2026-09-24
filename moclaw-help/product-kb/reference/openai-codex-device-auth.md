---
id: moclaw.reference.openai_codex_device_auth
title: OpenAI Codex Device Auth
type: reference
product_area: billing
audience: support
status: verified
last_reviewed_at: 2026-08-06
applies_to:
  plans: [pro]
  environments: [test, prod]
  platforms: [web]
---

# OpenAI Codex Device Auth

## Direct Answer

**Connect Codex** in **Settings > API Keys** is an OpenAI Codex / ChatGPT
device-auth connection, not a normal pasted OpenAI API key. When available, the
user starts the Codex connection, opens the ChatGPT verification page, enters
the displayed device code there, and waits for MoClaw to show the connection as
complete.

## What It Is

- The Settings API Keys area supports an OpenAI Codex OAuth identity.
- OpenAI Codex is shown as **OpenAI Codex (ChatGPT)** and uses `oauth`, not an
  API-key text field.
- The Codex connection is displayed as **Connect Codex**, **Connected with
  ChatGPT**, or an OAuth identity row with an email or account ID.
- The device-auth dialog title is **Connect OpenAI Codex** and the copy says to
  use ChatGPT device authentication to connect Codex.
- The verification URL should be described as the URL shown by MoClaw. The
  backend currently uses the OpenAI Codex device verification URL; the UI may
  also have a ChatGPT device-auth fallback.
- The feature is marked experimental in the UI, so normal support answers
  should say "when available" and point users to the current Settings page.

## Device Auth Flow

1. The user opens **Settings > API Keys**.
2. The user chooses **Add API Key** and selects **OpenAI Codex (ChatGPT)**, or
   uses the reconnect action on an existing Codex row.
3. MoClaw starts a device-auth session and receives a device handle, user code,
   verification URL, polling interval, and expiry.
4. The dialog opens the verification URL shown by MoClaw and shows the device
   code.
5. The user enters the device code on the ChatGPT/OpenAI page, not in a support
   chat.
6. MoClaw polls until the server returns pending, complete, expired, or error.
7. On complete, MoClaw stores an enabled OAuth identity, refreshes the key list
   and credits state, and syncs active runtime sessions.

## States And Recovery

| State | Support Meaning |
|---|---|
| Starting | MoClaw is requesting a device code. |
| Pending / polling | The user has not finished authorization yet, or the provider has not finalized the auth session. |
| Complete | MoClaw stored an enabled Codex OAuth identity. |
| Expired | The code expired; ask the user to retry from **Settings > API Keys**. |
| Error | Auth could not complete; ask the user to retry and collect safe visible error/time details if it repeats. |
| Forbidden / invalid handle | The device-auth handle does not belong to this user or is invalid; ask the user to restart the flow from **Settings > API Keys**. |
| Refresh needed / revoked | The stored Codex token may need reconnecting. |

Closing the dialog cancels the local polling loop. Retrying starts a new device
auth session and code.

## Security Boundaries

- Do not ask users to paste provider API keys, OAuth tokens, refresh tokens,
  ChatGPT passwords, cookies, authorization codes, or device codes into support.
- Do not ask users to paste the device-auth handle. Treat it as an internal
  signed polling handle, not a support diagnostic.
- The device code is meant to be entered on the ChatGPT/OpenAI verification
  page shown by the product flow. The device-auth handle is signed, user-bound,
  and time-limited, and should not be collected in support.
- Do not tell users to paste a normal OpenAI API key for the Codex option.
- Do not claim the connection changes the user's MoClaw account login identity.
- Do not claim every account or environment can use Codex; check whether the row
  is visible in the current UI.

## Do Not Say

- Do not say **Connect Codex** is the same as adding an OpenAI API key.
- Do not say ChatGPT password or OAuth tokens should be sent to MoClaw support.
- Do not say every OpenAI or ChatGPT model is automatically available.

## Related Cards

- `moclaw.reference.model_tiers`
- `moclaw.troubleshooting.model_tier_unavailable_or_switch_failed`
- `moclaw.concepts.credits_entitlement`
