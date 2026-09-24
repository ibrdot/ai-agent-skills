---
id: help.account.sign_in_and_logout
title: Sign In And Log Out
audience: user
status: verified
source_cards:
  - moclaw.reference.authentication_and_login
  - moclaw.reference.account_profile_and_user_menu
  - moclaw.ui.settings
  - moclaw.playbooks.ask_for_screenshot_or_reference_id
last_reviewed_at: 2026-06-08
---

# Sign In And Log Out

Open MoClaw and choose **Log in or sign up**. If you open a protected MoClaw
page while signed out, MoClaw sends you to login and then returns you to the app
after authentication completes.

## Log Out

Use the lower-left user menu, then choose **Logout**.

During logout, MoClaw clears local app state and signs you out of the current
MoClaw session. Do not close the page halfway through if it is still navigating.

## If Login Fails

If you see **Login failed. Please try again.**, use the login page button to
retry.

If the page appears stuck on a callback or spinner, refresh once or open
`/auth`, then try signing in again.

If you see **Login is not configured**, you are likely in an environment where
login is not set up. Use the normal MoClaw app URL or contact support with the
URL path you are viewing.

## If You Keep Returning To Login

You may be signed out or your session may have expired. Sign in again from the
login page.

If the same protected page keeps sending you back to login after a successful
sign-in, contact support with:

- account email, if known;
- browser and device;
- page you were trying to open;
- approximate time and timezone;
- exact visible error copy or screenshot.

Do not send passwords, OAuth codes, access tokens, refresh tokens, cookies, or
full browser storage.

## Related Articles

- `account/settings-and-account.md`
- `account/account-and-data-requests.md`
- `troubleshooting/contact-support-and-send-diagnostics.md`
