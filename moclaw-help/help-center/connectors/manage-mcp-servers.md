---
id: help.connectors.manage_mcp_servers
title: Manage MCP Servers
audience: user
status: verified
source_cards:
  - moclaw.how_to.manage_mcp_servers
  - moclaw.troubleshooting.mcp_server_connection_or_tools_missing
  - moclaw.concepts.connectors_channels_skills
  - moclaw.reference.connectors_status
last_reviewed_at: 2026-06-09
---

# Manage MCP Servers

MCP servers can extend MoClaw with additional tools when the MCP connector is
available for your account and environment.

The current MCP management UI is for remote HTTPS Streamable HTTP MCP servers.
Do not assume that every local command-line MCP server configuration can be
pasted into this UI.

Saving a server is only the first step. The server also needs to test/sync
successfully and become active with tools before MoClaw can use it.

## Add An MCP Server

1. Open `/chat`.
2. Open the left sidebar.
3. Expand **Connectors**.
4. Find **MCP** if it is available for your account.
5. Click **Manage**.
6. Click **Add Server**.
7. Enter the server name, endpoint URL, optional service id, description, and
   authentication settings.
8. Save the server.
9. Test and sync the server from the row actions.

## Endpoint Requirements

- Use an `https://` endpoint.
- The endpoint must be public, not `localhost` or a private network address.
- The endpoint should not redirect.
- The endpoint must be a Streamable HTTP MCP endpoint that returns JSON
  responses for the current V1 path.
- Local command-line or stdio MCP configs do not fit this UI.

## Supported Auth Modes

The MCP dialog can support:

- No auth.
- Bearer token.
- API key header.
- API key query parameter.

Do not share secrets in chat or screenshots. Redact tokens and API keys before
sending anything to support.

## Status And Actions

| Status or action | Meaning |
|---|---|
| **Draft** | Saved, but not usable yet. |
| **Test** | Checks whether MoClaw can reach the server and fetch tools. A successful test does not activate a draft/error server by itself. |
| **Refresh/Sync** | Fetches and caches tools so they can be exposed to the agent; a successful sync can make the server active. |
| **Active** | Enabled with synced tools. |
| **Disabled** | Saved but not exposed to the agent. |
| **Error** | Test or sync failed. Check the visible error copy. |

## If Tools Do Not Appear

- Test the server.
- Sync or refresh tools from the MCP dialog.
- Check whether the server is enabled.
- Check the endpoint URL and auth mode.
- Check whether the server row shows **Active** and a nonzero tool count.
- Ask support if you expected MCP but the row is missing for your account.

A successful test does not guarantee every future tool call will work. Some
tool calls may still need extra input, confirmation before changing external
state, updated authentication, or a non-streaming response.

## Related Articles

- `connectors/connectors-overview.md`
- `connectors/mcp-server-connection-errors.md`
- `security/privacy-and-access.md`
