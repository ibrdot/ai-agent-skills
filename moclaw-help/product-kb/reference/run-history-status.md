---
id: moclaw.reference.run_history_status
title: Run History Status
type: reference
product_area: workspace
audience: support
status: verified
owner: product
last_reviewed_at: 2026-06-09
source_paths:
  - maxgent/client/webapp/src/components/workspace/panel.tsx
  - maxgent/client/webapp/src/components/showcase/showcase-workspace.tsx
  - maxgent/client/webapp/src/components/workspace/schedules-tab-view.test.tsx
  - maxgent/client/webapp/src/i18n/locales/en.json
  - maxgent/server/app-server/app/domains/agent_runtime/routes/runtime_v2.py
  - maxgent/agent/runtime-client/src/session-api.ts
  - product-kb/_index/conflicts-and-decisions.md
  - product-kb/reference/scheduled-tasks.md
  - product-kb/reference/message-display-and-actions.md
  - product-kb/reference/chat-conversations-and-history.md
  - product-kb/playbooks/feature-not-shipped-yet.md
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Run History Status

## Direct Answer

A dedicated **Run History** section is not currently confirmed in the real
left sidebar. The current left sidebar renders Channels, Connectors, Artifacts,
Schedules, and Skills. Support should not tell users to open **Run History**
unless current product UI confirms it.

There are implementation traces for Run History:

- `workspace.runHistory` exists in locale files;
- a showcase/demo component renders mock **Run History** rows;
- runtime task-log APIs exist internally.

Those traces are not enough to treat Run History as a shipped user-visible
panel.

## Current Alternatives

For users looking for previous work, task output, or execution details, route
them to currently confirmed surfaces:

- chat history and **Load earlier messages** for prior conversation context;
- per-message **Thinking** and **Used tools** activity for recent command,
  output, error, or running status;
- **left sidebar > Schedules** for scheduled task status, next run, last run,
  failure details, and cancellation when available;
- the target chat Session for delivered scheduled-task results when a schedule
  was created with result delivery;
- **left sidebar > Artifacts** for generated files and outputs.

## Support Wording

Use wording like:

> I do not see a confirmed Run History section in the current `/chat` UI. For
> now, use chat history and Used tools for recent run details, left sidebar >
> Schedules for scheduled task status, and Artifacts for generated outputs.

If the user saw **Run History** in a screenshot, demo, or older doc, explain
that visible availability depends on the current UI, account, and environment.

## Task Logs Boundary

Internal runtime task-log routes exist, but customer-facing answers should not
expose raw task-log endpoints or promise a visible log browser. If a user needs
support for a repeated failed run, collect safe visible details instead:

- account email;
- approximate time;
- current workspace or active Session if they can identify it;
- visible error copy;
- screenshot of the relevant chat, Schedules row, or Used tools popover.

Do not ask users to send secrets, API keys, OAuth tokens, signed URLs, or full
raw logs that may contain private data.

## Do Not Say

- Do not promise a **Run History** page or left-sidebar section exists for every
  user.
- Do not tell users to open **Run History**.
- Do not infer shipped UI from i18n strings, demo/showcase components, or
  internal task-log APIs.
- Do not expose raw task-log API paths in customer-facing answers.
- Do not ask users to paste full logs, credentials, tokens, cookies, or signed
  URLs.

## Related Cards

- `moclaw.playbooks.feature_not_shipped_yet`
- `moclaw.reference.scheduled_tasks`
- `moclaw.reference.message_display_and_actions`
- `moclaw.reference.chat_conversations_and_history`
- `moclaw.how_to.use_artifacts`
