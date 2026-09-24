---
id: moclaw.foundation.glossary
title: MoClaw Glossary
type: reference
product_area: foundation
audience: support
status: verified
last_reviewed_at: 2026-07-23
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# MoClaw Glossary

| Term                 | User-Facing Meaning                                                                                                                               | Avoid Saying                                    |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------- |
| Chat                 | The main surface where users talk to MoClaw and watch work happen.                                                                                | Agent page, console                             |
| Session              | A user-visible chat workspace in Recents. It can have a title, source, runtime binding, messages, files, schedules, and channel badges.           | Browser session, auth session                   |
| Thread               | A conversation branch inside a Session; message history loads and continues by Thread.                                                            | Chat room                                       |
| Message              | A persisted chat item sent by the user or AI.                                                                                                     | Event, row, bubble                              |
| Streaming Message    | A temporary AI response while generation is in progress; it becomes a persisted message when complete.                                            | Chunk, live text                                |
| AI Cloud Computer    | The user's cloud AI computer where MoClaw runs browsers, files, terminals, tools, and tasks.                                                      | Ordinary server, virtual machine unless needed  |
| Workspace File       | A current file in the AI Cloud Computer workspace that may change as work continues.                                                              | Stable artifact                                 |
| Artifact             | A stable file snapshot that MoClaw explicitly delivers for preview, download, sharing, or later viewing.                                          | Current workspace file                          |
| Dock                 | A file-preview and file-management workspace owned by one Session; it appears on the right on wide screens and full-screen on narrow screens.     | Global panel, VNC panel                         |
| Connector            | A third-party OAuth/MCP integration such as GitHub, Linear, or Google Workspace.                                                                  | Channel                                         |
| Channel              | A chat entry point such as Telegram, Slack, Lark, or Discord.                                                                                     | Connector                                       |
| Skill                | Agent-loadable instructions, rules, or scripts; source can be System or User.                                                                     | Plugin unless the user says plugin              |
| Schedule             | A scheduled task, such as once, cron, or interval.                                                                                                | Reminder unless the exact feature says reminder |
| Credit               | Usage balance consumed by model, tool, or media work.                                                                                             | Subscription access                             |
| Computer Entitlement | The product-access gate for MoClaw. Without active entitlement, credits can be visible but locked.                                                | Credits balance                                 |

## Naming Rules

- Prefer **AI Cloud Computer** for user-facing answers; do not lead with
  sandbox, E2B, or runtime.
- You may say "cloud workspace" or "cloud computer" when explaining an issue,
  but do not make users think it is their local machine.
- Keep `Connector` and `Channel` separate. GitHub is a connector; Telegram is a
  channel. Slack can appear in channel and connector contexts, so answer from
  the specific UI surface.
