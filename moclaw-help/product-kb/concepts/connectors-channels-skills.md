---
id: moclaw.concepts.connectors_channels_skills
title: Connectors, Channels, And Skills
type: concept
product_area: connectors
audience: user
status: verified
owner: product
last_reviewed_at: 2026-06-09
source_paths:
  - maxgent/client/webapp/src/components/workspace/panel.tsx
  - maxgent/client/webapp/src/components/workspace/skills-tab-view.tsx
  - maxgent/client/webapp/src/components/connectors/connectors-section.tsx
  - maxgent/client/webapp/src/components/channels/channel-rows.tsx
  - maxgent/client/webapp/src/lib/connector-registry.ts
  - maxgent/client/webapp/src/lib/connector-visibility.ts
  - maxgent/client/webapp/src/components/chat/chat-input.tsx
  - maxgent/server/app-server/app/domains/connector/README.md
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web, telegram, slack]
---

# Connectors, Channels, And Skills

## Direct Answer

- A **Connector** is third-party service access, such as Google Workspace,
  GitHub, or Linear. MCP server management should only be described when a
  current verified UI shows an MCP row.
- A **Channel** is where the user chats with MoClaw, such as Telegram, Slack,
  Lark, or Discord.
- A **Skill** is a loadable instruction or script package that guides the agent
  through a class of tasks.

## Why This Matters

Users often mix "can I chat with it in Slack?" with "can it access
Slack/GitHub data?" Support answers should separate:

- chat entry-point questions: Channel;
- third-party account, data, or permission questions: Connector;
- task-specific workflow or tool-behavior questions: Skill.

## Current Entry Points

- Channels: left sidebar Channels section.
- Connectors: left sidebar Connectors section.
- Skills: left sidebar Skills section shows loaded skills and can open
  their entry files.
- Commands: the chat composer `/` opens the command menu; current commands are not the
  same as Skills.

Google Workspace is the current user-visible Google row. Explain Gmail,
Calendar, Tasks, Drive, Docs, Sheets, and Slides from this connector; do not
send users looking for a separate Gmail connector row.

## Current Surface Matrix

| Surface | Current user-facing examples | What it means |
|---|---|---|
| Connector row | Google Workspace, GitHub, Linear; MCP only if visible in the current account UI | Authorizes service access or external tools. A visible row still may need provider-side setup. |
| Channel row | Telegram, Slack, Lark, Discord | Lets the user talk to MoClaw from another chat surface. It does not grant data access to that service by itself. |
| Skill | Loaded System/User skills in the left sidebar | Gives the agent instructions or tool-handling behavior for a task. It is not an OAuth connection. |
| Slash command | `/new`, `/stop`, and command-menu items | Controls the current chat flow. It is not a third-party service connection. |

The current frontend connector registry checked on 2026-06-15 is
`google-workspace`, `github`, and `linear`. The current channel registry is
`telegram`, `slack`, `lark`, and `discord`, with Lark hidden in production by
the frontend visibility rule. Older MCP materials should not be treated as
proof that every account has an MCP row.

## Boundaries

- Different environments and accounts can show different connectors/channels.
- Do not equate a service appearing in UI with availability for every user.
- Connectors such as GitHub also have provider-side account, organization, and
  installation scope.
- Local disconnect and provider-side revocation are not always the same thing.
  If remote access is unconfirmed or the GitHub App remains installed, ask the
  user to confirm in the provider settings.

## Related Cards

- `moclaw.reference.connectors_status`
- `moclaw.reference.skills_and_slash_commands`
- `moclaw.ui.connectors_panel`
- `moclaw.ui.workspace_sidebar`
