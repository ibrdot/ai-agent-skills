---
id: moclaw.reference.google_workspace_scopes
title: Google Workspace Scopes
type: reference
product_area: connectors
audience: support
status: verified
last_reviewed_at: 2026-06-09
applies_to:
  plans: [free, trial, pro]
  environments: [test, prod]
  platforms: [web]
---

# Google Workspace Scopes

## Direct Answer

Current Google Workspace design uses a narrower Drive permission model:
Drive/Docs/Sheets/Slides access is scoped through `drive.file` and a selected
Workspace Folder, not full Google Drive access.

Google Workspace should be answered as service-specific access, not one
all-or-nothing permission. Gmail, Calendar, Tasks, and Drive folder setup can
have different readiness states.

## Current Scope Set

The current app-server config lists these Google OAuth scopes:

| Area | Scope | User-facing meaning |
|---|---|---|
| User email | `userinfo.email` | Identify the connected Google account. |
| Gmail | `gmail.modify` | Read, compose, and send Gmail messages. |
| Calendar | `calendar` | Read/write calendar events and manage calendars. |
| Tasks | `tasks` | Work with Google Tasks. |
| Drive files | `drive.file` | Work with app-created or user-selected Drive files/folders. |

Drive/Docs/Sheets/Slides currently use `drive.file`; do not say MoClaw needs
full `drive`, `spreadsheets`, `documents`, or `presentations` scopes for the
current folder-scoped design.

## Drive Folder Rule

The intended Drive/Docs/Sheets/Slides model is setup-time folder selection:

1. User connects Google Workspace.
2. User selects an existing Drive folder or creates/reuses a
   `MoClaw Agent Space` folder.
3. MoClaw stores that folder id.
4. Agent-created Google files are placed in that folder.
5. User-owned files should be put or selected into that folder for MoClaw to use.

The selected folder grants access to that folder and its current/future
contents under `drive.file`. If Picker is unavailable because of browser
constraints, the product can create or reuse a `MoClaw Agent Space` folder as
the Workspace Folder.

Server-side validation checks that the folder exists, is a folder, is not in
trash, and is accessible under the current `drive.file` token before storing
the folder id.

The Picker access token is requested with only `drive.file`, even when the
stored Google connection also has Gmail and Calendar scopes. This narrows the
browser-side token used for folder selection.

Sandbox/runtime access receives a short-lived access token and the stored
Workspace Folder id. The Google refresh token remains server-side.

## Support Implications

- If Gmail/Calendar/Tasks work but Drive/Docs/Sheets/Slides do not, check
  whether the Workspace Folder is selected.
- Do not say MoClaw can read the user's whole Drive.
- Do not describe `drive.file` as equivalent to full `drive`.
- If the user asks why Google Picker did not appear, explain that some browser
  settings can block Picker and that **Create New Folder** or the fallback
  `MoClaw Agent Space` path can still complete setup.
- If the user asks whether MoClaw can use a specific file outside the Workspace
  Folder, tell them to move/copy/select it into the Workspace Folder or choose
  a different Workspace Folder.
- Do not ask for Google OAuth tokens, authorization codes, refresh tokens,
  cookies, passwords, signed URLs, or full raw logs.
- If a user asks for exact compliance or Google verification status, escalate to
  the connector/product owner.
- Do not use this card to answer SOC 2, ISO, HIPAA, DPA, GDPR, retention, or
  model-training-policy questions.

## Related Cards

- `moclaw.how_to.connect_google_workspace`
- `moclaw.troubleshooting.google_workspace_needs_folder`
- `moclaw.reference.connectors_status`
- `moclaw.playbooks.security_privacy_answering`
