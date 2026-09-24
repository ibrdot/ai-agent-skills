---
id: help.workspace.preview_generated_files
title: Preview Generated Files
audience: user
status: verified
source_cards:
  - moclaw.reference.file_preview_renderers
  - moclaw.reference.file_preview_limits
  - moclaw.troubleshooting.file_cannot_preview_or_download
  - moclaw.how_to.use_artifacts
last_reviewed_at: 2026-07-23
---

# Preview Generated Files

Open generated files from **Artifacts** or a file card in Chat. Artifact files
open in their source Session's Dock. MoClaw uses the best available viewer for
the file type.

## What Can Preview

- Images, video, and audio can open in a media viewer when the file is
  available.
- Markdown, text, code, and many source files can open as readable content.
- PDFs can preview when they are within the current PDF preview limit.
- Word, PowerPoint, and similar documents may show a converted preview.
- Spreadsheets can preview when they are small enough for the spreadsheet
  viewer.
- `.html`, `.htm`, `.jsx`, and `.tsx` files can open a live preview when the
  source is compatible.
- `.mmd` and `.mermaid` files can open a diagram preview with source, zoom, and
  export controls.

## If A Preview Is Preparing Or Failed

If you see **Preparing document preview**, wait briefly and retry. You can still
use **Download original** while the preview is being prepared.

If you see **Couldn't generate a preview** or **No preview available**, the
preview renderer could not show that file. That does not automatically mean the
file is gone. Try **Download** or **Download original** when available, refresh
**Artifacts**, or reopen the file from Chat.

## Code Preview Notes

The live preview is meant for simple generated HTML or React component files.
For React previews, the file needs a default export and can only use the
preview libraries currently bundled by MoClaw. If the preview shows a compile
or runtime error, ask MoClaw to fix the generated file or simplify it.

The preview is not a full production hosting environment and should not be
treated as proof that every dependency, backend API, or external package is
available.

## Mermaid Diagram Export

For `.mmd` or `.mermaid` files:

1. Open the file.
2. Use the eye/source buttons to switch between diagram and source.
3. Use zoom controls if the diagram is too large or small.
4. Use the download menu to export the Mermaid source, SVG, or PNG.

The current Artifacts page does not expose **Copy link** or **Prompt with file**.

## When To Contact Support

Send support the file name, visible file path if shown, file size, approximate
time, and exact preview error. If the UI shows a Reference ID, include that
too.

Do not send signed URLs, API keys, OAuth tokens, passwords, or full raw logs.

## Related Articles

- `workspace/files-and-artifacts.md`
- `workspace/upload-or-reference-files.md`
- `troubleshooting/common-errors.md`
