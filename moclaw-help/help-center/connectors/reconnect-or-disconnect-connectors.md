---
id: help.connectors.reconnect_disconnect
title: Reconnect Or Disconnect A Connector
audience: user
status: verified
source_cards:
  - moclaw.troubleshooting.connector_expired
  - moclaw.ui.connectors_panel
  - moclaw.reference.connectors_status
  - moclaw.troubleshooting.google_workspace_needs_folder
  - moclaw.troubleshooting.github_repo_not_visible
last_reviewed_at: 2026-06-09
---

# Reconnect Or Disconnect A Connector

Use this when a connected service shows **Expired**, stops working, or you want
to remove a connector.

## Reconnect A Connector

1. Open `/chat`.
2. Open the left sidebar.
3. Expand **Connectors**.
4. Find the affected service.
5. If the row shows **Reconnect**, click it.
6. If it only shows **Connect**, connect it again.
7. Finish the provider authorization page.
8. Return to MoClaw and refresh **left sidebar > Connectors**.

Do not send OAuth tokens, authorization codes, passwords, API keys, or provider
secrets to support.

## Connector-Specific Notes

- **Google Workspace** is the row for Gmail, Calendar, Tasks, Drive, Docs,
  Sheets, and Slides. Do not look for a separate Gmail row. If OAuth succeeds
  but Drive still says **Drive setup needed**, finish the Workspace Folder step.
- **GitHub** has a connected identity plus GitHub App account/organization
  access. A repository can still be missing after reconnect if the App is not
  installed, not enabled, or limited to selected repositories.
- **Linear** reconnect restores the authorized Linear user/workspace. It does
  not guarantee every Linear workspace, team, project, issue, or archived item
  is visible.
- If **MCP** is visible, it uses **Manage** for remote MCP servers. It is not a
  normal OAuth row with a **Disconnect** action.

## After Reconnecting

- For Google Workspace, check whether **Drive setup needed** is still shown.
- For GitHub, open GitHub settings and check the connected identity, accessible
  accounts or organizations, and repository scope.
- For Linear, confirm you authorized the right Linear workspace.

## Disconnect A Connector

Open the connector's three-dot menu and choose **Disconnect** when available.

If MoClaw says it could not reach the provider to revoke access, retry later.
If it says the connector was disconnected locally but remote access could not be
confirmed, open the provider's own access settings and confirm whether the app
is still installed or authorized.

Some provider revoke failures are retried. If the provider/network still cannot
be reached, disconnect can fail and should be retried. If the provider token was
already invalid, MoClaw may complete local disconnect and ask you to confirm
remote access in the provider settings.

For GitHub organizations, removing the local connection in MoClaw may not
uninstall the GitHub App in GitHub. If MoClaw shows a reminder or GitHub still
shows access, open GitHub's app settings to uninstall the app or adjust
repository access.

For Google Workspace, use the provider access/settings link if Google still
shows MoClaw access after the local row is gone.

## Contact Support

Send:

- account email;
- connector name;
- visible status text;
- whether you were connecting, reconnecting, or disconnecting;
- provider account, workspace, or organization name;
- approximate time and timezone;
- screenshot of the connector row or settings modal with secrets redacted.

Do not send provider passwords, OAuth tokens, authorization codes, API keys, or
secret URLs. Do not send raw Google, GitHub, or Linear access tokens.

## Related Articles

- `connectors/connectors-overview.md`
- `connectors/connect-github.md`
- `connectors/connect-google-workspace.md`
- `connectors/connect-linear.md`
- `connectors/github-repository-access.md`
- `connectors/google-workspace-permissions.md`
