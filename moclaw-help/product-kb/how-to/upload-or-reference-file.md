---
id: moclaw.how_to.upload_or_reference_file
title: Upload Or Reference A File
type: how_to
product_area: workspace
audience: user
status: verified
owner: product
last_reviewed_at: 2026-07-23
source_paths:
  - maxgent/client/webapp/src/modules/chat/composer/hooks/use-chat-composer.ts
  - maxgent/client/webapp/src/modules/chat/composer/hooks/use-chat-composer.test.ts
  - maxgent/client/webapp/src/modules/chat/composer/hooks/use-chat-drag-drop.ts
  - maxgent/client/webapp/src/modules/chat/composer/components/chat-drop-overlay.tsx
  - maxgent/client/webapp/src/lib/paste-large-text.ts
  - maxgent/client/webapp/src/lib/extract-paste-files.ts
  - maxgent/client/webapp/src/lib/process-attachment-files.ts
  - maxgent/client/webapp/src/lib/image-resize.ts
  - maxgent/client/webapp/src/lib/pending-outbound-message.ts
  - maxgent/client/webapp/src/modules/chat/composer/store/reference-attachment.ts
  - maxgent/client/webapp/src/lib/file-limits.ts
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Upload Or Reference A File

## Direct Answer

MoClaw supports two file paths in chat:

- Upload a new local file from the chat composer.
- Reference an existing workspace file or Artifact with an `@` mention when it
  appears in the composer picker.

Uploaded files are sent into the current session. Workspace references point to
files that already exist in the agent workspace and are treated as already
available to the session.

## Before You Start

- The current chat upload limit is 50 MB.
- A workspace reference is not the same as uploading a new file.
- Referenced workspace files may appear as inline `@filename` or `@path` tokens
  in the user message.
- Plain text paste below 5 KB stays native. Plain text paste from 5 KB through
  50 MB becomes a generated `pasted-...txt` attachment.
- Drag/drop attaches real files only when the drag is over the valid chat panel
  drop target.

## Steps

1. To upload a local file, use the attach control in the chat composer and
   choose the file, drag a file onto the chat panel, or paste a file/image from
   the clipboard.
2. Wait until the file chip finishes uploading.
3. Add the prompt text and send the message.
4. To reference an existing file, type `@` in the chat composer.
5. Choose an available workspace file or Artifact from the picker.
6. Send a message that says what MoClaw should do with it.

## If You Cannot See It

- If upload fails immediately, check whether the file is larger than 50 MB.
- If the send button is blocked, wait for active uploads to finish or remove a
  failed upload chip.
- If a large pasted-text upload fails, the composer can restore the pasted text
  into the draft so the user does not lose it.
- If drag/drop does nothing, confirm the user dragged real files over the chat
  panel rather than text/links or a sidebar area.
- If a published file cannot be referenced, refresh **Artifacts** and confirm
  it is still visible. The current Artifacts page does not expose **Prompt with
  file**, **Copy link**, or the broader **All files** tree.
- If a prompt with files is sent while a response is streaming, MoClaw may queue
  the attachment-bearing message until the active response finishes.
- If queueing fails, the message should remain in the composer; ask the user to
  retry after the active response is done.

## Do Not Say

- Do not say that referencing a workspace file uploads it again.
- Do not say that all pasted text becomes a file.
- Do not expose raw internal sandbox paths unless the user needs a copied
  workspace reference.
- Do not promise that every referenced file can be previewed or downloaded.
- Do not tell users that files over 50 MB can be uploaded through chat.
- Do not say attachment-bearing messages send immediately during an active
  stream.
- Do not ask the user to paste file contents, signed URLs, tokens, passwords, or
  full raw logs into support chat.

## Related Cards

- `moclaw.how_to.use_artifacts`
- `moclaw.reference.file_preview_limits`
- `moclaw.concepts.workspace_file_and_artifact`
- `moclaw.troubleshooting.chat_file_upload_or_attachment_failed`
