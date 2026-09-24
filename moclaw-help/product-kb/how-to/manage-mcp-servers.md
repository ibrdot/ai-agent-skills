---
id: moclaw.how_to.manage_mcp_servers
title: Manage MCP Servers
type: how_to
product_area: connectors
audience: user
status: verified
owner: product
last_reviewed_at: 2026-06-09
source_paths:
  - maxgent/client/webapp/src/components/connectors/mcp-connector.tsx
  - maxgent/client/webapp/src/components/connectors/connectors-section.tsx
  - maxgent/client/webapp/src/i18n/locales/en.json
  - maxgent/server/app-server/app/domains/connector/mcp_router.py
  - maxgent/server/app-server/app/domains/connector/mcp_schema.py
  - maxgent/server/app-server/app/domains/connector/services/mcp_access.py
  - maxgent/server/app-server/app/domains/connector/services/mcp_security.py
  - maxgent/server/app-server/app/domains/connector/services/mcp_client.py
  - maxgent/server/app-server/app/domains/connector/services/mcp_hub.py
  - maxgent/server/app-server/app/domains/connector/README.md
  - maxgent/server/app-server/app/domains/connector/README-MCP.md
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Manage MCP Servers

## Direct Answer

If **MCP** is visible in the current account UI, open **left sidebar >
Connectors > MCP** and click **Manage**. From the MCP dialog, you can add a
server, edit it, test it, sync tools, enable/disable it, or delete it.

## Before You Start

- Current MCP management is for remote HTTPS Streamable HTTP MCP servers.
- Supported auth modes in the UI are none, bearer token, API key header, and API
  key query parameter.
- API key body injection is reserved in schema but is not exposed by the current
  UI and is rejected by standard MCP JSON-RPC calls.
- MCP visibility can differ by account and environment. Do not promise the row
  unless the user can see it or a newer verified source confirms it.
- Saving a server is not enough. It must test/sync successfully and become
  active with a nonzero tool count before the agent can use its tools.

## Endpoint Rules

- Use an `https://` endpoint.
- The host must be publicly resolvable.
- The endpoint cannot be `localhost`, a private/reserved IP, or a cloud metadata
  address.
- The URL cannot include username/password or a fragment.
- Redirects are rejected.
- Current V1 calls expect JSON Streamable HTTP responses; SSE/streaming
  responses are rejected.
- Very large responses, very large schemas, or too many tools can fail sync.

## Steps

1. Open `/chat`.
2. Open the left sidebar.
3. Expand **Connectors**.
4. If the **MCP** row is visible, click **Manage**.
5. Click **Add Server**.
6. Enter name, endpoint URL, optional service id, description, and auth settings.
7. Save the server.
8. Use the row actions to test, refresh/sync, enable/disable, edit, or delete.

## Status And Action Meaning

| State or action | Meaning |
|---|---|
| **Draft** | Saved configuration exists, but tools are not usable yet. |
| **Test** | Fetches tools to verify endpoint/auth behavior. A successful test does not activate a draft/error server by itself and does not guarantee every future tool call succeeds. |
| **Refresh/Sync** | Fetches and caches usable tools. This is the normal step before tools appear to the agent; successful sync can activate the server. |
| **Active** | Server is enabled and has synced usable tools. |
| **Disabled** | Configuration exists but tools are not exposed to the agent. |
| **Error** | Test/sync failed; use the visible error to check URL policy, DNS, auth, timeout, invalid JSON, empty tools, response size, or tool count limits. |
| **Delete** | Removes the server from the user's active management list. |

## If You Cannot See It

- MCP may be hidden by account, environment, adapter, or backend connector
  metadata.
- If a server is present but not active, run test and sync from the MCP dialog.
- If auth fails, verify the selected auth mode and secret placement.
- If the endpoint is local, `http`, private-network-only, or a command-line
  stdio MCP config, it does not fit the current remote MCP UI.

## Do Not Say

- Do not tell users to paste arbitrary local command-line MCP server configs
  into this UI unless product ships that path.
- Do not expose internal broker/runtime details in normal support answers.
- Do not ask users to send bearer tokens, API keys, or secret query strings.
- Do not say save or test alone makes tools available to the agent.
- Do not say SSE/streaming MCP responses are supported in the current V1 path.

## Related Cards

- `moclaw.concepts.connectors_channels_skills`
- `moclaw.reference.connectors_status`
- `moclaw.troubleshooting.mcp_server_connection_or_tools_missing`
