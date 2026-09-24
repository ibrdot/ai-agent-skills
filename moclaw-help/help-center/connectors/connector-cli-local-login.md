---
id: help.connectors.connector_cli_local_login
title: connector-cli Local Login
audience: user
status: verified
source_cards:
  - moclaw.reference.connector_cli_local_login
  - moclaw.reference.authentication_and_login
  - moclaw.reference.connectors_status
  - moclaw.playbooks.ask_for_screenshot_or_reference_id
last_reviewed_at: 2026-06-09
---

# connector-cli Local Login

`connector-cli local login` is a local development login flow. It is not the
normal **left sidebar > Connectors** page and it is not available in production.

## When To Use It

Use it only if you are working with the local connector runtime and started from
the terminal command:

```sh
connector-cli local login
```

The command opens a browser page, waits for your MoClaw login, then returns a
one-time code to a local `127.0.0.1` callback owned by connector-cli.
The default wait window is about 10 minutes.

## If It Fails

Start the flow again from the terminal. Do not hand-edit the browser URL.

Common causes:

- the local-login route is disabled in the current environment;
- you are not signed in yet;
- the URL parameters from connector-cli expired or were malformed;
- the local callback listener is no longer running;
- the one-time exchange code expired or was already used.
- the browser could not navigate to the loopback callback page.

If the page says **Local login failed. Please try again from the terminal**,
rerun the terminal command so connector-cli creates a fresh URL and callback
listener.

## What Not To Share

Do not send support sandbox tokens, code verifiers, one-time exchange codes,
connector config files, OAuth tokens, cookies, or passwords.

For normal connector setup, use **left sidebar > Connectors** instead.

## Related Articles

- `connectors/connectors-overview.md`
- `connectors/manage-mcp-servers.md`
- `account/sign-in-and-logout.md`
