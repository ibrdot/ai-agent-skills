---
id: moclaw.reference.ai_cloud_computer_viewer
title: AI Cloud Computer Viewer
type: reference
product_area: workspace
audience: support
status: verified
owner: product
last_reviewed_at: 2026-07-30
source_paths:
  - maxgent/client/webapp/src/modules/runtime/computers/components/computers-page-view.tsx
  - maxgent/client/webapp/src/modules/runtime/computers/components/computers-page.tsx
  - maxgent/client/webapp/src/modules/runtime/computers/components/cloud-computer-header-action-view.tsx
  - maxgent/client/webapp/src/modules/runtime/computers/components/cloud-computer-header-action.tsx
  - maxgent/client/webapp/src/modules/runtime/computers/hooks/use-computers-page-controller.ts
  - maxgent/client/webapp/src/modules/runtime/computers/hooks/use-cloud-computer-viewer-action.ts
  - maxgent/client/webapp/src/routes/_authenticated/chat.computers.tsx
  - maxgent/client/webapp/src/modules/runtime/desktop/components/desktop-viewer-layer.tsx
  - maxgent/client/webapp/src/modules/runtime/desktop/components/desktop-viewer-window.tsx
  - maxgent/client/webapp/src/routes/_authenticated/desktop-popout.tsx
  - maxgent/client/webapp/src/stores/desktop-store.ts
  - maxgent/client/webapp/src/lib/environment-retry.ts
  - maxgent/client/webapp/src/lib/sandbox-error.ts
  - maxgent/client/webapp/src/i18n/locales/en.json
  - product-kb/concepts/ai-cloud-computer.md
  - product-kb/ui-map/workspace-sidebar.md
  - product-kb/ui-map/chat-page.md
  - product-kb/troubleshooting/workspace-unavailable.md
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web, desktop]
---

# AI Cloud Computer Viewer

## Direct Answer

The **Computers** page shows one **AI Cloud Computer** card with current viewer
status and a **View** or **Reconnect** action. It does not show a Local Desktop
card. Existing desktop Session pages also expose a Cloud Computer shortcut in
the top Chat header. When the Session Dock is collapsed, the shortcut appears
immediately left of its expand control. Both entries open, restore, or focus the
App Shell's global floating viewer for the current cloud workspace. Viewer
actions are disabled when the current sandbox/workspace has no sandbox id and
are hidden on mobile or narrow layouts.

This viewer is for MoClaw's cloud workspace. It is not Local Desktop and does
not mean MoClaw is viewing or controlling the user's personal computer.
Entering the Computers page can check and prepare the current environment.
Rendering the Header shortcut does not trigger environment initialization or
start a viewer connection. Opening or closing the viewer, or a viewer
connection error, does not create, switch, or end a Chat Session.

## Visible Controls And States

| UI Copy | Meaning |
|---|---|
| **Computers** | Standalone sidebar page for the current AI Cloud Computer status and viewer action. |
| **AI Cloud Computer** | Cloud workspace card on the Computers page. |
| **Cloud Computer** | Desktop-only Session Header shortcut that opens or reuses the same viewer. |
| **View** | Opens the visual viewer for the current cloud workspace. |
| **Reconnect** | Retries after the viewer connection information could not be loaded. |
| **Connected** | The VNC/desktop viewer stream is connected. |
| **Connecting...** | The viewer is opening or reconnecting to the desktop stream. |
| **Connection error** / **Connection lost** | The visual stream failed or disconnected. The viewer may retry automatically. |
| **Idle** | The viewer is not currently connected. |
| **Open in new window** | Pop the connected viewer into a separate browser window. This can be blocked by browser popup settings. |
| **Minimize** | Hides the visual stream behind a compact restore control without changing the target Computer. |

The viewer is one global floating window that stays attached to the same
Computer while users move between Chat and feature pages. It can also be opened
in a separate browser window. It is not a Session Dock tab.

The floating desktop viewer also has a close control. Closing the viewer clears
the visual stream connection in the web app; it should not be described as
deleting files, stopping the user's account, removing the cloud workspace, or
changing the current Chat Session.

## Recovery Guidance

There are two different recovery paths:

- **Viewer connection issue**: use **View** or **Reconnect** on the Computers
  page, click the Cloud Computer Header shortcut again, or close and reopen the
  viewer. If **Open in new window** does nothing, check browser popup blocking.
- **Workspace/runtime issue**: if chat or the workspace says **Workspace issue.
  Restart the workspace to continue.**, use the restart workspace action if it
  appears, then retry the task.

The desktop viewer can reconnect automatically after a non-clean disconnect.
Repeated **Failed to connect**, **Connection error**, or **Connection lost**
states should be escalated with account email, approximate time, screenshot,
visible copy, and whether the issue was in the in-app floating viewer or
pop-out window.

## Mobile And Layout Boundary

The current AI Cloud Computer visual viewer is hidden on mobile/narrow
viewports. Mobile users can still chat and use workspace surfaces that are
available in the mobile layout, but support should not promise the same visual
desktop viewer controls on mobile.

## Do Not Say

- Do not call the AI Cloud Computer viewer Local Desktop.
- Do not say viewing the AI Cloud Computer means MoClaw can see the user's
  laptop screen.
- Do not say closing the viewer stops the task, deletes files, or closes the
  cloud workspace.
- Do not tell users to open Settings to view the cloud computer.
- Do not say the Computers page contains a Local Desktop card.
- Do not say rendering the header entry initializes a workspace or connects
  the viewer.
- Do not say opening or closing the viewer, or a viewer connection error,
  changes the Chat Session.
- Do not tell users to dock or undock the viewer.
- Do not promise the visual desktop viewer appears on mobile.
- Do not expose raw VNC, stream URL, auth key, websockify, or sandbox internal
  details in customer-facing support answers.
- Do not tell users to fix Local Desktop when the visible issue is the cloud
  workspace viewer or workspace restart flow.

## Related Cards

- `moclaw.concepts.ai_cloud_computer`
- `moclaw.ui.workspace_sidebar`
- `moclaw.ui.chat_page`
- `moclaw.ui.mobile_layout`
- `moclaw.reference.cloud_and_local_tools`
- `moclaw.troubleshooting.workspace_unavailable`
- `moclaw.troubleshooting.sandbox_capacity_full`
