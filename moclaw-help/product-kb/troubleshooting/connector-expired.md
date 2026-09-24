---
id: moclaw.troubleshooting.connector_expired
title: Connector Expired Or Reconnect Failed
type: troubleshooting
product_area: connectors
audience: support
status: verified
owner: product
last_reviewed_at: 2026-06-09
source_paths:
  - maxgent/client/webapp/src/components/connectors/connectors-section.tsx
  - maxgent/client/webapp/src/components/connectors/connectors-section-view.tsx
  - maxgent/client/webapp/src/components/connectors/connector-settings-modal.tsx
  - maxgent/client/webapp/src/i18n/locales/en.json
  - maxgent/client/webapp/src/lib/connector-registry.ts
  - maxgent/client/webapp/src/lib/connector-visibility.ts
  - maxgent/client/webapp/src/stores/connector-store.ts
  - maxgent/server/app-server/app/domains/connector/router.py
  - maxgent/server/app-server/app/domains/connector/schema.py
  - maxgent/server/app-server/app/domains/connector/README.md
  - maxgent/server/app-server/app/domains/connector/services/credential.py
  - maxgent/server/app-server/app/domains/connector/services/registry.py
  - maxgent/server/app-server/app/domains/connector/services/providers/oauth2/handler.py
  - maxgent/server/app-server/app/domains/connector/docs/providers/github/auth.md
  - maxgent/server/app-server/app/domains/connector/docs/linear-auth-patterns.md
  - maxgent/server/app-server/app/routers/google_workspace.py
  - maxgent/server/app-server/app/services/google_workspace.py
applies_to:
  plans: [free, trial, pro]
  environments: [test, prod]
  platforms: [web]
---

# Connector Expired Or Reconnect Failed

## Symptom

The connector row shows **Expired**, **Reconnect**, warning status, or the user
says a previously connected service no longer works. The user may also report
that disconnecting failed, reconnecting redirected but did not restore access,
or MoClaw disconnected locally while provider access may still exist.

## Direct Answer

Ask the user to manage connectors from **left sidebar > Connectors**. For an
expired OAuth connector, use the row's **Reconnect** or **Connect** action and
finish the provider-side authorization flow. Do not ask for OAuth tokens,
provider secrets, or raw authorization codes.

## Likely Causes

- The third-party OAuth token expired or was revoked.
- The user changed permissions on the provider side.
- The connector is connected but a required account/folder/scope is missing.
- The connector is gated or unavailable in the current environment.
- A provider-side revocation or network call failed during disconnect.
- The provider authorization completed, but the product did not refresh
  connector state yet.
- GitHub identity is connected but GitHub App installation or organization
  enablement is missing.
- Google Workspace OAuth is connected but Drive folder setup is incomplete.
- Linear OAuth is connected but the authorized user/workspace is not the one the
  user expected, the target resource belongs to another workspace, or a required
  Linear provider UUID was not resolved.
- Linear permissions, workspace membership, archived resources, or provider-side
  revocation changed after the connector was created.

## Current UI And State Notes

- Connectors live in **left sidebar > Connectors**, not the Settings dialog.
- The current front-end connector registry checked on 2026-06-15 has
  **Google Workspace**, **GitHub**, and **Linear** rows. Do not tell users to
  look for a separate **Gmail** connector row; Gmail is part of
  **Google Workspace** in the visible UI.
- Generic remote connector visibility depends on backend metadata, connection
  state, and adapter rules. Local/mock can show catalog behavior that should not
  be used as proof of production availability.
- Not connected rows show **Connect** or a connector-specific action.
- Connected OAuth rows show a three-dot menu with **Settings** and
  **Disconnect**.
- Google Workspace can show **Expired** and a **Reconnect** action.
- Google Workspace can also show **Drive setup needed** after OAuth succeeds.
- Google Workspace uses a dedicated Google Workspace OAuth/status/revoke path,
  separate from the generic `/api/connector` OAuth rows.
- GitHub settings separate connected identity from accessible accounts and
  organizations.
- GitHub can show installed accounts/organizations that are not yet enabled in
  MoClaw.
- Disconnecting a GitHub organization inside MoClaw removes the local binding;
  users may still need to open GitHub to uninstall the app or adjust repository
  access.
- Linear is a standard OAuth connector row, not a GitHub-style installation list.
- Linear's current connector model uses an authorized Linear user/workspace
  boundary. Write actions default to the authorized user actor.
- Linear action IDs such as `teamId`, `assigneeId`, `stateId`, `projectId`, and
  `labelId` are provider UUIDs, not display names or team keys.
- If MCP is visible in a verified current UI, it uses **Manage** for server
  records and is not a normal OAuth connector row with **Disconnect**.
