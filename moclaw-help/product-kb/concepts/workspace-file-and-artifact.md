---
id: moclaw.concepts.workspace_file_and_artifact
title: Workspace Files And Artifacts
type: concept
product_area: workspace
audience: user
status: verified
owner: product
last_reviewed_at: 2026-07-23
source_paths:
  - maxgent/client/webapp/CONTEXT.md
  - maxgent/client/webapp/src/modules/artifacts/list/components/artifacts-page.tsx
  - maxgent/client/webapp/src/modules/app-shell/components/dock-panel.tsx
  - maxgent/client/webapp/src/i18n/locales/en.json
applies_to:
  plans: [trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Workspace Files And Artifacts

## Direct Answer

A Workspace File is a current file in the AI Cloud Computer workspace and can
change as the task continues. An Artifact is a stable file snapshot that MoClaw
explicitly delivers for preview, download, sharing, or later viewing.

## What Users Usually Mean

When users say "my file," they may mean one of three things:

- a file uploaded or referenced in chat;
- a current file in the AI Cloud Computer workspace;
- an Artifact produced by the AI.

Identify which one they mean before answering with the entry point and limits.

## UI Entry Points

- left navigation **Artifacts** page: view delivered artifacts grouped by source
  Session.
- Session Dock: open and preview files.
- File cards inside chat messages: open files referenced by the AI in messages.

The current Artifacts page does not expose an **All files** entry for browsing
the broader workspace tree.

## Boundaries

- Workspace Files depend on current workspace/sandbox availability.
- Artifacts are stable snapshots, but access URLs may need to be resolved or
  generated again.
- Oversized files, sandbox unavailability, and artifact publish failure can all
  prevent preview or download.

## Related Cards

- `moclaw.ui.workspace_sidebar`
- `moclaw.troubleshooting.workspace_unavailable` (planned)
