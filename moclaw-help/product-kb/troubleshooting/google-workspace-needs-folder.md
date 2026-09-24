---
id: moclaw.troubleshooting.google_workspace_needs_folder
title: Google Workspace Needs Folder
type: troubleshooting
product_area: connectors
audience: user
status: verified
owner: product
last_reviewed_at: 2026-06-09
source_paths:
  - maxgent/client/webapp/src/components/connectors/connectors-section.tsx
  - maxgent/client/webapp/src/i18n/locales/en.json
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

# Google Workspace Needs Folder

## Symptom

The Google Workspace connector says **Drive setup needed**, or Gmail/Calendar
work but Drive, Docs, Sheets, or Slides are not ready.

## Likely Causes

- Google OAuth completed, but no Workspace Folder has been selected.
- The selected Google Drive folder was removed or permissions changed.
- The selected folder is in trash, is no longer a folder, or is not accessible
  to the connected Google account under `drive.file`.
- Google Picker was blocked by browser settings, third-party cookie policy,
  private browsing, or a Picker error before folder selection finished.
- The account is connected but MoClaw is intentionally scoped to a folder rather
  than the whole Drive.

## Recovery Steps

1. Open **left sidebar > Connectors**.
2. Open the Google Workspace row menu.
3. Choose **Select Existing Folder** to pick a Drive folder, or **Create New
   Folder** to create a MoClaw Agent Space folder.
4. If Picker fails or does not open, use **Create New Folder** or retry the
   folder setup flow so the fallback can create/reuse `MoClaw Agent Space`.
5. Wait for the connector row to show ready status.
6. Retry the Drive/Docs/Sheets/Slides task.

## Escalate When

- Folder picker cannot open.
- Folder selection succeeds but the connector remains in needs-folder state.
- The user cannot access the selected folder in Google Drive.
- The folder is visible to the user but validation still says it is not
  accessible under `drive.file`.
- The fallback folder is created but the connector still shows
  **Drive setup needed**.

## Do Not Say

- Do not say MoClaw can access the user's whole Drive.
- Do not imply Gmail/Calendar failure if the visible issue is only Drive folder
  setup.
- Do not tell users to grant full Drive access as the first fix.
- Do not ask users for Google OAuth codes, access tokens, refresh tokens,
  cookies, passwords, signed URLs, or full raw logs.

## Related Cards

- `moclaw.how_to.connect_google_workspace`
- `moclaw.reference.connectors_status`
- `moclaw.reference.google_workspace_scopes`
- `moclaw.playbooks.ask_for_screenshot_or_reference_id`
