---
id: moclaw.how_to.use_artifacts
title: Use Artifacts
type: how_to
product_area: workspace
audience: user
status: verified
owner: product
last_reviewed_at: 2026-07-23
source_paths:
  - maxgent/client/webapp/src/routes/_authenticated/chat.artifacts.tsx
  - maxgent/client/webapp/src/modules/artifacts/list/components/artifacts-page.tsx
  - maxgent/client/webapp/src/modules/artifacts/list/components/artifacts-page-view.tsx
  - maxgent/client/webapp/src/modules/artifacts/list/hooks/use-artifact-file-actions.ts
  - maxgent/client/webapp/src/lib/file-limits.ts
  - maxgent/client/webapp/src/lib/file-download.ts
  - maxgent/client/webapp/src/i18n/locales/en.json
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Use Artifacts

## Direct Answer

Open **Artifacts** from the left navigation. The standalone page groups
published files by their source Session. Users can refresh or paginate the
list, open a source Session, preview a file in that Session's Dock, or download
supported files.

## Before You Start

- Artifacts are files produced or surfaced by the agent workspace.
- The list is account-wide and grouped by source Session.
- The list can load more results.
- Large files can be shown in the list but blocked from download.
- The current Artifacts row menu only exposes **Download**.

## Steps

1. Open **Artifacts** from the left navigation.
2. Click refresh if the list looks stale.
3. Select a Session group title to return to that Session.
4. Select a file to open it in its source Session's Dock. MoClaw navigates to
   that Session after preparing the preview.
5. Use the file row action menu to download the file when available.

## If You Cannot See It

- If the page says no artifacts, the account may not have published files yet.
- If refresh fails, retry from the Artifacts page.
- If download is disabled, check whether the file exceeds the transfer limit.
- If preview fails, use the file-preview troubleshooting card before treating
  the file as missing.

## Do Not Say

- Do not call every workspace file an artifact.
- Do not promise download for files over the current file transfer limit.
- Do not tell users to expand Artifacts inside Chat; it is a standalone page.
- Do not promise **Prompt with file**, **Copy link**, or **All files** actions
  on the current Artifacts page.
- Do not say the Artifacts page itself contains the file preview.

## Related Cards

- `moclaw.concepts.workspace_file_and_artifact`
- `moclaw.reference.file_preview_limits`
- `moclaw.reference.file_preview_renderers`
