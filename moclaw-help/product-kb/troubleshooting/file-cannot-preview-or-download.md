---
id: moclaw.troubleshooting.file_cannot_preview_or_download
title: File Cannot Preview Or Download
type: troubleshooting
product_area: workspace
audience: user
status: verified
owner: product
last_reviewed_at: 2026-07-23
source_paths:
  - maxgent/client/webapp/src/modules/artifacts/preview/components/document-preview-state.ts
  - maxgent/client/webapp/src/modules/artifacts/preview/components/document-preview.tsx
  - maxgent/client/webapp/src/modules/artifacts/preview/components/pdf-preview.tsx
  - maxgent/client/webapp/src/modules/artifacts/preview/components/spreadsheet-preview.tsx
  - maxgent/client/webapp/src/modules/artifacts/preview/components/code-preview-renderer.tsx
  - maxgent/client/webapp/src/modules/artifacts/preview/components/preview-shared.tsx
  - maxgent/client/webapp/src/modules/artifacts/preview/components/file-viewer-view.tsx
  - maxgent/client/webapp/src/lib/file-types.ts
  - maxgent/client/webapp/src/modules/artifacts/preview/lib/file-viewer-preview.ts
  - maxgent/client/webapp/src/lib/file-limits.ts
  - maxgent/client/webapp/src/lib/preview-compile.ts
  - maxgent/client/webapp/src/lib/mermaid-render.ts
  - maxgent/client/webapp/src/modules/artifacts/list/components/artifacts-page-view.tsx
  - maxgent/client/webapp/src/i18n/locales/en.json
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# File Cannot Preview Or Download

## Symptom

The user can see a file or artifact, but preview is unavailable, document preview
fails, binary content cannot preview, or download is disabled/fails.

## Likely Causes

- The file type is not previewable in the current viewer.
- A document preview is still preparing or failed to generate.
- The file is binary and has no text preview.
- The file exceeds the Workspace download limit.
- The file exceeds a type-specific preview limit, such as PDF, spreadsheet,
  live-code, or Mermaid size limits.
- A live code preview has an unsupported dependency, no default React export,
  compile error, runtime error, or unsupported source extension.
- A Mermaid file has invalid syntax or is too large to render.
- Spreadsheet preview may be too large for the spreadsheet viewer.
- The file reference is stale or no longer available in the workspace.

## Recovery Steps

1. If the file is still preparing, wait briefly and retry opening it.
2. If the preview failed but **Download original** is available, download the
   original file.
3. If download is disabled, check whether the file is larger than 50 MB.
4. If the file is a spreadsheet and preview fails, try downloading the original
   file.
5. If a generated `.jsx` or `.tsx` preview fails, ask MoClaw to fix the source
   so it has a default React export and only uses supported preview libraries.
6. If a Mermaid file fails, switch to source view and check syntax or file size.
7. If the file is binary, explain that preview may not be available and use
   download when supported.
8. Refresh Artifacts or the file manager and reopen the file from the current
   list.
9. If download still fails, collect the file name, workspace path if visible,
   file size, exact visible preview/download error, Reference ID if shown, and
   approximate time.

## Escalate When

- A file under the documented download limit repeatedly fails to download.
- Document preview stays pending or failed across refreshes.
- The file appears in the UI but both preview and download are unavailable
  without a clear size/type reason.

## Do Not Say

- Do not promise every file under 50 MB can be previewed.
- Do not promise files over 50 MB can be downloaded from the workspace file viewer.
- Do not call a preview conversion failure data loss.
- Do not say every JavaScript, TypeScript, Python, or arbitrary app project can
  run in MoClaw's live preview.
- Do not call **Copy link** a public sharing URL.
- Do not expose internal signed URLs or sandbox paths unless needed for support
  escalation.

## Related Cards

- `moclaw.reference.file_preview_limits`
- `moclaw.reference.file_preview_renderers`
- `moclaw.reference.message_display_and_actions`
- `moclaw.how_to.use_artifacts`
- `moclaw.how_to.upload_or_reference_file`
