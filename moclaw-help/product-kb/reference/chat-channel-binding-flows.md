---
id: moclaw.reference.chat_channel_binding_flows
title: Chat Channel Binding Flows
type: reference
product_area: channels
audience: support
status: verified
owner: product
last_reviewed_at: 2026-06-09
source_paths:
  - maxgent/client/webapp/src/components/channels/channel-rows.tsx
  - maxgent/client/webapp/src/components/channels/telegram-row.tsx
  - maxgent/client/webapp/src/components/channels/telegram-row-view.tsx
  - maxgent/client/webapp/src/components/channels/slack-row.tsx
  - maxgent/client/webapp/src/components/channels/slack-row-view.tsx
  - maxgent/client/webapp/src/components/channels/lark-row.tsx
  - maxgent/client/webapp/src/components/channels/lark-row-view.tsx
  - maxgent/client/webapp/src/components/channels/discord-row.tsx
  - maxgent/client/webapp/src/components/channels/discord-row-view.tsx
  - maxgent/client/webapp/src/components/channels/channel-bind-dialog.tsx
  - maxgent/client/webapp/src/lib/connector-registry.ts
  - maxgent/client/webapp/src/lib/connector-visibility.ts
  - maxgent/client/webapp/src/stores/connector-store.ts
  - maxgent/client/webapp/src/i18n/locales/en.json
  - maxgent/client/webapp/src/i18n/locales/zh.json
  - maxgent/server/app-server/app/routers/im.py
  - maxgent/server/app-server/app/schemas/im.py
  - maxgent/server/app-server/app/services/im_server_client.py
  - maxgent/server/app-server/app/routers/slack.py
  - maxgent/server/app-server/app/services/slack.py
  - maxgent/server/app-server/app/schemas/slack.py
  - product-kb/reference/connectors-status.md
  - product-kb/concepts/connectors-channels-skills.md
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web, telegram, slack, lark, discord]
---

# Chat Channel Binding Flows

## Direct Answer

MoClaw chat channels are managed from **left sidebar > Channels**. Current product
sources include Telegram, Slack, Lark, and Discord rows, but availability can
depend on account, environment, chat-provider configuration, and provider setup.

The channel bind flows are not identical:

| Channel | Current Flow | Notes |
|---|---|---|
| Telegram | Click **Connect**, scan the QR code or open the Telegram link, then wait for the row to become connected. | The frontend accepts only `t.me` or `telegram.me` connect URLs. UI copy says to scan with the phone camera, not Telegram's scanner. |
| Slack | Click **Connect** and complete Slack OAuth. | Backend requests Slack bot scopes for DM messaging and redirects back to `/chat` with success/error query params. |
| Lark | Click **Connect**, copy/paste or send the displayed bind token through the Lark bot flow, and wait for connection. | The row is hidden in the current production environment. Connect URLs are limited to known Lark/Feishu applink domains. |
| Discord | Click **Connect**, copy/paste or send the displayed bind token through the Discord bot flow, and wait for connection. | Current reviewed UI can show Discord, but support should still confirm account/environment and provider setup. Connect URLs are limited to known Discord domains. |

For Telegram, Lark, and Discord, the frontend polls for bind completion every 3
seconds for up to 5 minutes. Closing/canceling the bind dialog stops polling
and clears temporary connect URLs/tokens from UI state.

The IM bind token TTL is also 5 minutes. If the user misses that window or the
row remains on **Waiting for connection**, they should cancel and start a fresh
connect flow so the bot receives the current token.

## Connected And Disconnect States

When connected, rows show connected status and a three-dot menu with a
disconnect action. Disconnecting removes the MoClaw channel binding so that
channel can be reconnected later. It does not automatically mean MoClaw has
full access to that third-party workspace's data.

Slack disconnect calls the Slack revoke path and removes the IM binding when one
exists. Telegram, Lark, and Discord disconnect through the IM binding delete
path.

## Channels Are Not Connectors

A channel lets the user talk to MoClaw from another app. A connector authorizes
MoClaw to access a third-party service or data source. Do not tell users that
connecting a Slack channel grants MoClaw access to every Slack message or
workspace resource.

## Troubleshooting Guidance

If a user cannot bind a channel:

1. Ask them to open **left sidebar > Channels** and confirm whether the channel row
   is visible.
2. If the row is missing, explain that the channel may be account/environment
   gated.
3. If the row is stuck on **Waiting for connection**, ask them to retry the
   connect flow and complete the provider-side step within the current 5-minute
   dialog window.
4. For Telegram, ask them to use the phone camera or the **Open in Telegram**
   action if shown.
5. For Lark/Discord, ask them to send the bind code to the bot shown by the
   product flow. Do not ask them to send the bind code to support.
6. For Slack, ask them to finish the Slack OAuth authorization and return to
   `/chat`.
7. If it still fails, collect account email, channel name, approximate time,
   visible row state, and a screenshot with secrets redacted.

## Do Not Say

- Do not promise every user can use every channel.
- Do not say Lark is visible in production when the current product hides it in
  production.
- Do not say connecting a channel grants third-party data connector access.
- Do not ask for provider passwords, OAuth tokens, Slack codes, API keys, or
  verification codes.
- Do not ask users to paste channel bind tokens into support chat.
- Do not expose raw internal endpoint names, IM-server internals, or provider
  token details in normal customer-facing answers.

## Related Cards

- `moclaw.concepts.connectors_channels_skills`
- `moclaw.reference.connectors_status`
- `moclaw.ui.workspace_sidebar`
- `moclaw.playbooks.ask_for_screenshot_or_reference_id`
