---
id: moclaw.how_to.connect_google_workspace
title: Connect Google Workspace
type: how_to
product_area: connectors
audience: user
status: verified
owner: product
last_reviewed_at: 2026-06-09
source_paths:
  - maxgent/client/webapp/src/components/connectors/connectors-section.tsx
  - maxgent/client/webapp/src/i18n/locales/en.json
  - maxgent/client/webapp/src/lib/connector-registry.ts
  - maxgent/client/webapp/src/stores/connector-store.ts
  - maxgent/client/webapp/src/lib/google-picker.ts
  - maxgent/client/webapp/src/lib/google-drive.ts
  - maxgent/server/app-server/app/services/google_workspace.py
  - maxgent/docs/google-workspace-scopes.md
applies_to:
  plans: [free, trial, pro]
  environments: [test, prod]
  platforms: [web]
---

# Connect Google Workspace

## Direct Answer

Open the left sidebar, go to **Connectors**, find **Google Workspace**,
and click **Connect**. After OAuth, MoClaw may ask you to choose or create a
Workspace Folder in Google Drive before Drive, Docs, Sheets, and Slides are
fully ready.

Google Workspace setup has two practical layers:

1. Google OAuth connects the account for services such as Gmail, Calendar,
   Tasks, and Drive APIs.
2. Workspace Folder setup chooses the Drive folder MoClaw can use for Drive,
   Docs, Sheets, and Slides work.

OAuth can succeed while Drive still shows **Drive setup needed**.

## Before You Start

- Google Workspace covers Gmail, Calendar, Tasks, Drive, Docs, Sheets, and
  Slides in current UI copy.
- Gmail, Calendar, and Tasks can be ready before Drive files are fully set up.
- Drive file access is scoped to the selected Workspace Folder.
- MoClaw should not be described as having full Google Drive access.
- Do not ask users to send Google OAuth codes, access tokens, refresh tokens,
  cookies, passwords, or raw email/file contents.

## Steps

1. Open `/chat`.
2. Open the left sidebar.
3. Expand **Connectors**.
4. Click **Connect** on Google Workspace.
5. Complete Google authorization.
6. If the connector says **Drive setup needed**, open the connector menu.
7. Choose **Select Existing Folder** or **Create New Folder**.
8. Confirm the connector shows ready status.

Current reviewed UI shows folder setup actions when Google Workspace is
connected and Drive setup is still needed. Do not promise a permanently visible
"change folder" action after the connector is already ready.

## Drive Folder Choices

| Choice | What Happens |
|---|---|
| **Select Existing Folder** | Opens Google Picker so the user can choose one Drive folder for MoClaw's Drive/Docs/Sheets/Slides work. |
| **Create New Folder** | Creates or reuses a Drive folder named `MoClaw Agent Space` and uses it as the Workspace Folder. |

When Google Picker is blocked by browser behavior such as strict third-party
cookie handling, the product can fall back to creating or reusing
`MoClaw Agent Space` so setup can still complete.

The selected folder and its current/future contents are the intended working
area for Drive, Docs, Sheets, and Slides. User-owned files outside that folder
should be moved, copied, or selected into the Workspace Folder before MoClaw can
use them.

## If You Cannot See It

- Google Workspace is a current connector when visible in **left sidebar >
  Connectors**. If the row is missing, collect the current UI/account context
  instead of treating it as unlaunched.
- If the connector is expired, reconnect Google Workspace.
- If Drive/Docs/Sheets/Slides do not work but Gmail/Calendar/Tasks do, check
  whether a Workspace Folder has been selected.
- If folder selection fails, check whether the folder is accessible to the
  connected Google account and is not in trash.
- If the browser blocks the Picker, use **Create New Folder** or retry the setup
  flow so the fallback can create/reuse `MoClaw Agent Space`.
- If a ready connector needs a different Workspace Folder and the menu does not
  show folder actions, use the currently visible connector actions, reconnect,
  or escalate with the connector row state.

## Do Not Say

- Do not say MoClaw can read all Google Drive files.
- Do not skip the folder-selection step when explaining Drive access.
- Do not say `drive.file` is the same as full `drive` scope.
- Do not say Gmail, Calendar, Tasks, Drive, Docs, Sheets, and Slides all share a
  single all-or-nothing readiness state.
- Do not promise a folder-switch menu action when the current ready connector UI
  does not show one.
- Do not ask users for Google OAuth codes, access tokens, refresh tokens,
  cookies, passwords, or full raw logs.

## Related Cards

- `moclaw.reference.connectors_status`
- `moclaw.troubleshooting.connector_expired`
- `moclaw.troubleshooting.google_workspace_needs_folder`
- `moclaw.reference.google_workspace_scopes`
- `moclaw.playbooks.security_privacy_answering`
