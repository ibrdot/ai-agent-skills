---
id: help.workspace.upload_or_reference_files
title: Upload Or Reference Files
audience: user
status: verified
source_cards:
  - moclaw.how_to.upload_or_reference_file
  - moclaw.troubleshooting.chat_file_upload_or_attachment_failed
  - moclaw.how_to.use_artifacts
  - moclaw.concepts.workspace_file_and_artifact
last_reviewed_at: 2026-07-23
---

# Upload Or Reference Files

There are two ways to give MoClaw files:

- Upload a new local file from the chat composer.
- Reference an existing file with `@` when it appears in the composer picker.

Uploading and referencing are different. Uploading sends a local file into the
current session. Referencing points MoClaw to a file that already exists in the
workspace.

## Upload A Local File

1. Open `/chat`.
2. Use the attachment control in the chat composer, drag a file onto the chat
   panel, or paste an image/file from your clipboard.
3. Choose or drop the file.
4. Wait for the upload chip to finish.
5. Add your prompt and send.

If upload fails, check whether the file is larger than the current chat upload
limit.

## Paste Text Or Files

- Small plain-text paste behaves like normal browser paste.
- Large plain-text paste may become a generated `pasted-...txt` attachment so
  MoClaw can handle it as a file.
- If that pasted-text upload fails, MoClaw restores the original text to the
  editor when possible.
- Pasted images or files attach as files.

Do not paste private secrets, tokens, passwords, or full logs into support chat.

## Reference A Workspace File

1. Type `@` in the composer.
2. Choose an available file from the picker.
3. Send a message that tells MoClaw what to do with it.

The current Artifacts page does not expose **Prompt with file**, **Copy link**,
or the broader **All files** workspace tree.

If MoClaw is already responding, a message with attached files or workspace
references may be queued until the current response finishes.

## Good Prompts

- "Summarize @report.pdf and list the key risks."
- "Use this spreadsheet and create a clean weekly report."
- "Open this artifact and make a revised version with shorter copy."

## Related Articles

- `workspace/files-and-artifacts.md`
- `troubleshooting/common-errors.md`
