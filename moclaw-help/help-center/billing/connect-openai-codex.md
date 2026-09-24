---
id: help.billing.connect_openai_codex
title: Connect OpenAI Codex
audience: user
status: verified
source_cards:
  - moclaw.reference.openai_codex_device_auth
  - moclaw.reference.model_tiers
  - moclaw.troubleshooting.model_tier_unavailable_or_switch_failed
last_reviewed_at: 2026-08-06
---

# Connect OpenAI Codex

When available, **Connect Codex** lets MoClaw use an OpenAI Codex / ChatGPT
device-auth connection. This is different from pasting a normal provider API
key.

## Connect Codex

1. Open **Settings**.
2. Go to **API Keys**.
3. Click **Add API Key**.
4. Choose **OpenAI Codex (ChatGPT)** if it is visible.
5. Continue to **Connect Codex**.
6. Open the verification page shown by MoClaw.
7. Enter the displayed device code on that verification page.
8. Return to MoClaw and wait for the connection to complete.

Do not send your ChatGPT password, provider API key, OAuth token, cookies,
device auth handle, or device code to support.

## How It Differs From API Keys

- Anthropic, OpenRouter, and DeepSeek use an API-key field.
- OpenAI Codex uses ChatGPT device authentication instead.
- A connected Codex row may show as **Connected with ChatGPT**, or show the
  email/account from the connected identity.
- **Connected with ChatGPT** does not change your MoClaw account login identity.

## If The Code Expires Or Fails

Retry from **Settings > API Keys**. A retry creates a new device-auth session
and a new device code. Use the latest code shown by MoClaw.

Closing the dialog stops MoClaw's local polling. If the connection did not
complete, reopen **Settings > API Keys** and retry.

If it keeps failing, contact support with the visible error, approximate time
and timezone, and whether the Codex row is visible in **Settings > API Keys**.
Do not include passwords, API keys, OAuth tokens, refresh tokens, cookies,
authorization codes, device auth handles, or device codes.

## Related Articles

- `chat/model-tiers.md`
- `chat/model-tier-locked-or-switch-failed.md`
