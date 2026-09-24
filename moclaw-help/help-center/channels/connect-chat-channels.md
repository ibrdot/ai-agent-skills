---
id: help.channels.connect_chat_channels
title: Connect Chat Channels
audience: user
status: verified
source_cards:
  - moclaw.reference.chat_channel_binding_flows
  - moclaw.concepts.connectors_channels_skills
  - moclaw.reference.connectors_status
  - moclaw.playbooks.ask_for_screenshot_or_reference_id
last_reviewed_at: 2026-06-09
---

# Connect Chat Channels

Open **left sidebar > Channels** in `/chat`, then use the row for the channel you
want to connect. Available rows can vary by account and environment.

## Telegram

Click **Connect** on the Telegram row. MoClaw can show a QR code and an **Open
in Telegram** action.

Use your phone camera to scan the QR code if the hint says so, then finish the
bot-side connection and wait for the row to change to connected.

## Slack

Click **Connect** on the Slack row and finish Slack authorization. After the
provider flow returns to MoClaw, check **left sidebar > Channels** again for the
connected state.

## Lark Or Discord

Click **Connect** on the row if it is visible. MoClaw can show a bot link and a
short bind code. Send the bind code to the bot as instructed by the product
flow, then wait for the row to become connected.

Do not send the bind code to support. It is for the bot binding flow.

## Disconnect A Channel

When a channel is connected, open the row's three-dot menu and choose the
disconnect action. You can reconnect later if the channel is still available.

## If A Channel Is Missing Or Stuck

- If the row is missing, it may not be enabled for your account or environment.
- If the row stays on **Waiting for connection**, cancel and retry the connect
  flow. Telegram, Lark, and Discord bind tokens are time-limited, so use the
  current dialog's code/link instead of an older one.
- For Telegram, try the **Open in Telegram** action if scanning does not work.
- For Lark or Discord, make sure you sent the current bind code to the bot.
- For Slack, make sure you completed the Slack authorization flow.

If it still fails, contact support with your account email, channel name,
approximate time, visible row state, and a screenshot of **left sidebar >
Channels**.

Do not send provider passwords, OAuth tokens, API keys, verification codes, or
private workspace messages.

## Channels vs Connectors

Channels are where you chat with MoClaw. Connectors are separate permissions for
services such as Google Workspace, GitHub, Linear, or MCP. Connecting a chat
channel does not automatically give MoClaw access to all data in that service.

## Related Articles

- `channels/chat-channels.md`
- `connectors/connectors-overview.md`
- `troubleshooting/contact-support-and-send-diagnostics.md`