- If connector disconnect succeeds locally but remote revoke is unconfirmed,
  the UI can tell users to review provider access settings.
- If the provider revoke request fails because of provider/network failure,
  disconnect can fail and the user should retry.

## Disconnect And Revoke Semantics

- Generic remote connector disconnect calls `/api/connector/delete_auth`,
  attempts provider revoke for healthy stored payloads, then revokes local
  credentials.
- Retryable provider revoke failures such as network, rate limit, or 5xx errors
  are retried. If they still fail, the UI can show **Could not reach
  {connector} to revoke access. Please try again.**
- Non-retryable provider revoke failures such as already-invalid tokens can
  still result in local disconnect, with `remote_revoke_status=unconfirmed`.
  Support should tell the user to review the provider's own access/settings
  page.
- GitHub account/organization **Disconnect...** uses the account-level local
  disconnect path and then shows a reminder that the GitHub App may still be
  installed remotely.
- Google Workspace revoke is a dedicated best-effort Google route. If the local
  row is gone but the provider still shows MoClaw access, send the user to
  Google account connections/settings to confirm or remove remote access.

## Recovery Steps

1. Ask the user which connector is affected.
2. Tell them to open **left sidebar > Connectors**.
3. Check whether the row is missing, not connected, connected, expired, or
   warning.
4. If the row is expired, use **Reconnect** if shown; otherwise use **Connect**
   again.
5. Complete the provider-side authorization page and return to MoClaw.
6. Refresh **left sidebar > Connectors** or reopen `/chat`.
7. If it is Google Workspace, verify Drive folder setup after reconnect.
8. If it is GitHub, verify GitHub identity, GitHub App installation, enabled
   account/organization, and repository scope.
9. If it is Linear, verify the connected Linear user/workspace, confirm the
   target team/project/issue/user/state belongs to that workspace, and resolve
   provider UUIDs before retrying writes.
10. If the user expects a Gmail connector row, explain that Gmail belongs to the
    **Google Workspace** row in the current UI.
11. If disconnect says local disconnect completed but remote revoke was
   unconfirmed, tell the user to review the provider's access/settings page.
12. If disconnect failed because MoClaw could not reach the provider, retry
    later and escalate if it repeats.
13. If the connector still fails, collect safe diagnostic details.

## Escalate When

- Reconnect succeeds but the connector still shows expired.
- The connector disappears for an account that should have access.
- The user reports provider-side authorization succeeded but MoClaw cannot use
  the service.
- Disconnect repeatedly fails.
- Local disconnect succeeds but provider access still appears active and the
  user cannot remove it from the provider settings.
- The row remains connected after a disconnect attempt and the visible toast
  says MoClaw could not reach the provider to revoke access.
- GitHub user identity is connected but accessible organizations or repositories
  do not match the GitHub App settings.
- Google Workspace reconnect succeeds but Drive setup remains stuck.
- Linear OAuth succeeds but the expected workspace, team, project, issue, user,
  or workflow state remains inaccessible.
- Linear create/update fails after provider IDs were resolved and connector
  status is connected.

Collect account email, connector name, visible status text, whether the user was
connecting/reconnecting/disconnecting, approximate time/timezone, provider
account/workspace/organization name, and a screenshot of the connector row or
settings modal with secrets redacted.

## Do Not Say

- Do not promise that reconnecting restores all permissions.
- Do not tell users to look for a separate Gmail connector row in the current
  UI.
- Do not tell users to share raw OAuth tokens or secrets.
- Do not ask for provider passwords, OAuth authorization codes, refresh tokens,
  bearer tokens, or API keys.
- Do not say disconnecting a GitHub organization in MoClaw always uninstalls the
  GitHub App remotely.
- Do not say local disconnect always proves remote provider access was removed.
- Do not promise MCP **Manage** unless MCP is visible in the current account UI
  or a newer verified source confirms it.
- Do not treat Google Drive setup issues as generic OAuth expiry; use the Google
  folder troubleshooting card.
- Do not treat missing GitHub repositories as generic OAuth expiry; use the
  GitHub repository troubleshooting card.
- Do not say Linear uses GitHub App installation or repository selection.
- Do not promise every Linear workspace, team, project, issue, or archived
  resource is visible after OAuth.
- Do not tell users to paste Linear OAuth tokens, refresh tokens, API keys,
  cookies, passwords, or arbitrary GraphQL queries.

## Related Cards

- `moclaw.reference.connectors_status`
- `moclaw.ui.connectors_panel`
- `moclaw.how_to.connect_linear`
- `moclaw.how_to.connect_google_workspace`
- `moclaw.how_to.connect_github`
- `moclaw.troubleshooting.google_workspace_needs_folder`
- `moclaw.troubleshooting.github_repo_not_visible`
- `moclaw.reference.github_authorization_scope`
