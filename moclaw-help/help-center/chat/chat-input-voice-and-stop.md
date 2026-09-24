---
id: help.chat.chat_input_voice_and_stop
title: Chat Input, Voice, And Stop
audience: user
status: verified
source_cards:
  - moclaw.reference.chat_composer_controls
  - moclaw.reference.chat_conversations_and_history
  - moclaw.troubleshooting.voice_recording_not_working
  - moclaw.how_to.upload_or_reference_file
last_reviewed_at: 2026-07-23
---

# Chat Input, Voice, And Stop

Use the chat input at the bottom of `/chat` to send text, attach files, mention
workspace files, choose a model tier, stop a response, or record voice when that
feature is available.

## Send A Message

Type your message and use the send button. If your settings use `Enter`, press
`Enter` to send and `Shift+Enter` for a newline. If your settings use
`Cmd+Enter` or `Ctrl+Enter`, plain `Enter` creates a newline.

The send button may be unavailable while MoClaw is waiting for the workspace,
uploading a file, or showing a failed attachment chip.

## Attach Or Mention Files

Use the attachment button to upload a local file. Wait until the chip finishes
uploading before sending.

To reference a file already in the workspace, type `@` when file suggestions
are available.

## Stop A Response

When MoClaw is responding and the input is empty, the send action becomes a stop
button. Use it to request that the current response stops.

If you type a new text message while a response is streaming, MoClaw can send
that as additional context. If you include files during an active response,
MoClaw may queue that file message until the current response finishes.

## Record A Voice Message

If the microphone button is visible, use it to start recording. Use it again to
stop. Voice recording needs browser microphone permission.

Current limits:

- Record at least 1 second.
- Recordings stop at 3 minutes.
- If transcription fails, the voice message can still send, but MoClaw may not
  have the spoken text for that turn. Resend the key details as text if needed.

## If Voice Is Not Working

Check browser microphone permission first. If the browser says voice recording
is unsupported, try a modern desktop browser. If the voice button is missing, it
may not be enabled for your current environment.

## Related Articles

- `workspace/upload-or-reference-files.md`
- `chat/start-new-conversation-and-history.md`
- `chat/read-chat-messages-and-open-files.md`
- `workspace/skills-and-commands.md`
- `chat/model-tiers.md`
