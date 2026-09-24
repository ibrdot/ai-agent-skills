---
id: help.workspace.view_ai_cloud_computer
title: View Or Reconnect The AI Cloud Computer
audience: user
status: verified
source_cards:
  - moclaw.reference.ai_cloud_computer_viewer
  - moclaw.concepts.ai_cloud_computer
  - moclaw.ui.workspace_sidebar
  - moclaw.ui.chat_page
  - moclaw.troubleshooting.workspace_unavailable
  - moclaw.reference.cloud_and_local_tools
last_reviewed_at: 2026-07-30
---

# View Or Reconnect The AI Cloud Computer

The AI Cloud Computer is MoClaw's cloud workspace. You can open a visual desktop
view when it is available in the desktop web layout.

## Open The Viewer

On a desktop-sized layout, use either entry:

- Open the left sidebar, select **Computers**, and click **View** on the
  **AI Cloud Computer** card.
- In an existing Session, click the Cloud Computer button in the top Chat
  header. When the Session Dock is collapsed, the button is immediately left of
  its expand control.

Both entries open the App Shell's global floating viewer. Clicking either entry
again reuses or focuses the viewer for the same Computer instead of creating
another one. If the viewer connects, you may see **Connected**. It stays
attached to the same Computer while you move between Chat and feature pages and
is separate from the Session Dock.

Entering the Computers page can check and prepare the current cloud environment.
Simply seeing the Header button does not trigger environment initialization or
start a viewer connection. Opening or closing the viewer, or a viewer
connection error, does not create, switch, or end the current Chat Session.

## If You Cannot See View

Viewer actions are hidden on mobile or narrow screens and can be disabled while
the current cloud workspace is not ready. The Header shortcut appears only on
existing Session pages; use **Computers** from the sidebar for the standalone
status page.

The AI Cloud Computer viewer is different from **Local Desktop**. It shows the
cloud workspace, not your personal computer.

## If The Viewer Fails

If you see **Failed to connect**, **Connection error**, **Connection lost**, or
**Idle**, click **View** on the Computers page or the Cloud Computer button in
the top Chat header again.

If **Open in new window** does nothing, your browser may have blocked the
pop-out window. Use the in-app viewer, or allow pop-ups for MoClaw and try
again.

## If The Workspace Has A Restart Error

If chat says **Workspace issue. Restart the workspace to continue.**, use the
restart workspace action if the UI offers one, then retry the task.

If the same issue repeats, send support your account email, approximate time,
screenshot, and exact visible error copy. Do not send stream URLs, auth keys,
passwords, API keys, OAuth tokens, or signed URLs.

## Related Articles

- `getting-started/ai-cloud-computer.md`
- `workspace/cloud-and-local-tools.md`
- `desktop/local-desktop.md`
- `troubleshooting/common-errors.md`
