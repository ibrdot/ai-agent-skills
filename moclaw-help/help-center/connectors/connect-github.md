---
id: help.connectors.connect_github
title: Connect GitHub
audience: user
status: verified
source_cards:
  - moclaw.how_to.connect_github
  - moclaw.reference.github_authorization_scope
  - moclaw.troubleshooting.github_repo_not_visible
  - moclaw.troubleshooting.connector_expired
  - moclaw.reference.connectors_status
last_reviewed_at: 2026-06-09
---

# Connect GitHub

Use the GitHub connector when it is visible for your account and you want
MoClaw to work with repositories, pull requests, issues, or code-related tasks.

## Connect GitHub

1. Open `/chat`.
2. Open the left sidebar.
3. Expand **Connectors**.
4. Find **GitHub** if it is available for your account.
5. Click **Connect** and finish the GitHub authorization flow.
6. Reopen GitHub settings from the connector row.
7. Confirm the connected GitHub identity shown in the settings header.
8. Check **Accessible Accounts & Organizations**.
9. Use **Install GitHub App** if the account or organization is not listed.
10. Use **Enable** if the account or organization appears under **Accounts &
    Organizations to Enable**.
11. Use **Manage Scope** and then **Configure in GitHub** if repository access
    needs to be changed.

## Why A Repository May Be Missing

GitHub access has three layers:

- Your GitHub identity connection.
- GitHub App installation for a personal account or organization.
- Repository scope: all repositories or selected repositories.

If MoClaw cannot see a repository, check whether the GitHub App is installed for
the right user or organization and whether the installation has access to all
repositories or only selected repositories.

If GitHub authorization succeeded but you never saw an organization or
repository selection page, the identity step may have completed before the App
installation or repository-scope step. Open GitHub connector settings and check
the account/organization list.

The normal flow is OAuth-first: MoClaw first confirms your GitHub identity, then
discovers the GitHub App installations visible to that identity. Repository
work is controlled by the GitHub App installation and repository scope, not by
the identity authorization alone.

If you do not see **GitHub** in **Connectors**, it may not be enabled for your
current account or environment. Send support your account email and a screenshot
of the visible Connectors list rather than starting from GitHub tokens or OAuth
codes.

## GitHub Settings

| Section | Meaning |
|---|---|
| Connected identity | The GitHub user connected to your MoClaw account. |
| Accessible Accounts & Organizations | GitHub App installations enabled in MoClaw for the current user. |
| Accounts & Organizations to Enable | GitHub App installations that still exist on GitHub but are inactive in MoClaw. |
| Install GitHub App | Starts GitHub's App installation target picker for a personal account or organization. |
| Enable | Restores the local MoClaw binding for an inactive installation when you still have GitHub-side access. |
| Manage Scope | Opens the per-account menu for repository scope actions. |
| Selected repositories | Only selected repos are available to MoClaw. |
| Configure in GitHub | Opens GitHub's installation settings to change repository scope. |

The connector-level **Disconnect** removes the GitHub identity authorization and
local connector credentials. The organization-level **Disconnect...** removes
that local account/organization binding in MoClaw. In both cases, GitHub-side
App installation or repository access may still need to be reviewed in GitHub.

## What To Send Support

- Your MoClaw account email.
- The GitHub user or organization name.
- Whether the GitHub App is installed.
- Whether repository access is set to all repositories or selected
  repositories.
- Whether the account/organization is listed as accessible or inactive.
- A screenshot of the connector state, with private data redacted.

Do not send GitHub tokens, OAuth codes, cookies, App private keys, webhook
secrets, or personal access tokens.

## Related Articles

- `connectors/connectors-overview.md`
- `connectors/reconnect-or-disconnect-connectors.md`
- `troubleshooting/common-errors.md`
