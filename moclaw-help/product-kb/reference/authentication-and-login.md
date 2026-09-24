---
id: moclaw.reference.authentication_and_login
title: Authentication And Login
type: reference
product_area: account
audience: support
status: verified
last_reviewed_at: 2026-06-08
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Authentication And Login

## Direct Answer

MoClaw uses a shared sign-in flow. Anonymous users who open a protected MoClaw
page are sent to login, then returned to the safe in-app page they were trying
to reach. **Logout** is in the lower-left user menu.

## User-Facing Entry Points

- `/auth` is the login entry and fallback page.
- When Auth0 is configured and there is no visible error, `/auth` starts
  Universal Login automatically.
- If Auth0 is not configured for the environment, `/auth` shows **Login is not
  configured**.
- If login fails, `/auth` can show **Login failed. Please try again.**
- `/auth/callback` is a transient callback route and should not be presented as
  a normal destination.
- Protected app routes redirect signed-out users to login with a safe return
  target.
- The lower-left user menu exposes **Logout**.

## Post-Login Routing Rules

- Signed-in users should not remain on `/auth`; they are redirected to a safe
  stored post-login target or `/chat`.
- The return target must be an in-app relative path.
- External return targets are rejected.
- `/auth` and `/auth/*` are rejected as return targets.
- `/` is rejected as the default post-login target unless explicitly allowed.
- Search params and hashes are preserved for safe in-app paths.

## Callback Failure Handling

| Callback State | Behavior |
|---|---|
| `error` query param is present | Redirects to `/auth` with the error and description so the user sees login-failed UI. |
| Missing `code` / `state` | Redirects to `/auth`. |
| `code` / `state` is present but auth resolves signed-out | Redirects to `/auth?error=...` with adapter error code or `auth0_callback_failed`. |
| Auth resolves signed-in while callback page is mounted | Navigates to stored post-login target or `/chat`. |

For support, this means a visible callback URL, spinner, or **Login failed**
message is an auth-flow symptom; do not ask for OAuth authorization codes,
tokens, cookies, or provider passwords.

## Logout Rules

- Logout is a single shared sequence used by the user menu and forced gate
  surfaces.
- Once logout starts, MoClaw latches auth into a signing-out state so route
  guards and API calls do not bounce the user back into login mid-logout.
- Logout clears analytics identity, local message cache best-effort, client
  stores, remembered user-sub identity, and remembered email before the auth
  adapter's terminal sign-out step.
- Local loopback environments may return to `/auth` if the marketing/pages URL
  is not reachable; hosted environments return to the configured origin.

## Account Switching Rule

MoClaw stores the last authenticated user subject in the browser. If a different
user signs in, the Identity Gate shows a loading screen and clears client state
before rendering the new account. This prevents one frame of account A's
workspace from painting under account B.

## Support Guidance

- If a user sees **Login failed. Please try again.**, ask them to retry from the
  visible login page.
- If a user is stuck on `/auth/callback` or a spinner, ask them to refresh once
  or return to `/auth`, then retry login.
- If a protected page keeps sending them to login, ask whether they recently
  logged out, whether the issue repeats after a fresh login, and what page they
  were trying to open.
- If **Login is not configured** appears, the current environment lacks login
  configuration; use the normal production app or escalate the environment.
- For repeated issues, collect account email if known, approximate time and
  timezone, browser/device, the visible URL path, and exact visible error copy.

## Do Not Say

- Do not tell users to send OAuth authorization codes, access tokens, refresh
  tokens, cookies, passwords, or full browser storage.
- Do not promise `/auth/callback` is a normal page users should bookmark.
- Do not claim logout instantly revokes every external provider session; it is
  MoClaw sign-out plus the current auth adapter's terminal step.
- Do not tell users an account can be edited or deleted from the login page.

## Related Cards

- `moclaw.reference.account_profile_and_user_menu`
- `moclaw.reference.account_identity_and_data_requests`
- `moclaw.ui.settings`
- `moclaw.playbooks.ask_for_screenshot_or_reference_id`
