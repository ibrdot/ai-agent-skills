---
id: moclaw.troubleshooting.chat_file_upload_or_attachment_failed
title: Chat File Upload Or Attachment Failed
type: troubleshooting
product_area: chat
audience: support
status: verified
last_reviewed_at: 2026-07-23
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Chat File Upload Or Attachment Failed

## Symptom

The user cannot attach a file, drag-and-drop does not attach, pasted content
turns into a file, a pasted-text upload fails and restores text to the editor,
the send button is blocked by an attachment chip, or a message with files is
queued while MoClaw is already responding.

## Key Rules

- The chat upload limit is 50 MB.
- The attach button, paste-file path, and drag-and-drop file path share the same
  upload pipeline.
- Drag-and-drop only attaches drags that carry `Files`; normal text or link
  drags are ignored.
- Pasted files and pasted images attach as files.
- Plain text paste below 5 KB uses the browser's native paste behavior.
- Plain text paste from 5 KB through 50 MB is converted into a generated
  `pasted-YYYYMMDD-HHMMSS-ms.txt` file and uploaded as an attachment.
- Plain text paste above 50 MB uses native paste behavior rather than converting
  to an uploadable attachment.
- JPEG, PNG, and WebP images may be downscaled before upload when the image long
  edge is above the current client-side resize threshold.
- Workspace references are already-available reference attachments and should
  not be described as new uploads.
- If the current response is streaming, plain text can be sent as supplemental
  context, but messages with attachments are queued until the active response
  finishes.

## Visible States

| Visible State | Support Meaning |
|---|---|
| **Drop files to attach** | The chat panel detected a file drag over the valid drop target. |
| Upload chip with progress | Upload is in flight; sending is blocked until it finishes. |
| Failed upload chip | Sending is blocked until the failed chip is removed or upload is retried through a new attach. |
| **Upload failed - your pasted text has been restored to the editor** | A large pasted-text attachment failed, so MoClaw removed the generated file chip and put the original text back in the draft. |
| **Queued this message and will send it as soon as the current response finishes.** | A file/reference message was accepted while the model was streaming and is waiting for the active response to finish. |
| **Could not queue this message. It is still in the composer.** | The queue write failed; the draft and attachments should remain in the composer. |

## Recovery Steps

1. If a local upload fails immediately, check whether the file is over 50 MB.
2. If a failed upload chip blocks Send, remove the chip and attach a smaller
   file or retry the attach action.
3. If a large pasted text upload fails, use the restored editor text, split the
   text, or save it as a smaller file before attaching.
4. If drag-and-drop does nothing, use the attach button and confirm the drag was
   a real file drag over the chat panel, not a text/link drag or a drop over the
   sidebar.
5. If image upload triggers a generic provider/image issue, ask the user to
   retry with the processed image, a smaller image, or a non-image file.
6. If a message with attachments is queued during streaming, wait for the
   current response to finish. If the queue failure notice appears, send it
   again after the current response is done.
7. If referencing an Artifact does not work, refresh **Artifacts** and confirm
   the published file is still visible. The current Artifacts page does not
   expose the broader **All files** workspace tree.

## Escalate When

- A file under 50 MB repeatedly fails through both attach button and drag/drop.
- Large pasted text repeatedly fails and is restored, even after splitting.
- Queue failure repeats while browser storage is available.
- A referenced workspace file is visible but cannot be sent or resolved.

## Safe Diagnostic Fields

- Account email.
- Approximate time and timezone.
- File name, file size, and file type.
- Whether the user used attach, drag/drop, paste-file, large text paste, or an
  `@` mention.
- Exact visible notice/error copy.
- Whether a response was streaming when the user tried to send.

Do not ask for file contents, signed URLs, raw storage URLs, API keys, OAuth
tokens, passwords, cookies, or full raw logs.

## Do Not Say

- Do not say all pasted text becomes a file.
- Do not say files over 50 MB can be uploaded through chat.
- Do not say workspace references are uploaded again.
- Do not say queued attachment messages are sent immediately while the current
  response is still streaming.
- Do not tell users to paste private file contents into support chat.

## Related Cards

- `moclaw.how_to.upload_or_reference_file`
- `moclaw.reference.chat_composer_controls`
- `moclaw.reference.file_preview_limits`
