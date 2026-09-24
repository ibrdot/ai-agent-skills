---
id: moclaw.reference.user_preferences_and_settings
title: User Preferences And Settings
type: reference
product_area: account
audience: support
status: verified
owner: product
last_reviewed_at: 2026-07-23
source_paths:
  - maxgent/client/webapp/src/modules/app-shell/components/user-profile-view.tsx
  - maxgent/client/webapp/src/modules/chat/shell/components/new-chat-header.tsx
  - maxgent/client/webapp/src/modules/settings/components/settings-dialog.tsx
  - maxgent/client/webapp/src/modules/settings/components/general-section.tsx
  - maxgent/client/webapp/src/modules/settings/components/general-section-view.tsx
  - maxgent/client/webapp/src/modules/settings/components/appearance-section.tsx
  - maxgent/client/webapp/src/modules/settings/components/appearance-section-view.tsx
  - maxgent/client/webapp/src/modules/settings/components/usage-widgets.tsx
  - maxgent/client/webapp/src/modules/settings/components/usage-widgets-view.tsx
  - maxgent/client/webapp/src/stores/settings-store.ts
  - maxgent/client/webapp/src/i18n/index.ts
  - maxgent/client/webapp/src/i18n/locales/en.json
  - maxgent/client/webapp/src/i18n/locales/zh.json
  - maxgent/client/webapp/src/lib/format-time.ts
  - maxgent/client/webapp/src/modules/chat/message-list/components/message-list-v2.tsx
  - maxgent/client/webapp/src/modules/chat/message/components/agent-message.tsx
  - maxgent/client/webapp/src/modules/chat/message/components/user-message.tsx
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# User Preferences And Settings

## Direct Answer

MoClaw user preferences live in **Settings**. Current Settings sections include
General, Appearance, Account, Usage, Billing, API Keys, and About. On desktop
they appear as tabs in the Settings dialog; on mobile they appear as stacked
sections in a full-screen sheet.

The primary visible entry is the lower-left user menu's **Settings** item.
Some product surfaces can open a specific Settings tab directly, such as the
usage/credits widget opening **Usage**.

## General Preferences

| Setting       | Current Options / Behavior                                                                                           |
| ------------- | -------------------------------------------------------------------------------------------------------------------- |
| Language      | `en`, `zh`, `pt`, `fr`, `es`, `ko`, `ja`, `ru`, `de`. Unsupported values normalize to English.                       |
| Send with     | Enter, or Cmd+Enter on macOS/iPhone/iPad user agents and Ctrl+Enter elsewhere.                                       |
| Timezone      | Browser-supported IANA timezones, shown with UTC offset; fallback list exists if the browser cannot enumerate zones. |
| Time format   | 12-hour or 24-hour.                                                                                                  |
| Notifications | Browser desktop notifications; enabling asks browser permission first when the Notification API is available.        |

Language is persisted separately in browser storage under `maxclaw-language`.
Detection order is saved language, browser language list, then English. Changing
language also updates the page `<html lang>` value.

Timezone and time-format preferences are confirmed to affect visible chat
message timestamps. Formatting falls back to the browser's local timezone if a
stored timezone is invalid. Do not use this card alone to claim how scheduled
task execution timezone is chosen.

If the user enables desktop notifications and the browser permission is denied
or not granted, the current implementation does not turn the stored notification
preference on. If the browser does not support notifications, the preference can
still be stored, but actual delivery depends on browser/OS support.

## Appearance Preferences

| Setting | Current Options                             |
| ------- | ------------------------------------------- |
| Theme   | Light, Auto, Dark                           |
| Font    | Default, Bold, Magazine, Coder              |
| Size    | XS, S, M, L, XL                             |
| Spacing | Tight, Snug, Default, Comfortable, Spacious |
| Color   | Default, Paper, Ocean                       |
| Reset   | Resets appearance preferences only          |

Appearance and other non-language settings are persisted in browser storage
under `maxclaw-settings`.

The Appearance reset action only resets `theme`, `font`, `fontSize`, `spacing`,
and `color` to defaults. It does not reset language, send key, timezone, time
format, notifications, usage badge visibility, account state, billing state, or
API keys.

## Usage Preference

The **Settings > Usage** section has a **Show on home** toggle. It controls
whether the small Usage/Credits badge appears in the New Chat header for
signed-in users when the app is not running in mock mode. It does not add the
badge to Session or feature pages.

The default value for new or migrated local settings is on. This preference is
also browser-local.

## Support Boundaries

- These preferences are local web-app preferences. If the user changes browser,
  clears local storage, uses private/incognito mode, or uses another device,
  settings may not follow unless the app later adds account-synced preferences.
- Browser notifications also depend on the browser/OS notification permission.
- Do not say Settings has a Connectors tab. Current connector management is in
  the left sidebar Connectors section.
- Do not say the Account tab edits profile name, email, or avatar; current code
  displays identity and subscription controls but does not provide profile edit
  controls.
- Do not instruct users to find a Window Controls setting. That setting row is
  retired/hidden in current Settings even though legacy values may still exist
  in browser storage.

## Related Cards

- `moclaw.ui.settings`
- `moclaw.reference.account_profile_and_user_menu`
- `moclaw.reference.billing_invoices`
