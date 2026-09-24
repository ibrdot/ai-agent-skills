---
id: moclaw.reference.connectors_status
title: Connectors And Channels Status
type: reference
product_area: connectors
audience: support
status: verified
owner: product
last_reviewed_at: 2026-06-09
source_paths:
  - maxgent/client/webapp/src/components/connectors/connectors-section.tsx
  - maxgent/client/webapp/src/components/channels/channel-rows.tsx
  - maxgent/client/webapp/src/components/channels/telegram-row.tsx
  - maxgent/client/webapp/src/components/channels/slack-row.tsx
  - maxgent/client/webapp/src/components/channels/lark-row.tsx
  - maxgent/client/webapp/src/components/channels/discord-row.tsx
  - maxgent/client/webapp/src/lib/connector-registry.ts
  - maxgent/client/webapp/src/lib/connector-visibility.ts
  - maxgent/client/webapp/src/stores/connector-store.ts
  - maxgent/client/webapp/src/lib/config.ts
  - maxgent/client/webapp/src/i18n/locales/en.json
  - maxgent/server/app-server/app/domains/connector/README.md
  - maxgent/server/app-server/app/domains/connector/services/registry.py
  - maxgent/client/webapp/src/components/connectors/README.md
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Connectors And Channels Status

## Direct Answer

MoClaw's current frontend connector registry includes **Google Workspace**,
**GitHub**, and **Linear**. Channels are a separate surface: **Telegram**,
**Slack**, **Lark**, and **Discord**.

Whether a user sees a row can still depend on environment, account connection
state, and connector metadata returned by the backend. Support answers must
first separate connector rows, channel rows, provider-side access, and
skills/commands.

## Current Surface Matrix

| Surface | User-facing row | Current rule | Support wording |
|---|---|---|---|
| Google Workspace | **Google Workspace** | Dedicated row/status path, not fetched from the remote connector list. | Use this one row for Gmail, Calendar, Tasks, Drive, Docs, Sheets, and Slides. |
| GitHub | **GitHub** when visible | Remote connector. Current backend/account visibility can limit who sees the row; local/mock catalog behavior is not proof of production availability. | Explain identity, GitHub App installation, account/org enablement, and repository scope separately. |
| Linear | **Linear** | Remote connector. Shows when backend marks it visible/connected. | Ask for workspace/team/project/issue details and visible row state when access fails. |
| MCP | Only if a current verified UI shows an **MCP** row | Older MCP docs describe a remote MCP management dialog, but the current frontend connector registry checked on 2026-06-15 does not include an MCP row. | Do not promise **left sidebar > Connectors > MCP** unless the user can actually see it or a newer verified source confirms it. |
| Telegram | **Telegram** | Channel row rendered from `CHANNEL_REGISTRY`. | Chat entry point only; not data access to Telegram workspace data. |
| Slack | **Slack** | Channel row rendered from `CHANNEL_REGISTRY`. | Chat entry point only; not a Slack data connector. |
| Lark | **Lark** | Channel row is hidden in the current production environment. | If the row is absent in production, do not promise public availability. |
| Discord | **Discord** | Channel row rendered by the current visibility rule. | Chat entry point; actual binding still depends on account/provider setup. |
| Notion | No current row | Backend registry keeps Notion commented out. | Treat as not currently user-facing unless a newer verified source says otherwise. |

## Visibility And State Rules

- Remote connector state starts as hidden. `/api/connector/list_connectors`
  marks a remote connector `visible: true` when the backend returns it.
- A remote connector can still show if already connected, even if it would not
  otherwise be visible.
- In non-production environments, catalog behavior can differ from production;
  do not use local/mock connector rows as proof of production availability.
- Google Workspace uses `/auth/google-workspace/status` and its own folder
  setup state instead of the generic remote connector list.
- The visible OAuth connector state labels include **Connect**, **Connecting**,
  **Connected**, **Expired**, **Settings**, and **Disconnect**. If MCP is
  visible, older MCP materials describe **Manage** plus server statuses such as
  **Active**, **Disabled**, **Draft**, **Error**, and **Testing**.

## Answering Rule

When user asks "Can I connect X?", answer in this order:

1. If X appears in current account UI, tell them the exact UI entry.
2. If X is a Google service, explain it through **Google Workspace** unless a
   newer verified UI shows a separate row.
3. If X is a chat channel, keep it separate from data connector access.
4. If X is hidden or missing, say availability may depend on account,
   environment, connector metadata, or provider setup.
5. If X is only in roadmap/seed docs, say it is not something to rely on yet.

## Status And Visibility Notes

- The current frontend connector registry checked on 2026-06-15 includes
  **Google Workspace**, **GitHub**, and **Linear**. GitHub still depends on
  backend/account visibility. MCP materials should be treated as conditional
  until a current UI confirms the row.
- Gmail, Calendar, Tasks, Drive, Docs, Sheets, and Slides are explained through
  the **Google Workspace** row. Do not invent a separate user-facing Gmail row.
- If MCP is visible in a verified current UI, it uses a **Manage** dialog for
  server records, not a standard OAuth reconnect/disconnect row.
- Remote connector rows can be hidden until backend metadata is returned or the
  account is connected. Do not use a missing row as proof that the service will
  never be available.
- Channel rows are not equivalent to connector rows. Telegram, Slack, Lark, and
  Discord are chat entry points; they do not automatically grant MoClaw data
  access to those services.

## Do Not Say

- Do not say all listed services are available for every user.
- Do not confuse channel binding with data connector authorization.
- Do not infer third-party data access from a chat-channel connection.
- Do not tell users to connect Gmail from a separate connector row unless the
  current UI is re-verified.
- Do not describe Notion as a current connector row from the old seed list.
- Do not promise an MCP row from old docs alone, and do not describe MCP as a
  local command-line config importer.

## Related Cards

- `moclaw.concepts.connectors_channels_skills`
- `moclaw.reference.chat_channel_binding_flows`
- `moclaw.ui.connectors_panel`
- `moclaw.ui.workspace_sidebar`
