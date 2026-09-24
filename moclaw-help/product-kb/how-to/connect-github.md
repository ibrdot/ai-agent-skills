---
id: moclaw.how_to.connect_github
title: Connect GitHub
type: how_to
product_area: connectors
audience: user
status: verified
owner: product
last_reviewed_at: 2026-06-09
source_paths:
  - maxgent/client/webapp/src/components/connectors/connectors-section.tsx
  - maxgent/client/webapp/src/components/connectors/connector-settings-modal.tsx
  - maxgent/client/webapp/src/lib/connector-registry.ts
  - maxgent/server/app-server/app/domains/connector/README.md
  - maxgent/server/app-server/app/domains/connector/docs/providers/github/auth.md
  - maxgent/server/app-server/app/domains/connector/services/github_connect.py
  - maxgent/server/app-server/app/domains/connector/services/providers/oauth2/github.py
  - maxgent/server/app-server/app/domains/connector/router.py
  - maxgent/client/webapp/src/components/connectors/README.md
  - maxgent/client/webapp/src/i18n/locales/en.json
applies_to:
  plans: [free, trial, pro]
  environments: [test, prod]
  platforms: [web]
---

# Connect GitHub

## Direct Answer

If **GitHub** is visible in the current account UI, open the left sidebar, go to
**Connectors**, find **GitHub**, and use **Connect**. After connecting your
GitHub identity, use the GitHub settings dialog to install, enable, or configure
GitHub App access for the accounts or organizations whose repositories MoClaw
should use.

## Before You Start

- GitHub has three practical layers in MoClaw: identity authorization, GitHub
  App installation, and repository selection.
- Connecting identity alone does not guarantee every repository is visible.
- GitHub connector visibility can depend on account and environment; do not
  promise the row is available for every user.
- Repository scope is managed on GitHub's side through the GitHub App
  installation/settings page.
- If OAuth succeeds but no org/repo selection appeared, open GitHub connector
  settings and check accessible or inactive accounts/organizations.
- The implementation is OAuth-first: **Connect GitHub** starts GitHub App user
  authorization, then MoClaw discovers visible GitHub App installations.

## Steps

1. Open `/chat`.
2. Open the left sidebar.
3. Expand **Connectors**.
4. If **GitHub** is visible, select it and click **Connect**.
5. Complete the GitHub authorization flow.
6. Reopen GitHub settings from the connector row.
7. Confirm the connected GitHub identity.
8. Check **Accessible Accounts & Organizations**.
9. Use **Install GitHub App** if the account or organization is not listed.
10. Use **Enable** if the account or organization appears under accounts or
    organizations to enable.
11. For an accessible installation, use **Manage Scope**, then
    **Configure in GitHub**, to adjust repository access in GitHub.

## GitHub Setting States

| State | Meaning |
|---|---|
| Connected identity | MoClaw knows which GitHub user is connected. This alone does not grant repo access. |
| Accessible account/org | The GitHub App installation is enabled in MoClaw for the current user. |
| Inactive account/org | The GitHub App is installed on GitHub, but the current user's MoClaw binding is not enabled. |
| All repositories | The GitHub App installation grants access to all repos in that account/org. |
| Selected repositories | Only selected repos are available. Add missing repos in GitHub. |
| Install GitHub App | Calls the backend install-start route and opens GitHub's App installation target picker with product state. |
| Manage Scope | Opens the per-account menu for scope management. |
| Configure in GitHub | Opens the GitHub installation management URL for that account/org. |
| Disconnect organization | Removes local MoClaw binding; GitHub-side App installation may still remain. |

## If You Cannot See It

- GitHub connector visibility can depend on account/environment.
- If **GitHub** is not visible in **Connectors**, do not route the user through
  this flow as if the row is present; collect current UI/account context.
- If repositories are missing, check whether the relevant GitHub App
  installation is enabled and whether repository selection is `all` or
  `selected`.
- If an inactive account/org is shown, **Enable** revalidates that the current
  GitHub user can still see that installation before restoring local access.
- If a local disconnect happened, GitHub App access may still exist remotely;
  open GitHub to finish uninstalling or adjust repository access.

## Do Not Say

- Do not say "connecting GitHub gives access to all repos."
- Do not say repo scope is controlled only inside MoClaw.
- Do not say an inactive account/org means the GitHub App is uninstalled.
- Do not ask users for GitHub tokens, OAuth codes, cookies, App private keys, or
  webhook secrets.
- Do not say the AI agent or sandbox receives the GitHub user access token.

## Related Cards

- `moclaw.reference.connectors_status`
- `moclaw.concepts.connectors_channels_skills`
- `moclaw.reference.github_authorization_scope`
- `moclaw.troubleshooting.github_repo_not_visible`
- `moclaw.troubleshooting.connector_expired`
