---
id: help.chat.start_new_conversation_history
title: Start A New Conversation And Load History
audience: user
status: verified
source_cards:
  - moclaw.reference.chat_conversations_and_history
  - moclaw.concepts.session_thread_message
  - moclaw.reference.skills_and_slash_commands
  - moclaw.reference.chat_composer_controls
  - moclaw.reference.message_display_and_actions
last_reviewed_at: 2026-07-09
---

# Start A New Conversation And Load History

Use **New session** when you want a fresh chat workspace in Recents. Use `/new`
when you want a fresh conversation thread inside the current Session.

## Start A New Session

1. Open `/chat`.
2. Open the left sidebar.
3. In **Recents**, choose **New session**.

You can also select a recent Session from **Recents**. When row actions are
visible, you can rename or delete a Session from the list.

## Start A New Conversation Thread

1. Click the `/` button in the chat input, or type `/` at the start of a
   message.
2. Choose `/new`, or type `/new` and send it.

MoClaw starts a new conversation thread inside the current Session.

## What Changes

Starting a new Session changes the visible chat workspace. Starting `/new`
changes the current message thread. Neither action creates a new account or
guarantees a new AI Cloud Computer. Workspace files and artifacts may still
belong to the relevant workspace/session context.

If you need MoClaw to continue work from an old conversation, give it a short
summary or point it to the key workspace files. Do not paste passwords, API
keys, OAuth tokens, or other secrets.

## Load Earlier Messages

If **Load earlier messages** appears in the chat, use it to load older messages
in chunks. Use **Recents** to switch between visible Sessions.

## If You See An Error

| Error Or Symptom | What To Try |
|---|---|
| **Conversation too long** | Start a new thread or Session, then carry over a short summary and any key files. |
| **Current session issue. Please start a new chat.** | Start a new Session from Recents, or use `/new` if the current Session still loads. If it repeats, contact support with the visible error and time. |
| **Too many active sessions** | Wait a moment and try again. This does not automatically mean you need to upgrade. |
| **Failed to active session. Please try again later.** | Wait until the workspace/session is ready, then retry. If it repeats, send support your account email, approximate time, and a screenshot. |

## Related Articles

- `chat/chat-input-voice-and-stop.md`
- `workspace/skills-and-commands.md`
- `chat/read-chat-messages-and-open-files.md`
- `troubleshooting/common-errors.md`
