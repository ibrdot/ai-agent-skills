---
id: moclaw.reference.file_preview_limits
title: File Preview And Transfer Limits
type: reference
product_area: workspace
audience: support
status: verified
owner: product
last_reviewed_at: 2026-07-23
source_paths:
  - maxgent/client/webapp/src/lib/file-limits.ts
  - maxgent/client/webapp/src/lib/file-download.ts
  - maxgent/client/webapp/src/modules/artifacts/preview/lib/file-viewer-preview.ts
  - maxgent/client/webapp/src/modules/artifacts/preview/components/file-viewer-view.tsx
  - maxgent/client/webapp/src/modules/artifacts/preview/components/pdf-preview.tsx
  - maxgent/client/webapp/src/lib/mermaid-render.ts
  - maxgent/client/webapp/src/modules/artifacts/list/components/artifacts-page-view.tsx
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# File Preview And Transfer Limits

## Direct Answer

Current frontend file transfer limits are 50 MB for chat upload and Workspace
download. Preview has additional type-specific limits, so a file can be within
the download limit but still too large or unsuitable to preview.

## Current Limits

| Action | Limit | Source |
|---|---:|---|
| Chat upload | 50 MB | `CHAT_UPLOAD_LIMIT_BYTES` |
| Workspace download | 50 MB | `WORKSPACE_DOWNLOAD_LIMIT_BYTES` |
| PDF preview | 20 MB | `PDF_MAX_BYTES` in file viewer |
| Spreadsheet preview | 5 MB | `SPREADSHEET_PREVIEW_MAX_BYTES` |
| Live code preview | 500,000 bytes | file viewer preview gate |
| Mermaid source render | 50,000 characters | `MAX_MERMAID_LENGTH` |
| Spreadsheet visible rows | 500 rows | `MAX_ROWS` in spreadsheet preview |

## Support Implications

- If a file appears but download is disabled, check file size first.
- If a user asks why upload/download fails, cite the 50 MB transfer limit.
- Preview availability can still vary by file type, renderer, conversion state,
  source syntax, and safe URL/content availability.
- Load `moclaw.reference.file_preview_renderers` when the user asks why a
  specific preview type, live code preview, document conversion, or Mermaid
  export did not work.

## Do Not Say

- Do not say every file under 50 MB can be previewed.
- Do not say files over 50 MB can be downloaded from the workspace file viewer unless product
  changes the limit.
- Do not collapse preview limits and download limits into one rule.

## Related Cards

- `moclaw.how_to.use_artifacts`
- `moclaw.concepts.workspace_file_and_artifact`
- `moclaw.reference.message_display_and_actions`
- `moclaw.reference.file_preview_renderers`
