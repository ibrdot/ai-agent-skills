---
id: moclaw.ui.settings
title: Settings Entry Points
type: ui_map
product_area: account
audience: user
status: verified
owner: product
last_reviewed_at: 2026-07-29
source_paths:
  - maxgent/client/webapp/src/modules/app-shell/components/app-shell.tsx
  - maxgent/client/webapp/src/modules/app-shell/components/user-profile-view.tsx
  - maxgent/client/webapp/src/modules/app-shell/components/desktop-download-overlay.tsx
  - maxgent/client/webapp/src/modules/chat/shell/components/new-chat-header.tsx
  - maxgent/client/webapp/src/modules/settings/components/settings-dialog.tsx
  - maxgent/client/webapp/src/modules/settings/components/desktop-settings-panel.tsx
  - maxgent/client/webapp/src/modules/settings/components/desktop-section-view.tsx
  - maxgent/client/webapp/src/modules/settings/components/api-keys-section-view.tsx
  - maxgent/client/webapp/src/i18n/locales/en.json
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Settings Entry Points

## Direct Answer

The main visible Settings entry point is **Settings** in the bottom-left user
avatar menu inside the shared App Shell sidebar. Settings is a global dialog
and can open over Chat or feature pages. On New Chat only, the Usage/Credits
widget can open **Usage** directly.

The current desktop-width Settings panel has these tabs:

1. General
2. Local Tools in the desktop client only
3. Appearance
4. Account
5. Usage
6. Billing
7. API Keys
8. About

## Tab Map

| Tab            | Use For                                                                                           |
| -------------- | ------------------------------------------------------------------------------------------------- |
| General        | Send shortcut, language, time format, timezone, notifications, and desktop launch behavior. |
| Local Tools    | Local Chrome mode and local shell controls in the desktop client.                                |
| Appearance     | Theme, colors, font, text size, and spacing.                                                      |
| Account        | Signed-in identity, current plan, plan state, and upgrade/cancel/keep-subscription actions.       |
| Usage          | Credits, balance, and usage history.                                                              |
| Billing        | Payment history, subscription invoice links, and Credit Pack invoice/receipt links.               |
| API Keys       | Connect Codex/ChatGPT OAuth identity when visible.                                                |
| About          | Privacy Policy and Terms.                                                                         |

For detailed billing and usage UI routing, load
`moclaw.ui.billing_and_usage_surfaces`.

## Important Correction

The current Settings dialog code does not have a Connectors tab. Connector
management primarily lives in the left sidebar Connectors section;
`/settings/connectors` is a compatibility/recovery route.

## User Menu Boundary

Logout, Products, Use Cases, Blog, Privacy Policy, Terms, and compact
plan/credits entry points live in the bottom-left user-avatar menu; they are not
standalone Settings tabs. The Account tab currently does not expose controls for
email, avatar, display name, or account deletion.

On desktop-width web, the download button beside the account entry opens the
Moclaw Desktop installer list. This download entry remains separate from
Settings and from the Cloud Computer viewer button in the top Chat header.

Do not describe Settings as a top-right gear entry. Usage, feedback, and
Community belong to the New Chat header; Session and feature pages do not repeat
that header. Settings remains available globally from the bottom-left account
menu.

## Mobile Layout

Mobile Settings is a full-screen sheet with sections stacked vertically. Do not
ask mobile users to look for a left-side Settings tab. Settings does not contain
a Cloud Computer section. The Cloud Computer header button and visual viewer
are also hidden on mobile.
