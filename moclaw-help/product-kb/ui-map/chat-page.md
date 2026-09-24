---
id: moclaw.ui.chat_page
title: Chat Page Structure
type: ui_map
product_area: chat
audience: user
status: verified
owner: product
last_reviewed_at: 2026-07-30
source_paths:
  - maxgent/client/webapp/src/routes/_authenticated.tsx
  - maxgent/client/webapp/src/routes/_authenticated/chat.tsx
  - maxgent/client/webapp/src/modules/app-shell/components/app-shell.tsx
  - maxgent/client/webapp/src/components/layout/app-layout.tsx
  - maxgent/client/webapp/src/modules/app-shell/components/app-sidebar.tsx
  - maxgent/client/webapp/src/modules/chat/shell/components/chat-navigation.tsx
  - maxgent/client/webapp/src/modules/chat/shell/components/chat-shell.tsx
  - maxgent/client/webapp/src/modules/chat/shell/components/new-chat-header.tsx
  - maxgent/client/webapp/src/modules/chat/shell/components/chat-session-header.tsx
  - maxgent/client/webapp/src/modules/chat/message-list/components/conversation-layout.tsx
  - maxgent/client/webapp/src/modules/chat/session-list/components/session-list-panel.tsx
  - maxgent/client/webapp/src/modules/app-shell/components/sidebar-module-navigation.tsx
  - maxgent/client/webapp/src/modules/chat/message-list/components/chat-area.tsx
  - maxgent/client/webapp/src/modules/chat/composer/components/chat-input.tsx
  - maxgent/client/webapp/src/modules/chat/composer/components/chat-input-view.tsx
  - maxgent/client/webapp/src/modules/chat/composer/hooks/use-chat-composer.ts
  - maxgent/client/webapp/src/modules/runtime/computers/components/cloud-computer-header-action.tsx
  - maxgent/client/webapp/src/modules/runtime/computers/hooks/use-cloud-computer-viewer-action.ts
  - maxgent/client/webapp/src/modules/chat/message-list/components/message-list-v2.tsx
  - maxgent/client/webapp/src/modules/chat/message/components/message-content.tsx
  - maxgent/client/webapp/src/modules/chat/message/components/agent-message.tsx
  - maxgent/client/webapp/src/modules/chat/message/components/user-message.tsx
  - maxgent/client/webapp/src/modules/chat/message-list/components/suggested-replies.tsx
  - maxgent/client/webapp/src/modules/chat/composer/components/tier-selector.tsx
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Chat Page Structure

## Direct Answer

MoClaw's authenticated product uses one App Shell with a left navigation,
middle page area, and an optional Dock belonging to the current Session.
`/chat` without a Session is New Chat and does not show a Dock; after the first
accepted message, it becomes a Session page.

## Desktop Layout

| Area         | Purpose                                                                                     |
| ------------ | ------------------------------------------------------------------------------------------- |
| Left sidebar | Product navigation, **Recents** session list, and account entry point.                      |
| Middle page  | New Chat, an active Session, or a feature page such as Computers, Artifacts, or Connectors. |
| Session Dock | File preview tabs for the active Session.                                                   |
| Global VNC   | A separate floating AI Cloud Computer viewer that can remain open across page changes.      |

## Mobile Layout

Do not assume the three areas are visible at the same time on mobile.
The sidebar becomes an overlay, and an active Dock becomes a full-screen
overlay while preserving the same tabs.
For mobile answers, say "open the menu/drawer" rather than "look at the left
sidebar."

## Entry Points

- New message: bottom composer in the middle chat area.
- New Chat: **New Chat** in the left sidebar.
- Recent Sessions: **Recents** in the left sidebar; rows can select, rename, or
  delete Sessions when actions are visible.
- Current Session title: chat header at the top of the chat area, with rename
  when available.
- New Chat header: usage, feedback, Community, and development-only controls
  when available. Session and feature pages do not repeat those controls.
- File reference: composer `@` or file-related buttons.
- Commands: composer `/` button or `/` prefix opens the command menu.
- Skills: left sidebar **Skills** opens loaded skills; do not describe `/` as
  the Skills panel.
- Voice: when voice messages are enabled, the microphone control appears on the
  right side of the composer.
- Stop response: while streaming and the composer is empty, the send button
  switches to stop.
- Message content: the middle message area can show text, file cards, images,
  voice player, Thinking, Used tools, failure state, copy/retry actions, and
  suggested follow-ups.
- Watch AI activity: open **Computers** and use **View** on the AI Cloud Computer
  card. On desktop Session pages, the Cloud Computer button in the top Header is
  a shortcut to the same App Shell viewer. When the Session Dock is collapsed,
  the shortcut is immediately left of its expand control.
- Files and outputs: open **Artifacts**, a chat file card, or the Session Dock.
- Settings: **Settings** in the bottom-left user-avatar menu. On New Chat, the
  Usage/Credits widget can open **Settings > Usage**.

## State And Visibility Rules

- Runtime, usage gate, and workspace readiness affect whether messages can be
  sent.
- Uploading or failed attachments block sending until they finish or are
  removed.
- Messages with attachments sent during streaming may be queued until the
  current response finishes.
- Voice recording depends on feature flag, microphone permission, browser
  support, and the transcription path.
- Suggested follow-ups only appear after the latest assistant reply and are
  hidden while streaming or when the chat area is disabled.
- Dock state belongs to a specific Session. Narrow screens change its
  presentation, not its contents.
- VNC is global to the App Shell and is not stored in a Session Dock.
- The Cloud Computer header button is hidden on mobile. Rendering it does not
  trigger environment initialization or start a viewer connection.
- Opening or closing the viewer, or a viewer connection error, does not create,
  switch, or end a Chat Session.
- `/chat/computers` is the standalone Computers feature page. It contains an AI
  Cloud Computer card and no Local Desktop card.
- Specific buttons can depend on current account state, workspace state, and
  feature flags.
- The `/chat` route can select a Session with a `session` query parameter.
- Session-scoped draft state can preserve draft text/attachments per visible
  Session; do not promise that switching Sessions deletes unsent drafts.
