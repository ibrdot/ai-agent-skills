---
id: help.connectors.github_repository_access
title: GitHub Repository Access
audience: user
status: verified
source_cards:
  - moclaw.reference.github_authorization_scope
  - moclaw.how_to.connect_github
  - moclaw.troubleshooting.github_repo_not_visible
last_reviewed_at: 2026-06-09
---

# GitHub Repository Access

Connecting GitHub has three layers:

- your GitHub identity;
- the GitHub App installation for a personal account or organization;
- the repository scope for that installation.

MoClaw cannot necessarily see every repository just because your GitHub identity
is connected.

MoClaw uses the GitHub identity authorization to know which GitHub user is
connected and which GitHub App installations that user can see. Repository
operations are bounded by the GitHub App installation and repository selection.

## Check Repository Scope

1. Open `/chat`.
2. Open the left sidebar.
3. Expand **Connectors**.
4. Open **GitHub** settings.
5. Confirm the connected GitHub identity is the account you expected.
6. Check whether the personal account or organization is listed.
7. Check whether it is accessible or appears under accounts/organizations to
   enable.
8. If it is inactive, use **Enable**. MoClaw rechecks GitHub before restoring
   the local binding.
9. Check whether repository access is all repositories or selected
   repositories.
10. If needed, use **Manage Scope** or **Configure in GitHub** to add the
    missing repository.

## Common States

| State | What It Means |
|---|---|
| Identity connected | MoClaw knows your GitHub user; repo access is still controlled by installations. |
| Accessible account/org | MoClaw can use authorized repositories in that account/org. |
| Account/org to enable | GitHub App exists in GitHub, but MoClaw local binding is inactive. |
| All repositories | The installation grants access to all repos in that account/org. |
| Selected repositories | Only selected repos are available. |
| Manage Scope | Opens the account action menu. Use **Configure in GitHub** from there to change the GitHub-side repository selection. |

## Personal Account vs Organization

A repository can belong to your personal GitHub account or an organization. If
it belongs to an organization, the GitHub App may need to be installed or
configured by someone with the right organization permissions.

If you disconnect an organization in MoClaw, that removes the local MoClaw
binding. It does not necessarily uninstall the GitHub App from GitHub. Use
GitHub's installation settings to uninstall the App or change repository scope.

If the repository was added or removed in GitHub very recently, refresh the
connector state and reopen GitHub settings. MoClaw also performs periodic
installation snapshot sync, but support should not promise that reconnect or
refresh immediately restores every permission without checking the visible
state.

## What To Send Support

- MoClaw account email.
- GitHub user or organization name.
- Missing repository name.
- Whether the account/org is accessible or inactive.
- Whether the installation uses all repositories or selected repositories.
- Screenshot of the GitHub connector state, with private data redacted.

Do not send GitHub tokens, OAuth codes, cookies, App private keys, webhook
secrets, or personal access tokens.

## Related Articles

- `connectors/connect-github.md`
- `connectors/connectors-overview.md`
