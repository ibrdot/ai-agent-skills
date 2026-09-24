---
id: help.connectors.connect_google_workspace
title: Connect Google Workspace
audience: user
status: verified
source_cards:
  - moclaw.how_to.connect_google_workspace
  - moclaw.reference.google_workspace_scopes
  - moclaw.troubleshooting.google_workspace_needs_folder
  - moclaw.troubleshooting.connector_expired
  - moclaw.reference.connectors_status
  - moclaw.playbooks.ask_for_screenshot_or_reference_id
last_reviewed_at: 2026-06-09
---

# Connect Google Workspace

Use Google Workspace when you want MoClaw to work with Google services such as
Gmail, Calendar, Tasks, Drive, Docs, Sheets, or Slides when they are available
for your account.

Availability can depend on environment and account configuration. If you do not
see Google Workspace in **left sidebar > Connectors**, it may not be enabled for
your current account.

## Connect Google Workspace

1. Open `/chat`.
2. Open the left sidebar.
3. Expand **Connectors**.
4. Find **Google Workspace**.
5. Click **Connect**.
6. Complete the Google authorization flow.
7. Return to MoClaw and check the connector row status.

## Finish Drive Setup

Google Workspace can connect successfully while Drive files still need one more
step. If the connector says **Drive setup needed**, choose or create a Workspace
Folder in Google Drive.

That folder is the Drive area MoClaw can use for Drive, Docs, Sheets, and
Slides work. MoClaw should not be described as having access to your whole
Google Drive.

You may see these menu actions:

| Action | Meaning |
|---|---|
| **Select Existing Folder** | Pick an existing Drive folder for MoClaw to use. |
| **Create New Folder** | Create or reuse a `MoClaw Agent Space` folder. |

These folder actions are mainly visible when Google Workspace is connected but
Drive setup is still needed. If your connector is already ready and you need a
different folder, use the currently visible connector actions, reconnect, or
contact support with the connector row state.

If the folder picker is blocked by the browser, MoClaw may fall back to creating
or reusing `MoClaw Agent Space` so setup can still finish.

Files outside the Workspace Folder are not part of the normal Drive working
area. Move, copy, or select files into that folder if you want MoClaw to use
them.

## If It Stops Working

Open **left sidebar > Connectors**, find Google Workspace, and use **Reconnect** if
shown. After reconnecting, check whether Drive setup is still complete.

If Gmail, Calendar, or Tasks still work but Drive, Docs, Sheets, or Slides do
not, check the Workspace Folder setup before treating the whole connector as
broken. The connector can show **Ready now: Gmail, Calendar, Tasks** while
**Drive setup needed** still applies to Drive, Docs, Sheets, and Slides.

## What To Send Support

- Account email.
- Screenshot of the Google Workspace connector row.
- Whether Gmail/Calendar work but Drive/Docs/Sheets/Slides do not.
- Whether you selected or created the Workspace Folder.
- Approximate time if authorization or folder selection failed.

Do not send Google OAuth codes, access tokens, refresh tokens, cookies,
passwords, signed URLs, or raw email/file contents.

## Related Articles

- `connectors/connectors-overview.md`
- `connectors/reconnect-or-disconnect-connectors.md`
- `connectors/google-workspace-permissions.md`
- `troubleshooting/common-errors.md`
