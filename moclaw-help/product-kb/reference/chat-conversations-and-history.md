---
id: moclaw.reference.chat_conversations_and_history
title: Chat Conversations And History
type: reference
product_area: chat
audience: support
status: verified
last_reviewed_at: 2026-07-09
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Chat Conversations And History

## Direct Answer

MoClaw now exposes chat **Sessions** in the left sidebar **Recents** list.
Users can start a fresh visible chat workspace with **New session**, select a
recent Session, rename it, or delete it from the row actions when those controls
are visible.

Inside a Session, `/new` remains a command-menu shortcut for starting a fresh
conversation thread in that Session. Earlier messages can be loaded with **Load
earlier messages** when that control is available.

Do not collapse Session, Thread, browser login session, and account history into
one concept. Do not promise export or full account-wide history controls unless
a current product source confirms them.

## Sessions And Recents

The `/chat` route supports selecting a Session with a `session` query
parameter. The left sidebar has a **Recents** section:

- **New session** clears the active chat selection and shows an empty chat
  starting point.
- Selecting a row activates that Session and loads its messages/runtime context.
- Rows can show a running spinner when the agent is active.
- Rows can show channel badges when the Session is associated with Telegram,
  Slack, Lark, or Discord.
- Row actions can rename or delete the Session from the visible Recents list.
- Session titles can also be renamed from the chat header when the header is
  shown.

The session list is user-facing, but support answers should still avoid exposing
raw app-session ids unless the user is collecting diagnostic context.

## How New Conversation Threads Work

Current slash commands are loaded from the server command registry. The visible registry
includes `/new` and `/stop`.

`/new` creates a thread inside the current Session through the sessions API:

- frontend command execution calls the sessions thread endpoint;
- the active thread id changes;
- the local chat state is reset for that thread;
- a local welcome message is added for the new conversation.

Starting a new conversation thread does not create a new account, change the
user's plan, or necessarily create a new AI Cloud Computer. It also does not
guarantee that workspace files or artifacts are cleared, because those belong to
the workspace/session context, not only the visible message list.

## History Loading

MoClaw loads messages for the active thread and can load earlier messages in
chunks. The chat store tracks the current thread id, remaining threads, and
pagination cursors. Thread history is retrieved through runtime thread/message
APIs.

Support wording should stay user-facing:

- say "current conversation" for Thread;
- say "Session" or "Recents" when the user is switching visible chat workspaces;
- say "current workspace" only when troubleshooting files, runtime, schedules,
  or cloud-computer behavior;
- describe older content as "earlier messages/conversations in the current
  session" unless the user is explicitly asking about the Recents list.

## Failure States

| Visible Copy Or Symptom | Safe Support Guidance |
|---|---|
| **Conversation too long - please start a new conversation.** | Start a new conversation, then carry over a short summary or the key files/details needed for the next step. |
| **Current session issue. Please start a new chat.** | Start a new Session from Recents/New session, or use `/new` if the current Session still loads. If it repeats, use workspace/session troubleshooting and collect visible error copy/time. |
| **Too many active sessions - please wait a moment and try again.** | Wait briefly and retry. Do not assume this is a billing or upgrade issue. |
| **Failed to active session. Please try again later.** | Retry after the workspace/session is ready. If it repeats, collect account email, approximate time, and a screenshot of the visible state. |

## Do Not Say

- Do not say **New session** or `/new` deletes previous conversations.
- Do not say **New session** or `/new` creates a new account, billing state, browser login
  session, AI Cloud Computer, or cleared workspace.
- Do not say deleting a Session is the same as deleting account data, files, or
  provider-side records.
- Do not promise visible export or full history-manager controls for
  conversations.
- Do not call Thread a browser session or login session.
- Do not tell users that "Conversation too long" means they must upgrade.
- Do not ask users to paste secrets to recreate lost context.

## Related Cards

- `moclaw.concepts.session_thread_message`
- `moclaw.reference.skills_and_slash_commands`
- `moclaw.reference.chat_composer_controls`
- `moclaw.reference.message_display_and_actions`
- `moclaw.troubleshooting.workspace_unavailable`
- `moclaw.troubleshooting.model_provider_timeout`
- `moclaw.troubleshooting.credits_locked`
