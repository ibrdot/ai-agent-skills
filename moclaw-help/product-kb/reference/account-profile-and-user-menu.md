---
id: moclaw.reference.account_profile_and_user_menu
title: Account Profile And User Menu
type: reference
product_area: account
audience: support
status: verified
owner: product
last_reviewed_at: 2026-06-09
source_paths:
  - maxgent/client/webapp/src/modules/settings/components/account-section.tsx
  - maxgent/client/webapp/src/modules/app-shell/components/user-profile.tsx
  - maxgent/client/webapp/src/modules/app-shell/components/user-profile-view.tsx
  - maxgent/client/webapp/src/modules/auth/lifecycle/hooks/use-current-user.ts
  - maxgent/client/webapp/src/modules/auth/lifecycle/api/current-user-api.ts
  - maxgent/client/webapp/src/modules/auth/lifecycle/lib/current-user.ts
  - maxgent/server/app-server/app/domains/identity/routes/auth.py
  - maxgent/server/app-server/app/domains/identity/schemas/auth.py
  - maxgent/client/webapp/src/i18n/locales/en.json
  - maxgent/client/webapp/src/i18n/locales/zh.json
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Account Profile And User Menu

## Direct Answer

The bottom-left user profile menu is the main account menu. It shows the current
user identity, plan, credits, Settings, external product links, Privacy Policy,
Terms, and Logout. The **Settings > Account** section shows the signed-in profile
and current plan controls.

## User Menu

The user menu can show:

- display name and email when signed in;
- a short plan badge such as Pro or Trial;
- active plan display name;
- credit balance row that opens **Settings > Usage**;
- upgrade, buy credits, or resubscribe action depending on plan state;
- Settings entry;
- external links for Products, Use Cases, Blog, Privacy Policy, and Terms;
- Logout.

If the left sidebar is collapsed, the avatar remains available as a
compact menu trigger.

## Account Section

**Settings > Account** currently shows:

- profile card with avatar, display name, and email when signed in;
- current plan name and status;
- price and validity range for non-free plans when available;
- Upgrade, Cancel Pro, or Keep Subscription action depending on subscription
  state. Current public support posture is no public 30-day no-card MoClaw
  Trial, so do not promise a Start Trial action unless the current account UI
  explicitly shows one.

The Account section does not currently expose profile editing controls.

## Profile Data

- Web clients fetch the canonical current-user profile from `GET /api/auth/me`.
- The response includes id, auth subject, email, email verification state, and
  an internal-user flag.
- The API only returns email when the stored user email is verified.
- Display name falls back to auth profile data or a verified email-derived name.
- The user menu may also show plan state, credits, and subscription actions, but
  those are billing/usage surfaces rather than profile-edit controls.

## Support Boundaries

- Do not tell users they can edit email, avatar, or display name inside
  **Settings > Account** unless product adds those controls.
- Do not tell users they can delete an account from Settings; no current
  Settings control or public account-deletion policy was found in these sources.
- Do not treat the user menu's plan, credits, or subscription actions as profile
  editing or data-deletion controls.
- For subscription cancellation/reactivation, route to the billing/cancellation
  how-to; for refunds or disputes, route to billing escalation.
- For legal/privacy wording, link the current Privacy Policy and Terms rather
  than paraphrasing legal commitments.

## Related Cards

- `moclaw.reference.authentication_and_login`
- `moclaw.reference.account_identity_and_data_requests`
- `moclaw.ui.settings`
- `moclaw.how_to.cancel_or_reactivate_pro`
- `moclaw.reference.refund_policy`
- `moclaw.playbooks.security_privacy_answering`
