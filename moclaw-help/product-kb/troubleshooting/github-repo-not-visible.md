---
id: moclaw.troubleshooting.github_repo_not_visible
title: GitHub Repo Not Visible
type: troubleshooting
product_area: connectors
audience: user
status: verified
owner: product
last_reviewed_at: 2026-06-09
source_paths:
  - maxgent/client/webapp/src/components/connectors/connector-settings-modal.tsx
  - maxgent/client/webapp/src/stores/connector-store.ts
  - maxgent/server/app-server/app/domains/connector/README.md
  - maxgent/server/app-server/app/domains/connector/docs/providers/github/auth.md
  - maxgent/server/app-server/app/domains/connector/router.py
  - maxgent/server/app-server/app/domains/connector/services/github_connect.py
  - maxgent/server/app-server/app/domains/connector/services/providers/oauth2/github.py
  - maxgent/client/webapp/src/components/connectors/README.md
  - maxgent/client/webapp/src/i18n/locales/en.json
applies_to:
  plans: [free, trial, pro]
  environments: [test, prod]
  platforms: [web]
---

# GitHub Repo Not Visible

## Symptom

The user connected GitHub but MoClaw cannot see a repository, organization, or
account they expected.

## Likely Causes

- The user connected GitHub identity but did not install the GitHub App for the
  relevant account or organization.
- The GitHub App is installed, but that account/org is inactive in MoClaw and
  needs **Enable**.
- The GitHub App installation uses selected repositories and does not include
  the target repository.
- The installation is visible but disabled inside MoClaw.
- The user removed local MoClaw access but did not adjust/uninstall the GitHub
  App remotely.
- The repo belongs to an organization and the user does not have permission to
  install/configure the GitHub App for that organization.
- OAuth identity authorization succeeded, but the user has not completed or
  restored the GitHub App installation step.
- GitHub-side repository scope was changed recently and the visible MoClaw
  connector state has not refreshed yet.

## Recovery Steps

1. Ask whether the missing repo is under a personal account or organization.
2. Tell the user to open **left sidebar > Connectors > GitHub > Settings**.
3. Confirm the connected GitHub identity is the expected GitHub user.
4. Check **Accessible Accounts & Organizations**.
5. If the account/org is missing, use **Install GitHub App**.
6. If the account/org appears under accounts/organizations to enable, use
   **Enable**.
7. If the account/org is accessible but the repo is missing, check whether the
   installation uses all repositories or selected repositories.
8. If selected, use **Manage Scope**, then **Configure in GitHub**, and include
   the missing repo.
9. Retry the MoClaw task after the connector refreshes.
10. If GitHub was just changed, reopen GitHub connector settings and confirm
    the account/org is still accessible and the repository selection is updated.

## Common Interpretations

| User Sees | Meaning |
|---|---|
| GitHub identity connected, no repo choice shown | OAuth identified the user, but repo access is controlled by GitHub App installations. Open connector settings. |
| Account/org listed as inactive | GitHub App may still be installed on GitHub, but the local MoClaw binding is not enabled. Use **Enable**. |
| Selected repositories | Only selected repos are available; configure the installation in GitHub to add another repo. |
| Disconnect organization | MoClaw local binding was removed; GitHub App may still be installed remotely. |
| GitHub changed but MoClaw still looks stale | Refresh/reopen connector settings. Periodic installation sync exists, but support should use the visible state before promising access. |

## Escalate When

- GitHub shows the repo is authorized but MoClaw still cannot see it.
- The app installation callback returns to the wrong environment.
- The user belongs to the organization but cannot authorize the GitHub App.
- The account/org is accessible and set to all repositories, but the target repo
  still cannot be used.
- Enabling an inactive installation fails.

Collect MoClaw account email, GitHub username, account/org name, missing repo
name, whether the org is accessible or inactive, repository selection mode, and
a screenshot of GitHub connector settings with private data redacted.

## Do Not Say

- Do not say "GitHub connected" means "all repos connected."
- Do not ask the user to paste private GitHub tokens into chat.
- Do not say OAuth identity authorization is the same as GitHub App repository
  installation.
- Do not say inactive means uninstalled.
- Do not say disconnecting in MoClaw always uninstalls the GitHub App remotely.
- Do not ask for or accept raw GitHub OAuth, installation, PAT, App private key,
  webhook secret, cookie, or authorization-code material.

## Related Cards

- `moclaw.how_to.connect_github`
- `moclaw.reference.connectors_status`
- `moclaw.reference.github_authorization_scope`
