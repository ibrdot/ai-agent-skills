---
id: moclaw.reference.file_preview_renderers
title: File Preview Renderers And Export Actions
type: reference
product_area: workspace
audience: support
status: verified
owner: product
last_reviewed_at: 2026-07-23
source_paths:
  - maxgent/client/webapp/src/modules/artifacts/preview/components/file-viewer-view.tsx
  - maxgent/client/webapp/src/modules/artifacts/preview/components/document-preview.tsx
  - maxgent/client/webapp/src/modules/artifacts/preview/components/document-preview-state.ts
  - maxgent/client/webapp/src/modules/artifacts/preview/components/pdf-preview.tsx
  - maxgent/client/webapp/src/modules/artifacts/preview/components/spreadsheet-preview.tsx
  - maxgent/client/webapp/src/modules/artifacts/preview/components/code-preview-renderer.tsx
  - maxgent/client/webapp/src/lib/preview-compile.ts
  - maxgent/client/webapp/src/lib/file-types.ts
  - maxgent/client/webapp/src/modules/artifacts/preview/lib/file-viewer-preview.ts
  - maxgent/client/webapp/src/lib/mermaid-render.ts
  - maxgent/client/webapp/src/lib/mermaid-export.ts
  - maxgent/client/webapp/src/modules/artifacts/preview/components/blocks/viewer-actions.tsx
  - maxgent/client/webapp/src/modules/artifacts/list/components/artifacts-page.tsx
  - maxgent/client/webapp/src/i18n/locales/en.json
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# File Preview Renderers And Export Actions

## Direct Answer

MoClaw can preview many workspace files and artifacts, but preview support
depends on file type, file size, available content, and whether a converted
preview is ready. Preview failure does not by itself mean the original file is
lost; use **Download**, **Download original**, refresh the file list, or collect
safe file details for support.

## Viewer Behavior By Type

| File Type | Current Behavior |
|---|---|
| Images, video, audio | Opens media in the file viewer when a safe URL or content is available. |
| PDF | PDF viewer renders PDFs up to the preview limit; larger PDFs show a download fallback. |
| Documents | `.docx`, `.pptx`, `.odt`, `.odp`, `.doc`, and `.ppt` use a file-id preview conversion flow. |
| Spreadsheets | `.xlsx`, `.xls`, `.csv`, and `.tsv` preview when a workbook source is available and the file is within the spreadsheet preview limit. |
| HTML / React preview | `.html` and `.htm` pass through as HTML; `.jsx` and `.tsx` compile in the browser as a React component preview. |
| Mermaid | `.mmd` and `.mermaid` open a Mermaid viewer with preview/source modes, zoom, fit-to-view, and export actions. |
| Markdown/text/source | Rendered as markdown, text, or source when file content is available and printable. |
| Binary/unknown | Shows **No preview available** and offers download when supported. |

## Current Preview Limits

| Surface | Limit |
|---|---:|
| Workspace download transfer | 50 MB |
| PDF preview | 20 MB |
| Spreadsheet preview | 5 MB |
| Code live preview content | 500,000 bytes |
| Mermaid source rendering | 50,000 characters |
| Spreadsheet visible rows | 500 rows at a time |

The 50 MB transfer limit is separate from preview limits. A file can be too
large to preview but still downloadable if it is within the transfer limit.

## Document Preview States

| Visible Copy | Meaning |
|---|---|
| **Preparing document preview** | Conversion is pending or still loading. The UI still offers **Download original**. |
| **Preview version. Original file available for download** | MoClaw is showing a converted preview, not replacing the original file. |
| **Couldn't generate a preview** | Conversion or PDF rendering failed. The user should use **Download original** when available. |

## Code Preview Rules

- Live code preview is only verified for `.html`, `.htm`, `.jsx`, and `.tsx`.
- `.jsx` and `.tsx` must export a default React component.
- The browser-side compiler only supports whitelisted preview libraries:
  `react`, `react-dom`, `react-dom/client`, `recharts`, and `lucide-react`.
- Unknown imports, missing default exports, empty source, compile errors, and
  runtime errors can make the preview show an error even when the source file is
  still available.
- Do not promise backend execution, external package installation, server-side
  APIs, or arbitrary browser permissions inside the live preview.

## Mermaid Rules

- Mermaid files can toggle between **preview** and **source**.
- The preview has zoom in, zoom out, and fit-to-view controls.
- The download menu can export the source `.mmd`, standalone `.svg`, or `.png`.
- Invalid Mermaid syntax or source above the Mermaid limit can show a render
  error. That is a preview/rendering error, not proof of file loss.

## Workspace Reference Boundary

When a workspace surface exposes **Copy link**, it copies an `@...` workspace
reference token for chat reuse. It is not a public sharing URL. The current
Artifacts page itself only exposes file open and download.

## Support Implications

- If preview fails but download works, tell the user to download the original
  or ask MoClaw to convert/split the file.
- If a document preview is still preparing, wait briefly and retry before
  escalating.
- If a generated React preview fails, ask for the filename, visible preview
  error, approximate time, and whether the file is `.jsx` or `.tsx`.
- If Mermaid export is missing, confirm the file extension is `.mmd` or
  `.mermaid` and the diagram is in preview mode.
- If a file shows a Reference ID or publish trace, collect that value without
  asking for signed URLs, raw storage URLs, secrets, or full logs.

## Do Not Say

- Do not say every file can be previewed.
- Do not say preview failure means the original file was deleted.
- Do not say **Copy link** creates a public URL.
- Do not say all JavaScript, TypeScript, Python, or arbitrary app projects can
  run in the preview.
- Do not promise files over the Workspace download limit can be downloaded from
  the `/chat` UI.

## Related Cards

- `moclaw.reference.file_preview_limits`
- `moclaw.troubleshooting.file_cannot_preview_or_download`
- `moclaw.how_to.use_artifacts`
