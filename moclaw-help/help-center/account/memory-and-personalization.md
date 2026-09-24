---
id: help.account.memory_and_personalization
title: Memory And Personalization
audience: user
status: verified
source_cards:
  - moclaw.concepts.memory_and_personalization
  - moclaw.concepts.workspace_file_and_artifact
  - moclaw.reference.user_preferences_and_settings
  - moclaw.reference.account_identity_and_data_requests
last_reviewed_at: 2026-06-09
---

# Memory And Personalization

MoClaw may use context from your current conversation and workspace to continue
work. That context is not all one thing.

## What Counts As Context

- Chat history is the message history in the current conversation/session.
- Settings preferences are things like theme, language, and send-key behavior.
- Workspace memory files can appear as `MEMORY.md` or a `memory/` folder in the
  AI Cloud Computer workspace.
- Artifacts are separate user-facing outputs that MoClaw has surfaced for
  preview, reuse, or download.
- Internal memory/search systems can exist behind the scenes, but they are not a
  customer-facing settings page or support API.

## Where To Look

- For chat context, use the current chat and **Load earlier messages** when it
  appears.
- For preferences, open **Settings**.
- For workspace memory files, open **left sidebar > Artifacts**, then use the file
  manager when it is available and look for `MEMORY.md` or `memory/`.
- For generated outputs, use **left sidebar > Artifacts**.

## If You Want Something Changed Or Removed

Ask MoClaw clearly what you want changed, such as "do not use this preference in
future replies" or "use this updated project context instead."

That is a task request to MoClaw. It should not be treated as a guaranteed
account-wide deletion, export, or retention action.

For account deletion, data deletion, data export, retention, or legal privacy
requests, use the account/data request path rather than assuming a chat command
fully removes all stored data.

## Current Limits

- A dedicated Memory settings page is not currently confirmed.
- Self-serve controls to edit, delete, export, or disable each individual memory
  item are not currently confirmed.
- Starting a new conversation does not guarantee all memory or workspace files
  are cleared.
- Workspace memory files are workspace files, not automatically published
  Artifacts.
- Do not paste secrets, passwords, API keys, OAuth tokens, cookies, or signed
  URLs into chat to prove what should be forgotten.

## Related Articles

- `account/account-and-data-requests.md`
- `workspace/files-and-artifacts.md`
- `chat/start-new-conversation-and-history.md`
