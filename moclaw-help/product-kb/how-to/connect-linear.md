---
id: moclaw.how_to.connect_linear
title: Connect Linear
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
  - maxgent/server/app-server/app/domains/connector/docs/linear-auth-patterns.md
  - maxgent/server/app-server/app/domains/connector/router.py
  - maxgent/server/app-server/app/domains/connector/services/providers/oauth2/linear.py
  - maxgent/server/app-server/app/domains/connector/services/providers/actions/linear.py
  - maxgent/server/app-server/app/domains/connector/actions/linear/provider.yaml
  - maxgent/server/app-server/app/domains/connector/services/skills/linear/SKILL.md
applies_to:
  plans: [free, trial, pro]
  environments: [test, prod]
  platforms: [web]
---

# Connect Linear

## Direct Answer

Open the left sidebar, go to **Connectors**, find **Linear**, and use
**Connect**. Complete the Linear authorization flow, then return to MoClaw and
check the connector row for the connected status. Linear uses an OAuth2
authorization flow; it does not have GitHub's separate App installation and
repository-selection page.

The connection represents the authorized Linear user and the Linear
workspace/organization boundary available to that user. Current write operations
default to the authorized Linear user as the actor, so created issues, comments,
and updates can appear as that user in Linear.

Current Linear OAuth requests `read`, `issues:create`, `comments:create`, and
`write`. The backend stores and refreshes Linear OAuth credentials server-side.
Agent runtime and connector-cli use MoClaw's broker/action layer; they should
not receive raw Linear OAuth or refresh tokens.

## How Linear Access Works

| Layer | Meaning | Support Rule |
|---|---|---|
| Workspace / organization | The Linear resource boundary containing teams, issues, projects, users, labels, and cycles. | OAuth success does not guarantee every workspace, team, project, or issue is visible. |
| User | The Linear user who completed OAuth. | Check that the user authorized the expected Linear account. |
| Actor | The identity shown for Linear write operations. | Current default is `actor=user`; do not promise app-actor attribution unless product confirms a different path. |
| Credentials | OAuth tokens used by the backend to call Linear. | Provider credentials stay server-side; agents, sandboxes, support, and connector-cli do not receive raw Linear OAuth or refresh tokens. |
| Actions | Platform-defined Linear actions such as issue, project, user, team, and workflow-state operations. | Do not tell users or agents to run arbitrary GraphQL or invent params from upstream Linear docs. |
| Scopes | Current OAuth scopes include `read`, `issues:create`, `comments:create`, and `write`. | Do not promise actions outside the documented Linear action catalog. |

## Before You Start

- Linear availability can be environment/account-gated.
- The connector grants MoClaw permission to work with Linear through the
  authorized account or workspace.
- OAuth success does not prove that every Linear workspace, team, project, issue,
  or archived resource is visible to MoClaw.
- Creating or updating Linear resources often needs provider UUIDs. `teamId`,
  `assigneeId`, `stateId`, `projectId`, `labelId`, and creator/subscriber IDs
  are Linear provider IDs, not display names or team keys.
- Linear actions are schema-defined. Use documented action parameters and
  resolve IDs with list/search actions; do not build arbitrary GraphQL queries
  for normal support guidance.

## Steps

1. Open `/chat`.
2. Open the left sidebar.
3. Expand **Connectors**.
4. Click **Connect** on the Linear row.
5. Complete the Linear OAuth flow.
6. Return to MoClaw and verify that Linear shows as connected.
7. Open the connector settings menu if you need to disconnect or review
   authorized account details.

## If You Cannot See Linear Or Its Content

- Ask the user what environment/account they are using.
- If Linear is absent from the Connectors list, treat it as gated or not enabled
  for that user until product confirms the rollout.
- If authorization completes but tools cannot access Linear content, check the
  connected Linear workspace/account and provider-side permissions.
- Confirm that the target team, project, issue, user, workflow state, label, or
  cycle belongs to the connected workspace.
- If an issue create/update fails because of `teamId`, `projectId`, `stateId`,
  `assigneeId`, or `labelId`, resolve the provider UUID with the matching list
  action before retrying.
- If the row shows expired or warning status, use the connector reconnect flow.
- If the user changed Linear permissions, workspace membership, or provider
  access, reconnect and refresh the connector state.
- For support escalation, collect safe diagnostics: MoClaw account email,
  visible connector status, expected Linear workspace/team/project/issue,
  approximate time/timezone, and a redacted screenshot. Do not collect tokens.

## Do Not Say

- Do not promise every Linear workspace or team is visible after OAuth.
- Do not say Linear uses GitHub App installation, GitHub repository selection,
  or GitHub-style installation IDs.
- Do not say Linear write operations appear as an app actor by default.
- Do not ask for Linear OAuth tokens, refresh tokens, API keys, passwords,
  cookies, or full raw logs.
- Do not claim a Linear write succeeded until the connector or MCP response
  confirms it.
- Do not tell users or agents that a display name, project name, or team key can
  always be used as `teamId`, `projectId`, `stateId`, or `assigneeId`.
- Do not expose internal connector action names in normal support answers unless
  the user is asking for technical operator guidance.
- Do not say connector-cli, the sandbox, or support can safely receive Linear
  OAuth or refresh tokens.

## Related Cards

- `moclaw.reference.connectors_status`
- `moclaw.concepts.connectors_channels_skills`
- `moclaw.troubleshooting.connector_expired`
- `moclaw.playbooks.ask_for_screenshot_or_reference_id`
