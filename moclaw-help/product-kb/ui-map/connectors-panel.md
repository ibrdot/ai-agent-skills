---
id: moclaw.ui.connectors_panel
title: Connectors Panel
type: ui_map
product_area: connectors
audience: user
status: verified
owner: product
last_reviewed_at: 2026-07-29
source_paths:
  - maxgent/client/webapp/src/components/workspace/panel.tsx
  - maxgent/client/webapp/src/components/connectors/connectors-tab.tsx
  - maxgent/client/webapp/src/components/connectors/connectors-tab-view.tsx
  - maxgent/client/webapp/src/components/connectors/connectors-section.tsx
  - maxgent/client/webapp/src/components/connectors/connectors-section-view.tsx
  - maxgent/client/webapp/src/components/connectors/connector-settings-modal.tsx
  - maxgent/client/webapp/src/components/connectors/mcp-connector.tsx
  - maxgent/client/webapp/src/lib/connector-registry.ts
  - maxgent/client/webapp/src/lib/connector-visibility.ts
  - maxgent/client/webapp/src/stores/connector-store.ts
  - maxgent/client/webapp/src/i18n/locales/en.json
  - maxgent/client/webapp/src/i18n/locales/zh.json
  - maxgent/client/webapp/src/components/connectors/README.md
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Connectors Panel

## Direct Answer

The **Connectors** panel is a left-sidebar section inside `/chat`. It shows
third-party data/tool integrations such as **Google Workspace**, **GitHub**,
and **Linear** when they are visible for the current account and environment.
MCP server management should only be described when a current verified UI shows
an **MCP** row.

It is separate from **Channels**. Channels are chat entry points such as
Telegram, Slack, Lark, and Discord; Connectors are service access and tool
authorization.

## Where It Appears

1. Open `/chat`.
2. Open the left sidebar.
3. Expand **Connectors**.

In the current left sidebar order, **Connectors** appears after **Channels**
and before **Artifacts**. **Computers** is the separate first product-navigation
entry for AI Cloud Computer status and viewing.

## Current Connector Rows

| Connector | Current UI Behavior |
|---|---|
| **Google Workspace** | Dedicated Google status. Can show connected email, expired state, or Drive folder setup needed. This is the visible row for Gmail, Calendar, Tasks, Drive, Docs, Sheets, and Slides. |
| **GitHub** | Remote connector row. Settings opens GitHub identity and GitHub App installation/account management. |
| **Linear** | Remote connector row when backend metadata makes it visible or the account is connected. |
| **MCP** | Only describe this row if it is visible in the current account UI or a newer verified source confirms it; older docs describe a **Manage** dialog for remote MCP servers. |

## Row States And Actions

| State | User Sees |
|---|---|
| Not connected | Connector name, muted status dot, and **Connect** or connector-specific action. |
| Connecting/loading | Spinner/action disabled. |
| Connected | Status dot and a three-dot menu. |
| Expired | Warning status and reconnect-related action when available. |
| Needs setup | Google Workspace can show a folder setup warning after OAuth is connected. |

For connected OAuth connector rows, the three-dot menu can include **Settings**,
provider-specific actions, and **Disconnect**. Settings opens a modal with the
connector title, account/status details, website/privacy/manage links, and any
provider-specific account list.

Disconnect failures can produce two different meanings: MoClaw may fail to
reach the provider and ask the user to retry, or MoClaw may disconnect locally
while remote revoke is unconfirmed and ask the user to review provider access
settings.

## GitHub Settings Modal

GitHub has a provider-specific settings panel because GitHub identity,
installation, account/organization, and repository access are separate layers.

The modal can show:

- the connected GitHub identity subtitle;
- **Accessible accounts and organizations** / enabled installations;
- **Pending accounts and organizations** / installed but not enabled entries;
- repository selection labels such as all repositories or selected
  repositories;
- **Install GitHub App** / add organization action;
- per-account **Manage scope**, **Configure in GitHub**, **Enable**, and
  **Disconnect...** actions.

Disconnecting an organization-level local binding does not necessarily uninstall
the GitHub App remotely. The UI can show a reminder to open GitHub and complete
remote uninstall or repository-scope changes there.

## MCP Manage Dialog

If MCP is visible in a verified current UI, the row uses **Manage**. The dialog
can list configured servers, show server status, add a server, edit, test, sync
tools, enable/disable, or delete.

The current UI is for remote HTTPS Streamable HTTP MCP servers. Do not describe
it as a generic local command-line MCP config importer.

## Visibility Rules

- Google Workspace has a dedicated row/state path.
- Gmail is not a separate visible connector row in the current left sidebar.
- Remote connectors depend on backend connector metadata and account state.
- A remote connector may still appear when already connected, even if it would
  otherwise be hidden.
- Local/mock adapter behavior is not proof that a row is available in
  production.
- Do not promise every connector row is visible for every user.

## Do Not Say

- Do not say Connectors and Channels are the same thing.
- Do not say connecting GitHub identity automatically grants access to every
  organization or repository.
- Do not say disconnecting a GitHub organization row always uninstalls the
  GitHub App remotely.
- Do not say MCP accepts every local MCP server config; current UI is for remote
  HTTPS Streamable HTTP MCP servers.
- Do not describe the Connectors panel as a public marketplace of all possible
  integrations.

## Related Cards

- `moclaw.concepts.connectors_channels_skills`
- `moclaw.reference.connectors_status`
- `moclaw.how_to.connect_github`
- `moclaw.how_to.connect_google_workspace`
- `moclaw.how_to.connect_linear`
- `moclaw.how_to.manage_mcp_servers`
- `moclaw.ui.workspace_sidebar`
