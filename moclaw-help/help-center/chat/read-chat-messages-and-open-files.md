---
id: help.chat.read_messages_open_files
title: Read Chat Messages And Open Files
audience: user
status: verified
source_cards:
  - moclaw.reference.message_display_and_actions
  - moclaw.reference.cloud_and_local_tools
  - moclaw.reference.file_preview_limits
  - moclaw.troubleshooting.file_cannot_preview_or_download
  - moclaw.troubleshooting.voice_recording_not_working
last_reviewed_at: 2026-06-08
---

# Read Chat Messages And Open Files

MoClaw messages can include text, files, images, voice clips, tool activity, and
follow-up suggestions.

## Message Activity

**Thinking** shows visible activity or working text when MoClaw is processing.
You can expand or collapse it when it appears.

**Used tools** groups tool activity. Open a tool row to see details such as a
command, output, error, or running status. Very long output may show a
**Show more lines** action.

## Files, Images, And Voice

Click a file card or image to open it in the preview area when preview is
available. Some files may only download, and some files may not preview at all.

Voice messages show a play button, waveform, and duration. If the audio cannot
be resolved, the player may show **unavailable**.

## Copy And Retry

Hover or focus a completed message to reveal the copy action when copyable text
is available. Normal completed messages copy their message text; they do not add
diagnostic ids just because the message has internal ids.

Failed, canceled, or interrupted messages may add a `Diagnostic data:` section
to the copied text. This can include message or run ids such as **Assistant
Message ID**, **Run ID**, **User Message ID**, or **Client Message ID** so
support can locate the failed turn. It is not a request to send full raw logs,
passwords, API keys, tokens, signed URLs, or private file contents.

If your own text-only message failed, MoClaw may show **Retry**. Retry resends
that failed text in the current conversation; it does not start a new chat.
Retry is not available for failed messages with uploaded files because the
original local file cannot be reconstructed from the chat bubble. Some specific
failures, such as usage limits, rate limits, prompt-too-long, workspace issues,
or current-session issues, show guidance without Retry.

## Follow-Up Suggestions

Suggested follow-ups appear after some assistant replies. Choose one to send it
as your next message. They disappear once you send another message or while
MoClaw is streaming.

## Older Messages

If there is more history, use **Load earlier messages** at the top of the
message list.

## If Something Does Not Open

Refresh the file list or reopen the message. If a file still cannot preview or
download, collect the file name, visible error copy, and approximate time for
support. Do not send passwords, API keys, OAuth tokens, or signed URLs.

## Related Articles

- `workspace/files-and-artifacts.md`
- `workspace/cloud-and-local-tools.md`
- `workspace/upload-or-reference-files.md`
- `chat/chat-input-voice-and-stop.md`
- `troubleshooting/common-errors.md`
