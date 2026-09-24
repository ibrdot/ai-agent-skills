---
id: moclaw.ui.mobile_layout
title: Mobile Layout
type: ui_map
product_area: workspace
audience: user
status: verified
owner: product
last_reviewed_at: 2026-07-23
source_paths:
  - maxgent/client/webapp/src/modules/app-shell/components/app-shell.tsx
  - maxgent/client/webapp/src/components/layout/app-layout-view.tsx
  - maxgent/client/webapp/src/modules/chat/message-list/components/conversation-layout-view.tsx
  - maxgent/client/webapp/src/modules/app-shell/components/dock-panel.tsx
  - maxgent/client/webapp/src/stores/ui-store.ts
  - maxgent/client/webapp/src/stores/dock-store.ts
  - maxgent/client/webapp/src/lib/constants.ts
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web_mobile]
---

# Mobile Layout

## Direct Answer

On mobile/narrow viewports, MoClaw keeps the same App Shell state but changes
how surfaces are presented. The sidebar becomes an overlay, the chat composer
uses mobile viewport/safe-area handling, and an active Session Dock fills the
screen without creating a separate file viewer.

## Breakpoints And State

- `MOBILE_BREAKPOINT` is 768 px.
- `isViewportMobile` is derived from `max-width: 768px`.
- Dock width and overlay behavior are controlled separately from the Chat
  mobile breakpoint.
- Opening or closing the narrow-screen Dock does not destroy its tabs.

## Surface Map

| Surface                    | Mobile/Narrow Behavior                                                 |
| -------------------------- | ---------------------------------------------------------------------- |
| Chat composer              | Anchored to the bottom using mobile viewport styling.                  |
| left sidebar               | Not a fixed wide desktop sidebar in the same way as desktop.           |
| File preview               | Opens in the current Session Dock; New Chat does not show a Dock.      |
| Dock panel                 | Uses a full-screen overlay when the side-by-side layout is too narrow. |
| Checkout success / pricing | Uses `MobileSheet` on mobile viewports.                                |

## Support Guidance

When a user says a button or panel is missing, ask whether they are on mobile,
tablet, or desktop width. The same feature may exist but be presented as a sheet,
overlay, or collapsed surface instead of a side panel.

## Do Not Say

- Do not use desktop-only spatial instructions for mobile users.
- Do not tell users that mobile opens a separate Mobile File Viewer.
- Do not imply that changing to the full-screen Dock closes or reloads tabs.

## Related Cards

- `moclaw.ui.chat_page`
- `moclaw.ui.workspace_sidebar`
- `moclaw.ui.dock_panel`
