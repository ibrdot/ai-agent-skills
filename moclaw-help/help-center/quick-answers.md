---
id: help.quick_answers
title: Quick Answers
audience: user
status: verified
source_cards:
  - moclaw.foundation.product_identity
  - moclaw.concepts.ai_cloud_computer
  - moclaw.concepts.workspace_file_and_artifact
  - moclaw.reference.chat_composer_controls
  - moclaw.reference.message_display_and_actions
  - moclaw.reference.pricing_and_credits
  - moclaw.concepts.credits_entitlement
  - moclaw.concepts.connectors_channels_skills
  - moclaw.reference.connectors_status
  - moclaw.reference.local_desktop_permissions
  - moclaw.reference.google_workspace_scopes
  - moclaw.playbooks.security_privacy_answering
  - moclaw.reference.support_feedback_and_diagnostics
  - moclaw.reference.account_identity_and_data_requests
  - moclaw.reference.account_profile_and_user_menu
  - moclaw.ui.billing_and_usage_surfaces
  - moclaw.reference.billing_invoices
last_reviewed_at: 2026-07-28
---

# Quick Answers

Use this page when you need the short version. Each answer links to the fuller
article for details.

## What Is MoClaw?

MoClaw is a personal AI agent that works in an AI Cloud Computer. It can help
with chat tasks, files, generated outputs, connectors, and workspace actions
depending on your account, environment, and connected services.

Read more: `getting-started/what-is-moclaw.md`

## Where Does The Work Happen?

Most work happens in the AI Cloud Computer, not directly on your personal
computer. Local browser, local files, local clipboard, or local commands require
the MoClaw Desktop app and the relevant local capability. The browser Web App
does not provide local capabilities, and installing the desktop app does not
grant full machine access.

Read more: `getting-started/ai-cloud-computer.md`,
`workspace/cloud-and-local-tools.md`, `desktop/local-desktop.md`

## How Do I Give MoClaw A File?

You can upload files in chat, paste supported content, drag files into the chat
area, or reference files that already exist in the workspace. A workspace `@`
reference points to an existing workspace file; it does not upload the same
local file again.

Read more: `workspace/upload-or-reference-files.md`,
`workspace/files-and-artifacts.md`

## Where Are Generated Files?

Generated outputs usually appear in **Artifacts** or as files in Chat. The
current web app does not expose an **All files** browser for the whole workspace
tree.

Read more: `workspace/files-and-artifacts.md`

## What Does MoClaw Remember?

Memory and context are not one thing. MoClaw can use the current chat history,
your browser-local preferences, and workspace files such as `MEMORY.md` or
`memory/` when they exist. A new conversation or "forget this" request should
not be treated as guaranteed account-wide deletion.

Read more: `account/memory-and-personalization.md`

## How Do I Delete Or Export Account Data?

Current **Settings > Account** shows your signed-in identity and plan state, but
current help sources do not show self-serve controls for editing email, display
name, or avatar, or for account deletion, data export, or data deletion. Contact
support with the request type, account email, whether you can still sign in, and
any active Pro, checkout, invoice, refund, or billing concern.

Account/data requests, subscription cancellation, refunds, invoices, and billing
records are separate workflows. Do not send passwords, verification codes,
OAuth tokens, API keys, browser storage, full card numbers, CVV, identity
documents, or full raw logs.

Read more: `account/account-and-data-requests.md`

## What Can MoClaw Access?

Access depends on the surface. Uploaded files, workspace files, connectors,
chat channels, Google Workspace, and Local Desktop all have different access
rules. Local file tools require MoClaw Desktop and are currently fixed to the
desktop user's Home directory. The app does not ask for per-directory approval,
and the operating system can still deny protected locations. Do not send
passwords, OAuth tokens, API keys, signed URLs, private file contents, or full
raw logs to support.

For SOC 2, ISO, HIPAA, DPA, GDPR, retention, deletion, or whether customer data
is used for model training, ask support for the current owner-reviewed policy.

Read more: `security/privacy-and-access.md`

## What Do Thinking, Used Tools, Copy, And Retry Mean?

**Thinking** and **Used tools** show visible activity, not complete hidden model
reasoning. Copy normally copies message text. Failed or interrupted messages
may add compact diagnostic ids. Retry can appear for failed text-only user
messages, but it cannot reconstruct uploaded files.

Read more: `chat/read-chat-messages-and-open-files.md`

## Why Is Chat Blocked Even Though I See Credits?

Credits and product access are separate. If Pro or Trial access is inactive,
credits may be visible but unusable.

Read more: `billing/pricing-credits-trials.md`

## Where Are Usage, Billing, And Invoices?

Open **Settings** from the user menu. Use **Usage** for credits and history,
**Billing** for billing/payment surfaces, and **Account** for plan state.

Read more: `billing/find-usage-billing-and-invoices.md`,
`account/settings-and-account.md`

## How Do Connectors Work?

Connectors are service access paths. Current confirmed connector rows are
Google Workspace, GitHub, and Linear when visible for your account and
environment. Telegram, Slack, Lark, and Discord are Channels, which are chat
entry points, not data connectors. Treat MCP as available only if you can see
an MCP row or support confirms it for your account.

Google Workspace is the row for Gmail, Calendar, Tasks, Drive, Docs, Sheets,
and Slides. If MCP is visible, it uses **Manage** for remote MCP servers. OAuth
success is not always enough; each provider can have separate scope, folder,
repository, workspace, or tool setup. Linear uses OAuth for a connected
user/workspace, and write actions currently default to that authorized Linear
user.

Read more: `connectors/connectors-overview.md`

## Can I Use Google Drive?

Current Google Drive/Docs/Sheets/Slides access is scoped through the selected
Google Workspace Folder under Google `drive.file`. It is not full Google Drive
access. Gmail, Calendar, and Tasks have separate readiness from Drive setup.

Read more: `connectors/google-workspace-permissions.md`

## How Do I Report A Bug Safely?

Use **Bug Report** / **Report a Bug** if it is visible. Include what happened,
what you expected, approximate time, visible error copy, and a screenshot with
secrets redacted. Use Reference ID or copied diagnostic text when shown; do not
send full raw logs or secrets.

Read more: `troubleshooting/contact-support-and-send-diagnostics.md`
