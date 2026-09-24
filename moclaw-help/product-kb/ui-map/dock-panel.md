---
id: moclaw.ui.dock_panel
title: Dock Panel
type: ui_map
product_area: workspace
audience: user
status: verified
owner: product
last_reviewed_at: 2026-07-23
source_paths:
  - maxgent/client/webapp/src/modules/app-shell/components/app-shell.tsx
  - maxgent/client/webapp/src/modules/app-shell/components/dock-panel.tsx
  - maxgent/client/webapp/src/modules/app-shell/components/dock-panel-view.tsx
  - maxgent/client/webapp/src/stores/dock-store.ts
  - maxgent/client/webapp/src/lib/constants.ts
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Dock Panel

## Direct Answer

The Dock Panel is the file-work surface attached to a Session. It hosts file
previews as tabs. New Chat does not show a Dock. VNC is a separate global
floating window and never appears in the Dock.

## When It Appears

- On wide screens, the Dock appears as the right-side panel.
- On narrow screens, the same Dock workspace becomes a full-screen overlay.
- Changing presentation does not close tabs or replace them with a separate
  mobile file viewer.
- The Dock is hidden when the current Session has no open items.

## What It Contains

| Item Type       | Meaning                                                           |
| --------------- | ----------------------------------------------------------------- |
| `file` | File preview from workspace files, artifacts, or chat file cards. |

## User-Facing Behavior

- Multiple docked items appear as tabs.
- Tabs can be selected or closed.
- Overflowing tabs can be scrolled horizontally.
- The panel-level control collapses the Dock without closing its tabs.
- Each tab has its own close action.
- Each Session keeps its own Dock workspace. Switching pages can hide the
  current Dock, but it does not destroy that Session's tabs.
- Opening an Artifact file targets its source Session's Dock, then navigates to
  that Session.
- File dock content can expose copy/download actions depending on file type.

## Do Not Say

- Do not say VNC or the AI Cloud Computer viewer is a Dock tab.
- Do not say collapsing the Dock closes all tabs.
- Do not say narrow screens use a separate Mobile File Viewer.
- Do not describe Dock tabs as global across all Sessions.

## Related Cards

- `moclaw.ui.chat_page`
- `moclaw.ui.workspace_sidebar`
- `moclaw.ui.mobile_layout`
- `moclaw.how_to.use_artifacts`
