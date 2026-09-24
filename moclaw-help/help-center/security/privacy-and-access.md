---
id: help.security.privacy_and_access
title: Privacy, Access, And Local Files
audience: user
status: verified
source_cards:
  - moclaw.playbooks.security_privacy_answering
  - moclaw.concepts.ai_cloud_computer
  - moclaw.concepts.workspace_file_and_artifact
  - moclaw.concepts.connectors_channels_skills
  - moclaw.reference.google_workspace_scopes
  - moclaw.reference.local_desktop_permissions
  - moclaw.reference.account_identity_and_data_requests
last_reviewed_at: 2026-07-28
---

# Privacy, Access, And Local Files

MoClaw separates cloud workspace access, uploaded files, workspace files,
connectors, channels, and Local Desktop access.

The access boundary depends on which surface you are using.

This article explains product access boundaries. It is not a legal, compliance,
retention, or model-training-policy commitment.

## Quick Reference

| If you are using... | What it means |
|---|---|
| Chat upload | The uploaded file becomes available in the MoClaw workspace for the task. It is not local-only after upload. |
| `@` file reference, **Quote in chat**, or **Prompt** | MoClaw is referencing an existing workspace file. This does not upload the same file again from your computer. |
| Google Workspace | Access is service-specific. Drive/Docs/Sheets/Slides use the selected Workspace Folder under Google `drive.file`; Gmail, Calendar, and Tasks are separate. |
| GitHub, Linear, or MCP connector | Access depends on that provider's authorization and connector settings. One connector does not grant access to all services. |
| Telegram, Slack, Lark, or Discord channel | A channel is a place to chat with MoClaw. It is not the same as granting service data access. |
| Local Desktop | Local browser/files/clipboard/commands require MoClaw Desktop and the relevant local capability. File tools are currently fixed to the desktop user's Home directory, and OS permission still applies. Bash is a separate permission surface. |

## Cloud Workspace

MoClaw normally works inside the AI Cloud Computer. Files uploaded to MoClaw or
created by MoClaw are workspace resources. They are not the same as arbitrary
local files on your computer.

Uploaded files are available to the MoClaw workspace for the task. Do not treat
an uploaded file as local-only after upload.

Workspace file references, such as `@` references or **Quote in chat**, point
to files that already exist in the MoClaw workspace. They are different from
uploading a fresh local file.

## Workspace Files And Artifacts

Workspace files are files in the current AI Cloud Computer workspace. Artifacts
are published outputs that MoClaw presents for preview, download, or later use.

The current Artifacts page shows published outputs, not the whole workspace
tree. Support should not ask you to paste raw internal paths, signed URLs,
authentication headers, or private tokens.

## Connectors

Connectors are third-party access paths such as GitHub, Linear, Google
Workspace, or MCP servers. Connector availability and permissions depend on the
service, your account, and the authorization flow.

Connecting one service does not automatically give MoClaw access to all other
services.

Do not send connector secrets, OAuth codes, access tokens, refresh tokens,
cookies, passwords, or provider config files to support.

### Google Workspace

Google Workspace permissions depend on the connector flow. The current
Drive/Docs/Sheets/Slides design is scoped to a selected Workspace Folder through
Google `drive.file`, not full Google Drive access.

Gmail, Calendar, and Tasks have separate permissions for the tasks you ask
MoClaw to do.

If Drive/Docs/Sheets/Slides are not ready, check whether the Workspace Folder is
selected before assuming the entire Google connection failed.

## Channels

Channels let you chat with MoClaw from another app, such as Telegram or Slack
when available for your account.

A chat channel is not the same as a data connector. Connecting a Slack or
Telegram chat channel does not by itself mean MoClaw can read every file,
message, repository, or document in that third-party workspace.

## Local Desktop

Local Desktop capabilities are available only inside MoClaw Desktop. Installing
the desktop app does not give MoClaw full access to your computer.

For local file work, file tools are currently fixed to the desktop app user's
Home directory, paths are normalized before the runtime boundary check, and OS
permissions still apply. MoClaw Desktop does not show a per-directory approval
prompt, keep an approved-folder list, or provide a shortcut to system file
access settings.

Bash Commands use a separate and broader risk model. On supported platforms,
Bash is enabled in the current default config and runs commands directly while
enabled. Its initial working directory must be inside Home, while the command
itself is not contained by a file system sandbox. Disable Bash in **Settings >
Local Tools** when local command execution is not wanted, and do not use Bash as
a workaround for an OS-denied local file.

## Compliance Or Legal Questions

For legal terms, DPA, retention, deletion, SOC 2, ISO, HIPAA, GDPR, whether
customer data is used for model training, or similar questions, ask support for
the current owner-reviewed policy. Do not rely on a general product article as
a legal commitment.

For account deletion, data deletion, or data export requests, include your
account email and the request type. Do not send passwords, full card numbers,
CVV, API keys, OAuth tokens, or unrelated personal data.

## What To Send Support

- Account email.
- Which surface is involved: cloud workspace, upload, artifact, connector,
  channel, Local Desktop, or account/data request.
- Visible page or section.
- Exact visible error copy, if any.
- Approximate time and timezone.
- Screenshot with secrets redacted.

Do not send passwords, OAuth tokens, API keys, cookies, full card numbers, CVV,
signed URLs, device codes, private file contents, or full raw logs.

## Related Articles

- `getting-started/ai-cloud-computer.md`
- `desktop/local-desktop.md`
- `connectors/connectors-overview.md`
- `account/account-and-data-requests.md`
