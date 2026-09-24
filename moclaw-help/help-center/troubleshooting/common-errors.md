---
id: help.troubleshooting.common_errors
title: Common Errors And What To Try
audience: user
status: verified
source_cards:
  - moclaw.troubleshooting.workspace_unavailable
  - moclaw.reference.ai_cloud_computer_viewer
  - moclaw.troubleshooting.sandbox_capacity_full
  - moclaw.troubleshooting.model_provider_timeout
  - moclaw.troubleshooting.file_cannot_preview_or_download
  - moclaw.reference.file_preview_renderers
  - moclaw.troubleshooting.voice_recording_not_working
  - moclaw.troubleshooting.credits_locked
  - moclaw.troubleshooting.checkout_payment_not_updated
  - moclaw.troubleshooting.model_tier_unavailable_or_switch_failed
  - moclaw.reference.chat_conversations_and_history
  - moclaw.troubleshooting.chat_file_upload_or_attachment_failed
  - moclaw.troubleshooting.mcp_server_connection_or_tools_missing
  - moclaw.troubleshooting.connector_expired
  - moclaw.playbooks.security_privacy_answering
  - moclaw.reference.authentication_and_login
  - moclaw.reference.support_feedback_and_diagnostics
  - moclaw.playbooks.ask_for_screenshot_or_reference_id
last_reviewed_at: 2026-07-29
---

# Common Errors And What To Try

Start with the visible symptom. Do not worry about the internal component name.

## Workspace Is Unavailable

Try the retry action if the UI offers one. If there is a restart workspace
action, use it. If the workspace is recovering, wait briefly and retry.

If the same issue repeats, collect your account email, approximate time, visible
error copy, and any reference id shown in the UI.

## AI Cloud Computer Viewer Failed

On a desktop Session page, click the Cloud Computer button in the top Chat
header. When the Session Dock is collapsed, the button is immediately
left of its expand control. It opens or reuses the App Shell viewer. If **Open in new window** does nothing,
your browser may have blocked the pop-out. The AI Cloud Computer viewer is the
cloud workspace, not your personal computer. Opening or closing the viewer, or
a viewer connection error, does not create, switch, or end the Chat Session.

## Sandbox Capacity Is Full

This usually means MoClaw temporarily cannot allocate a workspace. Wait and
retry. If many retries fail or the issue blocks paid work, collect the
approximate time and visible error copy for support.

## Model Provider Timed Out

Retry the message. If the prompt is very large, split it into smaller steps. If
the issue repeats, send the model tier, approximate time, and a short
description of the prompt.

## Conversation Too Long

Start a new conversation with `/new`, then carry over a short summary and any
key files. This does not automatically mean you need to upgrade, and it does
not delete previous messages.

## Current Session Issue

If the chat says **Current session issue. Please start a new chat.**, start a
new conversation. If the same message repeats, collect your account email,
approximate time, visible error copy, and a screenshot for support.

## Too Many Active Sessions

Wait a moment and try again. Do not send passwords, API keys, OAuth tokens, or
other secrets while trying to recreate context.

## Login Failed Or Callback Is Stuck

If you see **Login failed. Please try again.**, retry from the login page. If
the page is stuck on a callback or spinner, refresh once or open `/auth`, then
try signing in again.

Do not send OAuth codes, access tokens, refresh tokens, cookies, passwords, or
full browser storage to support.

## Model Tier Is Locked Or Switch Failed

Check **Settings > Account** for active Pro state. If the selector returns to
**Fast** or **Standard**, MoClaw may have corrected a tier that is not
authorized for the current account state.

## File Cannot Preview Or Download

Refresh **Artifacts** or reopen the file from Chat. If preview fails but
**Download original** is available, download the original. If download is
disabled, check whether the file is too large for workspace transfer.

For generated `.html`, `.htm`, `.jsx`, `.tsx`, `.mmd`, or `.mermaid` files,
preview errors can come from source syntax, unsupported preview dependencies,
runtime errors, or diagram rendering limits.

## File Upload Or Attachment Failed

If a file upload fails, check whether it is over the current chat upload limit.
If a failed attachment chip is blocking Send, remove the chip and attach a
smaller file or retry. Drag-and-drop only attaches real file drags over the chat
panel.

Large pasted text can become a `pasted-...txt` attachment. If that upload fails,
MoClaw may restore the pasted text to the editor. If a file/reference message is
queued while MoClaw is already responding, wait for the current response to
finish; if the queue failed, send it again after the response is done.

## Voice Recording Is Not Working

If the voice button is missing, it may not be enabled in the current
environment. If recording fails, check browser microphone permission and browser
support. Record for at least 1 second; current voice recordings stop at 3
minutes. If transcription fails, the voice message may still send, but MoClaw
may not have the spoken text for that turn.

## Credits Are Visible But Locked

Open **Settings > Usage** to check credits and **Settings > Account** to check
plan state. Credits may be locked when Pro or Trial access has expired, or when
you bought credits without active product access.

If `/chat` says **Billing status is temporarily unavailable**, wait for the
retry and refresh Usage/Account before assuming the payment or subscription
failed.

## Checkout Payment Or Credits Not Updated

Return to `/chat`, then refresh **Settings > Usage**. Check **Settings >
Account** for plan state and **Settings > Billing** for payment history. If the
state still looks wrong, collect the checkout time, charge amount/date, and any
visible invoice, receipt, or checkout reference for support.

## MCP Server Test Or Sync Failed

Open **left sidebar > Connectors** and check whether **MCP** is visible. If it
is, open **MCP > Manage**. Confirm the endpoint is a remote `https://`
Streamable HTTP MCP server, not a local command-line config. Run **Test**, then
**Refresh/Sync**, and check the server status, tool count, and visible error
copy.

## Connector Expired Or Reconnect Failed

Open **left sidebar > Connectors** and reconnect the affected service. If
disconnecting a GitHub organization only removed the local connection, open
GitHub's own app settings to uninstall the app or adjust repository access.
Never send OAuth tokens, authorization codes, passwords, or API keys to support.

## Access Or Privacy Concern

First identify the surface involved: chat upload, workspace file, Artifact,
connector, channel, Local Desktop, or account/data request.

Uploading a file makes it available in the MoClaw workspace for the task. A
workspace `@` reference points to an existing workspace file and does not upload
the same local file again. The current Artifacts page shows published outputs,
not the whole workspace tree. Local file tools require Local Desktop, are
currently fixed to the desktop user's Home directory, and still follow OS
permissions. Google Drive/Docs/Sheets/Slides access is scoped through the
selected Google Workspace Folder under `drive.file`.

Do not send passwords, OAuth tokens, API keys, cookies, signed URLs, private
file contents, or full raw logs while asking about access.

## What To Send Support

If **Bug Report** / **Report a Bug** is visible, use it. If it is missing, the
feedback path may not be available in the current environment; collect the same
details and use your normal support path.

Bug Report needs a written description. It can stage one image screenshot up to
5 MB; use **Copy reference** for compact diagnostic text instead of attaching
full logs.

Send only what is needed:

- Account email.
- Approximate time and timezone.
- What you were trying to do and what you expected.
- Screenshot of the visible MoClaw UI state.
- Exact visible error copy.
- Reference ID / **Copy reference**, invoice id, file name, connector name, or
  task id if the UI shows one.

Redact passwords, full card numbers, CVV, API keys, OAuth tokens, signed URLs,
and unrelated personal data.

For more detail, see `troubleshooting/contact-support-and-send-diagnostics.md`.
