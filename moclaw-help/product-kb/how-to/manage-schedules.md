---
id: moclaw.how_to.manage_schedules
title: Manage Schedules
type: how_to
product_area: automation
audience: user
status: verified
owner: product
last_reviewed_at: 2026-07-09
source_paths:
  - maxgent/client/webapp/src/modules/schedules/components/schedules-page.tsx
  - maxgent/client/webapp/src/modules/schedules/components/schedules-page-view.tsx
  - maxgent/client/webapp/src/modules/schedules/components/schedules-tab.tsx
  - maxgent/client/webapp/src/api/maxclaw-adapter.ts
  - maxgent/client/webapp/src/api/maxclaw/workspace-api.ts
  - maxgent/server/app-server/app/domains/agent_runtime/routes/runtime_v2.py
  - maxgent/fleet/src/core/agent/cron-tool.ts
  - maxgent/fleet/src/core/scheduler/deliver.ts
  - maxgent/client/webapp/src/i18n/locales/en.json
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Manage Schedules

## Direct Answer

Open **left sidebar > Schedules** to see scheduled tasks. This opens the
Schedules page, which shows schedule names, status, timing metadata, refresh,
and **Cancel** when cancellation is available.

To create a schedule, ask MoClaw in chat to schedule the task, then confirm the
created task appears in **left sidebar > Schedules**.

## Before You Start

- The current Schedules page is primarily a viewer/manager for existing
  schedules.
- Scheduled runs are isolated from the original chat context, but chat-created
  schedules can deliver their final result back to the Session where they were
  created when a delivery target is set.
- It displays active, failed, paused, and expired states.
- The UI shows broad schedule labels and next-run metadata from runtime task
  summaries; detailed cron wording appears only when the row data contains a
  detailed expression the view can parse.
- Schedules are read from active runtime-bound Sessions, not from a complete
  historical task archive.

## Steps

1. Open `/chat`.
2. Open the left sidebar.
3. Click **Schedules**.
4. Review each schedule row for status, frequency, next run, and last-run
   metadata.
5. Use the refresh button if the list looks stale.
6. Choose **Cancel** when the schedule should stop and the action is available.
7. To create a new schedule, ask in chat and then refresh/check the Schedules
   list. Include where the result should appear if that matters.

## If You Cannot See It

- If the page says no schedules, there are no current scheduled tasks returned
  by the active runtime-bound Sessions.
- If a schedule did not run, check its visible status first: failed, paused, or
  expired.
- If the row shows a `delivery:` warning, the run may have succeeded while
  delivery back to the target Session failed.
- If the task was created in a Session that no longer has an active runtime
  binding, it may not appear in the current Schedules list.
- If the user wants to create a schedule, the safest current support wording is:
  "Ask MoClaw in chat to schedule the task, then confirm it appears in
  left sidebar > Schedules."

## Do Not Say

- Do not claim there is a dedicated "New schedule" button in the sidebar unless
  product ships one.
- Do not promise pause, resume, edit, duplicate, or restore controls in the
  current Schedules page.
- Do not guess timezone behavior without a dedicated scheduling reference card.
- Do not say cancellation affects every same-name schedule; the current UI
  targets one task id in its owning Session.
- Do not describe a scheduled run as reusing the original chat context; result
  delivery is separate from run execution.

## Related Cards

- `moclaw.reference.scheduled_tasks`
- `moclaw.ui.workspace_sidebar`
- `moclaw.troubleshooting.schedule_did_not_run`
