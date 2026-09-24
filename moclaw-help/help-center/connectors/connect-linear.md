---
id: help.connectors.connect_linear
title: Connect Linear
audience: user
status: verified
source_cards:
  - moclaw.how_to.connect_linear
  - moclaw.troubleshooting.connector_expired
  - moclaw.reference.connectors_status
  - moclaw.concepts.connectors_channels_skills
  - moclaw.playbooks.ask_for_screenshot_or_reference_id
last_reviewed_at: 2026-06-09
---

# Connect Linear

Use Linear when you want MoClaw to work with Linear issues, projects, or related
planning tasks when the connector is available for your account.

## Connect Linear

1. Open `/chat`.
2. Open the left sidebar.
3. Expand **Connectors**.
4. Find **Linear**.
5. Click **Connect**.
6. Complete the Linear authorization flow.
7. Return to MoClaw and confirm that the connector row shows connected.

## How Linear Access Works

Linear uses OAuth authorization for a Linear user and workspace. It does not use
the same organization/repository installation screen that GitHub uses.

After connecting, MoClaw can work with Linear content that belongs to the
connected workspace and is allowed by the authorized user's permissions. An
OAuth connection does not guarantee that every Linear workspace, team, project,
or issue is visible.

Current Linear write actions are attributed to the authorized Linear user by
default, so comments or updates may appear as that user in Linear.

The current Linear OAuth flow requests Linear permissions for reading, writing,
creating issues, and creating comments. Provider OAuth and refresh tokens stay
server-side; MoClaw agents and connector tooling should use the platform's
documented Linear actions rather than handling raw tokens or arbitrary Linear
GraphQL queries.

## If Linear Is Missing

Linear connector availability can depend on account and environment. If the
Linear row is not visible, send support your account email, current environment
or app URL, and a screenshot of **left sidebar > Connectors**.

## If MoClaw Cannot See Linear Content

OAuth connection does not always mean every workspace, team, project, or issue
is available. Check:

- The Linear account or workspace you authorized.
- Whether the content belongs to that workspace.
- Whether provider-side permissions changed.
- Whether the connector row shows expired or needs reconnecting.
- Whether the target team, project, workflow state, user, or label was resolved
  to a Linear provider ID instead of a display name or team key.
- Whether the agent used a documented Linear action and accepted parameter,
  rather than an upstream Linear GraphQL field that MoClaw has not exposed.

For create or update failures, the agent may need to resolve IDs first. For
example, `teamId`, `projectId`, `stateId`, `assigneeId`, and label IDs are
provider IDs, not plain names.

Do not send OAuth tokens, refresh tokens, API keys, passwords, cookies, or full
raw logs to support. A redacted screenshot of the connector row or visible error
is safer.

## Related Articles

- `connectors/connectors-overview.md`
- `connectors/reconnect-or-disconnect-connectors.md`
- `troubleshooting/common-errors.md`
