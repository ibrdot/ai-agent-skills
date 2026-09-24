---
id: help.channels.agent_email_and_phone
title: Agent Email And Phone
audience: user
status: verified
source_cards:
  - moclaw.reference.agent_email_and_phone
  - moclaw.reference.google_workspace_scopes
  - moclaw.reference.connectors_status
  - moclaw.playbooks.feature_not_shipped_yet
last_reviewed_at: 2026-06-09
---

# Agent Email And Phone

MoClaw account email, connected Gmail, chat channels, and an agent-owned mailbox
or phone number are different things.

## What To Use For Email

If you want MoClaw to work with your Gmail, connect **Google Workspace**. That is
the current user-facing path for Gmail-style tasks such as reading, drafting, or
sending mail from your connected Google account.

An agent-owned MoClaw mailbox or phone/SMS number is not confirmed as generally
available for every account. If MoClaw gives you an address or number during a
specific task, use the exact visible instructions from that task.

## What To Check

- For Gmail: open **left sidebar > Connectors** and check **Google Workspace**.
- For external chat channels: open **left sidebar > Channels**.
- For account email or identity changes: use the account/data request path.

## Safety Notes

- Do not send passwords, 2FA codes, OAuth tokens, API keys, payment details, or
  other secrets through chat, email, or SMS.
- Do not assume a MoClaw agent phone number exists unless the current product
  flow shows one.
- Email or SMS delivery can fail because a connector is missing, a provider is
  unavailable, a number is not provisioned, or availability is not enabled for
  your account/environment.

## Related Articles

- `connectors/connect-google-workspace.md`
- `connectors/google-workspace-permissions.md`
- `channels/chat-channels.md`
- `account/account-and-data-requests.md`
