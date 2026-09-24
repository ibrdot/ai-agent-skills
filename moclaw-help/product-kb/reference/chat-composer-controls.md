---
id: moclaw.reference.chat_composer_controls
title: Chat Composer Controls
type: reference
product_area: chat
audience: user
status: verified
owner: product
last_reviewed_at: 2026-06-15
source_paths:
  - maxgent/client/webapp/src/components/chat/chat-input.tsx
  - maxgent/client/webapp/src/components/chat/chat-input-view.tsx
  - maxgent/client/webapp/src/components/chat/chat-drop-overlay.tsx
  - maxgent/client/webapp/src/hooks/use-chat-composer.ts
  - maxgent/client/webapp/src/hooks/use-chat-drag-drop.ts
  - maxgent/client/webapp/src/lib/send-button-state.ts
  - maxgent/client/webapp/src/lib/paste-large-text.ts
  - maxgent/client/webapp/src/lib/process-attachment-files.ts
  - maxgent/client/webapp/src/lib/image-resize.ts
  - maxgent/client/webapp/src/lib/pending-outbound-message.ts
  - maxgent/client/webapp/src/hooks/use-voice-recorder.ts
  - maxgent/client/webapp/src/lib/voice-cap.ts
  - maxgent/client/webapp/src/hooks/prepare-voice-attachments.ts
  - maxgent/client/webapp/src/api/maxclaw-adapter.ts
  - maxgent/client/webapp/src/lib/config.ts
  - maxgent/client/webapp/src/i18n/locales/en.json
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Chat Composer Controls

## Direct Answer

The chat composer is the main input surface in `/chat`. It supports typed text,
file attachment, workspace file mentions, slash commands, model tier selection,
send, stop, and, when enabled for the environment, voice recording.

## Controls

| Control | Behavior |
|---|---|
| Textarea | Draft input. It keeps unsent text in pending chat intent storage. |
| Attach button | Opens a file picker and starts eager upload. Send stays blocked while uploads are in flight or failed. |
| Drag/drop | Shows **Drop files to attach** over the valid chat panel and attaches dropped files. Text/link drags are ignored. |
| Clipboard paste | Pasted files/images attach as files. Large plain text can become a generated text-file attachment. |
| `@` mention | Inserts available workspace file mentions when the picker has entries. Mentioned files are sent as workspace references. |
| `/` button or `/` prefix | Opens the command menu when commands are enabled. This is not the Skills panel. |
| Tier selector | Lets the user choose the user-facing model tier. |
| Send button | Sends when there is text or at least one ready attachment/reference. |
| Stop button | Appears for an active stream with an empty composer and abort permission. It requests cancellation of the current response. |
| Voice button | Appears only when voice recording is enabled for the current environment. It records microphone audio and adds it as a voice attachment. |

## Send State Rules

- Disabled or unavailable workspace state blocks sending.
- While the sandbox/session is not ready, the send button shows a loading state
  with "Waiting for sandbox".
- Uploading attachments block sending until they finish.
- Failed attachment chips block sending until removed.
- Empty composer normally blocks sending.
- Empty composer during an abortable stream switches the send action to stop.
- Streaming plus plain text sends supplemental context to the active session.
- Streaming plus attachments queues the attachment-bearing message until the
  current response finishes.
- Queue write failure keeps the draft/attachments in the composer and shows a
  queue failure notice.
- After a successful send, there is a short grace period so a mobile double tap
  does not immediately stop the new stream.

## Paste And Attachment Rules

- Chat upload limit is 50 MB.
- Plain text paste under 5 KB stays native.
- Plain text paste from 5 KB through 50 MB becomes a generated
  `pasted-YYYYMMDD-HHMMSS-ms.txt` attachment.
- Plain text paste over 50 MB stays native instead of becoming an uploadable
  attachment.
- If a generated pasted-text attachment upload fails, MoClaw removes that chip
  and restores the pasted text to the draft when possible.
- Pasted files/images and file-picker attachments share the same upload
  pipeline.
- JPEG, PNG, and WebP image attachments may be downscaled client-side before
  upload.
- Reference attachments from `@` mentions, **Quote in chat**, or **Prompt with
  file** are treated as existing workspace references, not new local uploads.

## Keyboard Rules

- The send-key preference can be `Enter` or `Cmd/Ctrl+Enter`.
- In `Enter` mode, `Enter` sends and `Shift+Enter` inserts a newline.
- In `Cmd/Ctrl+Enter` mode, plain `Enter` inserts a newline and `Cmd+Enter` or
  `Ctrl+Enter` sends.
- Mention picker and slash command selection intercept `Enter` before the send
  preference applies.
- During IME composition, `Enter` is guarded so selecting a composed character
  does not accidentally send.

## Voice Rules

- Voice recording is controlled by the current environment's voice runtime gate.
  It can be hidden even when the browser itself supports recording.
- Recording requires browser microphone support and user permission.
- The minimum accepted recording duration is 1 second.
- The current maximum recording duration is 3 minutes; MoClaw auto-stops at the
  cap and shows a notice.
- Permission denied and unsupported browser errors show a dialog.
- Capture failure, too-short recording, max duration, and transcription failure
  show composer notices.
- Recorded audio is added as an attachment and uses the same upload pipeline as
  other chat files.
- Before sending, MoClaw tries to transcribe recorded audio through the file
  transcription endpoint. The adapter then sends a `<voice-message>` metadata
  tag containing file id, duration, and transcript.
- Transcription failure is non-fatal: the message still sends, but the transcript
  body is empty and the user sees a notice that the audio could not be
  transcribed.
- User-picked audio files without recorder duration are treated as generic file
  attachments, not voice bubbles.

## Do Not Say

- Do not promise the voice button appears in every environment or browser.
- Do not say voice recording can access the microphone without browser
  permission.
- Do not claim that audio over 3 minutes is currently accepted.
- Do not say transcription failure prevents the message from being sent.
- Do not say typing `/<skill-name>` runs a skill.
- Do not say every pasted text becomes a file.
- Do not say workspace references upload the file again.
- Do not say attachment-bearing messages are sent immediately while a response
  is already streaming.

## Related Cards

- `moclaw.reference.skills_and_slash_commands`
- `moclaw.reference.chat_conversations_and_history`
- `moclaw.reference.message_display_and_actions`
- `moclaw.reference.model_tiers`
- `moclaw.how_to.upload_or_reference_file`
- `moclaw.troubleshooting.voice_recording_not_working`
- `moclaw.troubleshooting.chat_file_upload_or_attachment_failed`
