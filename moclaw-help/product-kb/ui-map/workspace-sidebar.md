---
id: moclaw.ui.workspace_sidebar
title: App Left Sidebar
type: ui_map
product_area: workspace
audience: user
status: verified
owner: product
last_reviewed_at: 2026-07-30
source_paths:
  - maxgent/client/webapp/src/modules/app-shell/components/app-sidebar.tsx
  - maxgent/client/webapp/src/modules/app-shell/components/app-sidebar-view.tsx
  - maxgent/client/webapp/src/modules/chat/shell/components/chat-navigation.tsx
  - maxgent/client/webapp/src/modules/chat/shell/components/chat-navigation-view.tsx
  - maxgent/client/webapp/src/modules/app-shell/components/sidebar-module-navigation.tsx
  - maxgent/client/webapp/src/modules/chat/session-list/components/session-list-panel.tsx
  - maxgent/client/webapp/src/modules/app-shell/layout/lib/workspace-module-route.ts
  - maxgent/client/webapp/src/i18n/locales/en.json
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# App Left Sidebar

## Direct Answer

The left sidebar is the shared navigation inside the authenticated App Shell.
It stays available across Chat and feature pages and renders two main regions:

1. Product navigation entries.
2. **Recents** session list.

Workspace tool entries are:

1. Computers
2. Channels
3. Connectors
4. Artifacts
5. Schedules
6. Skills

## Section Map

| Section                 | User Meaning                                                                                                      | Common Questions                                                           |
| ----------------------- | ----------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| Computers               | AI Cloud Computer status and visual viewer entry. The page does not show Local Desktop.                           | How to view the cloud desktop or troubleshoot connection loss.             |
| Channels                | Chat entry points such as Telegram, Slack, Lark, and Discord.                                                     | How to bind or disconnect chat apps.                                       |
| Connectors              | Third-party accounts and tools such as Google Workspace, GitHub, and Linear; MCP only if the current UI shows it. | How to connect, why a connector expired, or why a repo is missing.         |
| Artifacts               | File snapshots delivered by AI.                                                                                   | Where outputs are and how to download them.                                |
| Schedules               | Scheduled tasks.                                                                                                  | Why a task did not run or how to cancel it.                                |
| Skills                  | Loaded capability instructions.                                                                                   | How to inspect a skill, what System/User means, or why a skill is missing. |

## Recents

The **Recents** region lists user-visible chat Sessions.

- **New session** clears the active chat selection and opens a fresh chat
  starting point.
- Selecting a row activates that Session.
- Session rows can show running state, source/channel badges, title, and row
  actions.
- Row actions can rename or delete the Session from the visible Recents list
  when available.
- The chat header can show the active Session title and a rename action.

Do not describe Recents as a full account export/history manager, and do not
call a Session a browser login session.

## State And Visibility Rules

- The active navigation row reflects the middle page, not which Dock tab or VNC
  window is open.
- On mobile, the sidebar is a drawer/overlay rather than a fixed left sidebar.
- Product entries route to standalone feature pages: **Computers**,
  **Channels**, **Connectors**, **Artifacts**, **Schedules**, and **Skills**.
- Computers contains one AI Cloud Computer card and no Local Desktop card. On
  desktop Session pages, the same viewer also has a Header shortcut; when the
  Session Dock is collapsed, it appears immediately left of the expand control.
  Viewer actions are hidden on mobile.
- Feature pages do not show the New Chat header's usage, feedback, or Community
  controls.

## Skills Section

The **Skills** entry opens the Skills surface for skills discovered in the
current workspace or active Session. It can show **System** and **User** source
labels.
The current visible surface is for inspection, not install/delete management.

## Related Cards

- `moclaw.reference.ai_cloud_computer_viewer`
- `moclaw.reference.cloud_and_local_tools`
- `moclaw.ui.chat_page`
