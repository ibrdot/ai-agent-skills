---
id: help.connectors.overview
title: Connectors And Channels
audience: user
status: verified
source_cards:
  - moclaw.concepts.connectors_channels_skills
  - moclaw.reference.connectors_status
  - moclaw.ui.connectors_panel
  - moclaw.troubleshooting.connector_expired
  - moclaw.reference.connector_cli_local_login
  - moclaw.ui.workspace_sidebar
last_reviewed_at: 2026-06-08
---

# Connectors And Channels

MoClaw uses **Connectors** for service access and **Channels** for chat entry
points.

- **Connectors** include **Google Workspace**, **GitHub**, **Linear**, and
  **MCP** when they are visible for your account and environment.
- **Channels** include **Telegram**, **Slack**, **Lark**, and **Discord** when
  they are visible for your account and environment.

Connecting a channel does not automatically give MoClaw access to that service's
data. Connecting a service also may not be enough by itself; some services need
extra folder, repository, organization, workspace, or server setup.

## Current Rows

| Row | Where it appears | What to know |
|---|---|---|
| **Google Workspace** | **left sidebar > Connectors** | This is the row for Gmail, Calendar, Tasks, Drive, Docs, Sheets, and Slides. Do not look for a separate Gmail row. |
| **GitHub** | **left sidebar > Connectors** | GitHub has identity, GitHub App installation, account/organization, and repository-scope layers. |
| **Linear** | **left sidebar > Connectors** | Access can depend on the connected Linear workspace and the exact team/project/issue IDs. |
| **MCP** | **left sidebar > Connectors** | Use **Manage** to add, test, sync, enable, disable, edit, or delete remote MCP servers. |
| **Telegram / Slack / Lark / Discord** | **left sidebar > Channels** | These are chat entry points, not data connectors. |

## Where To Manage Connectors

1. Open `/chat`.
2. Open the left sidebar.
3. Expand **Connectors**.
4. Pick the service you want to connect.
5. Follow the authorization or setup flow.

Some connector setup may open a provider page, such as GitHub or Google. Finish
the provider-side steps before returning to MoClaw.

`connector-cli local login` is a separate local development flow. It is not the
normal connector management page and is not available in production.

Google Workspace is the visible row for Gmail, Calendar, Tasks, Drive, Docs,
Sheets, and Slides. Do not expect a separate Gmail connector row in the current
left sidebar.

## What The Rows Mean

- If a row is not connected, use **Connect** or the row's action button.
- If a row is connected, open the three-dot menu for **Settings** or
  **Disconnect**.
- If a row is expired, reconnect it before asking MoClaw to use it.
- If Google Workspace says folder setup is needed, finish the Drive workspace
  folder step.
- If MCP shows **Manage**, use that dialog to add, test, sync, enable, disable,
  edit, or delete remote MCP servers.
- If disconnect reports that remote provider access could not be confirmed,
  review the provider's own access settings.

## GitHub Has Two Layers

GitHub connection has a user identity layer and a GitHub App installation or
account/organization layer. A repository may still be missing if the GitHub App
is not installed for the right account or if repository access is limited to
selected repositories.

Disconnecting a GitHub organization inside MoClaw may only remove the local
binding. Use GitHub's own settings to uninstall the GitHub App or change
repository access remotely.

## If A Connector Is Missing

If you do not see a connector, it may not be available for your current account
or environment, or backend connector metadata may not have returned it for your
account yet. Ask support with the connector name, account email, plan, and a
screenshot of the **left sidebar > Connectors** section.

## Important Distinction

Connecting your identity is not always enough. Some services also need
workspace, folder, repository, or organization-level access.

## Related Articles

- `connectors/connect-github.md`
- `connectors/connector-cli-local-login.md`
- `connectors/reconnect-or-disconnect-connectors.md`
- `troubleshooting/common-errors.md`
