---
id: help.connectors.google_workspace_permissions
title: Google Workspace Permissions
audience: user
status: verified
source_cards:
  - moclaw.reference.google_workspace_scopes
  - moclaw.how_to.connect_google_workspace
  - moclaw.troubleshooting.google_workspace_needs_folder
last_reviewed_at: 2026-06-09
---

# Google Workspace Permissions

MoClaw may ask for Google Workspace permissions so it can work with services
such as Gmail, Calendar, Tasks, Drive, Docs, Sheets, and Slides when the
connector is available for your account.

## Drive Access Is Folder-Scoped

MoClaw should not be described as having access to your entire Google Drive.

The current Drive/Docs/Sheets/Slides model uses a selected Workspace Folder.
MoClaw can work with app-created files and files you select or place in that
folder.

That folder can be one you select with Google Picker, or a folder named
`MoClaw Agent Space` that MoClaw creates or reuses if you choose **Create New
Folder** or the picker cannot be used. Creating or reusing that folder does not
mean MoClaw received whole-Drive access.

If Gmail or Calendar works but Drive files do not, check whether Google
Workspace still says **Drive setup needed**.

## What The Permissions Are For

| Area | Purpose |
|---|---|
| Google account email | Identify the connected Google account. |
| Gmail | Read, compose, and send mail for tasks you ask MoClaw to do. |
| Calendar | Read and manage calendar events. |
| Tasks | Work with Google Tasks. |
| Drive folder files | Work with files in the selected Workspace Folder. |

Gmail, Calendar, Tasks, and Drive folder setup are separate surfaces. One area
working does not prove every Google service is ready, and one Drive setup issue
does not mean Gmail or Calendar is broken.

The browser-side token used for folder selection is downscoped to `drive.file`.
MoClaw's stored Google refresh token stays server-side and should not be sent to
support.

## What To Send Support

- Account email.
- Screenshot of the Google Workspace connector state.
- Whether a Workspace Folder is selected.
- Whether the issue is Gmail/Calendar/Tasks or Drive/Docs/Sheets/Slides.

Do not send OAuth codes, access tokens, refresh tokens, cookies, passwords,
signed URLs, or raw email/file contents.

## Related Articles

- `connectors/connect-google-workspace.md`
- `security/privacy-and-access.md`
