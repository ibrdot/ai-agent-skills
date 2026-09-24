---
id: moclaw.reference.github_authorization_scope
title: GitHub Authorization Scope
type: reference
product_area: connectors
audience: support
status: verified
owner: product
last_reviewed_at: 2026-06-09
source_paths:
  - maxgent/server/app-server/app/domains/connector/docs/providers/github/auth.md
  - maxgent/server/app-server/app/domains/connector/README.md
  - maxgent/server/app-server/app/domains/connector/router.py
  - maxgent/server/app-server/app/domains/connector/services/github_connect.py
  - maxgent/server/app-server/app/domains/connector/services/providers/oauth2/github.py
  - maxgent/client/webapp/src/components/connectors/README.md
  - maxgent/client/webapp/src/components/connectors/connector-settings-modal.tsx
  - maxgent/client/webapp/src/stores/connector-store.ts
  - maxgent/client/webapp/src/i18n/locales/en.json
  - product-kb/how-to/connect-github.md
  - product-kb/troubleshooting/github-repo-not-visible.md
applies_to:
  plans: [free, trial, pro]
  environments: [test, prod]
  platforms: [web]
---

# GitHub Authorization Scope

## Direct Answer

GitHub access has three practical layers:

- **GitHub identity authorization**: confirms which GitHub user is connected
  to the MoClaw account.
- **GitHub App installation**: installs the GitHub App for a personal account
  or organization.
- **Repository selection**: controls whether the installation grants access to
  all repositories or only selected repositories.

Connecting GitHub identity does not automatically authorize every repository.

In the current implementation, **Connect GitHub** starts GitHub App user
authorization with no extra OAuth scopes. That user token is used for identity
and installation discovery, not as the direct agent runtime credential for
repository automation.

## Current UI Concepts

| UI Concept | Meaning | Support Implication |
|---|---|---|
| GitHub identity | The connected GitHub user shown in the connector header, such as `github.com / @name`. | This is not the repo access boundary by itself. |
| Accessible Accounts & Organizations | GitHub App installations that are enabled in MoClaw for the current user. | MoClaw can use authorized repos inside these accounts/orgs. |
| Accounts & Organizations to Enable | GitHub App is still installed on GitHub, but the current user's MoClaw local binding is inactive. | Use **Enable** if the user wants to restore access and still has GitHub-side permission. |
| Manage Scope / Configure in GitHub | Opens GitHub's installation settings for that account/org. | Repository scope is adjusted in GitHub, not only inside MoClaw. |
| Disconnect organization | Removes the local MoClaw binding for that installation. | It does not necessarily uninstall the GitHub App remotely. |

## Account And Repository Scope

GitHub App installations can be installed for:

- a personal GitHub account;
- a GitHub organization.

The installation can grant access to:

- all repositories in that account/org;
- only selected repositories.

The product UI can show enabled and available installations. An available
installation can mean the GitHub App still exists in GitHub, but the local
MoClaw binding for the current user is not enabled.

`repository_selection: all` means the GitHub App installation is configured for
all repositories in that account/org. `repository_selection: selected` means
only selected repositories are available. Support should still avoid saying
"all repos" unless the relevant account/org is enabled and the user's question
is scoped to that account/org.

## Flow Boundary

The normal user-facing flow can involve both OAuth and GitHub App installation:

1. **Connect GitHub** authorizes the GitHub user identity.
2. MoClaw discovers GitHub App installations visible to that user.
3. If the target account/org is missing, the user installs or configures the
   GitHub App.
4. If an installation exists but is inactive in MoClaw, the user enables it.
5. If the repo is missing, the user adjusts repository scope in GitHub.

OAuth alone can succeed without showing the GitHub org/repo selection page. In
that case, do not call the flow broken; ask the user to open GitHub connector
settings and check accessible or inactive accounts/organizations.

## Token And Agent Boundary

- GitHub user access tokens are stored server-side and used to identify the
  GitHub user and list visible App installations.
- Repository work is bounded by GitHub App installations. The backend can mint
  short-lived installation access tokens for the relevant installation.
- Sandbox and agent runtime should use MoClaw's connector broker path. Do not
  claim the agent receives raw GitHub OAuth, refresh, installation, App private
  key, webhook secret, or PAT credentials.
- If support needs diagnostics, collect visible connector state and redacted
  screenshots, not provider secrets.

## Recommended Support Wording

When a user says a repo is missing:

1. Ask whether the repo belongs to a personal account or organization.
2. Ask the user to open **left sidebar > Connectors > GitHub > Settings**.
3. Check the connected GitHub identity in the header.
4. Check whether the account/org appears under accessible accounts/orgs or
   accounts/orgs to enable.
5. If it is inactive, use **Enable**.
6. If it is accessible, check whether repository selection is all repositories or
   selected repositories.
7. If selected, use GitHub's **Manage Scope** / **Configure in GitHub**
   flow to include the missing repo.
8. Retry after the connector refreshes. If the user just changed GitHub-side
   installation scope, reopen the connector settings to force a fresh visible
   state check before escalating.

## Safe Diagnostics

Ask for:

- MoClaw account email.
- GitHub username and whether the missing repo is personal or organization-owned.
- Organization/account name.
- Missing repository name.
- Whether the account/org appears as accessible or inactive.
- Whether repository selection is all or selected.
- Screenshot of the GitHub connector settings with private data redacted.

Do not ask for GitHub personal access tokens, OAuth codes, App private keys,
webhook secrets, cookies, or raw installation tokens.

## Do Not Say

- Do not say "GitHub connected" means "all repos connected."
- Do not ask users to paste personal access tokens into chat.
- Do not say repository scope is controlled only inside MoClaw.
- Do not treat local disconnect as guaranteed remote uninstall; GitHub-side app
  installation can still exist.
- Do not say OAuth user authorization is the same thing as GitHub App
  installation.
- Do not say inactive/available installation means the app is uninstalled.
- Do not say GitHub user access tokens, installation tokens, App private keys,
  webhook secrets, or PATs are safe to paste into support chat.
- Do not say the agent or sandbox receives the raw GitHub user access token.

## Related Cards

- `moclaw.how_to.connect_github`
- `moclaw.troubleshooting.github_repo_not_visible`
- `moclaw.reference.connectors_status`
