---
id: moclaw.reference.agent_email_and_phone
title: Agent Email And Phone Status
type: reference
product_area: communications
audience: support
status: verified
owner: product
last_reviewed_at: 2026-06-09
source_paths:
  - maxgent/server/app-server/app/domains/agent_runtime/services/agent_server_runtime.py
  - maxgent/server/app-server/app/domains/agent_runtime/tests/unit/test_agent_server_runtime.py
  - maxgent/libs/sandbox-mcp/src/tools/email.ts
  - maxgent/libs/sandbox-mcp/src/tools/phone.ts
  - maxgent/server/app-server/app/routers/internal.py
  - maxgent/server/app-server/app/domains/agent/routes/user.py
  - maxgent/server/app-server/app/domains/agent/services/email.py
  - maxgent/server/app-server/app/domains/agent/services/phone.py
  - maxgent/server/app-server/app/domains/agent/routes/email_webhook.py
  - maxgent/server/app-server/.env.example
  - product-kb/reference/google-workspace-scopes.md
  - product-kb/how-to/connect-google-workspace.md
  - product-kb/reference/connectors-status.md
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Agent Email And Phone Status

## Direct Answer

MoClaw has implementation support for an agent-owned mailbox and SMS phone
number, but current MoClaw runtime configuration hides the raw agent email/SMS
tools from the model. Support should not promise that every user can ask MoClaw
to directly receive/send email or SMS through an agent-owned address/number.

Distinguish:

- the user's MoClaw account email;
- connected Gmail/Google Workspace access;
- chat channels such as Telegram, Slack, Lark, or Discord;
- an agent-owned email address or phone/SMS number.

## Current Evidence

- Sandbox MCP contains email tools for agent mailbox address, inbox/sent/trash,
  read, compose, reply, forward, update, and delete.
- Sandbox MCP contains phone tools for agent phone number, send SMS, list SMS,
  and read SMS.
- Current MoClaw runtime adds those email and phone tool names to
  `tools.disabled`, with a code comment that MoClaw does not expose agent
  email/SMS to the model.
- App-server has authenticated agent email routes and sandbox-authenticated
  internal email routes.
- Agent email addresses are derived from agent name plus the configured agent
  email domain.
- Inbound email webhook requires `AGENT_EMAIL_WEBHOOK_SECRET`; when it is empty,
  the inbound webhook returns not configured.
- Phone provisioning is best-effort and only works when Twilio settings are
  configured. If the agent has no active number, the phone-number route returns
  "Agent has no phone number."

## Safe User Wording

Use wording like:

> MoClaw account email, connected Gmail, and an agent-owned mailbox are different
> things. I do not see agent email/SMS as a generally exposed model tool in the
> current MoClaw runtime. For your Gmail, connect Google Workspace. For chat
> outside the web app, check left sidebar > Channels.

If a user says MoClaw already showed an address or phone number in their current
task, answer from that visible context and avoid universal claims.

## Google Workspace Difference

If the user wants MoClaw to read, compose, or send mail from their Gmail, route
them to Google Workspace. Google Gmail access is connector-based and uses Google
OAuth scopes; it is not the same as an agent-owned MoClaw mailbox.

## SMS And Phone Safety

Do not treat SMS availability as universal. Agent phone numbers depend on Twilio
configuration and successful provisioning. SMS sending can fail because no active
number exists, provider setup is missing, or rate limits/provider errors apply.

Do not ask users to send passwords, 2FA codes, OAuth tokens, API keys, or
payment details through email/SMS.

## Do Not Say

- Do not promise every MoClaw user has an agent email address or phone number.
- Do not say the model can directly use agent email/SMS tools in current MoClaw
  runtime.
- Do not confuse the user's account email with agent mailbox address.
- Do not confuse Google Workspace/Gmail connector access with agent mailbox
  access.
- Do not expose raw internal endpoint paths or tool names in customer-facing
  answers.
- Do not say email delete is permanent; current email delete moves to trash.
- Do not ask users to share passwords, 2FA codes, OAuth tokens, API keys, or
  sensitive SMS/email content.

## Related Cards

- `moclaw.reference.google_workspace_scopes`
- `moclaw.how_to.connect_google_workspace`
- `moclaw.reference.connectors_status`
- `moclaw.concepts.connectors_channels_skills`
- `moclaw.playbooks.feature_not_shipped_yet`
