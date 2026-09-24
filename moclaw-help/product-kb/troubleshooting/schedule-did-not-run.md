---
id: moclaw.troubleshooting.schedule_did_not_run
title: Schedule Did Not Run
type: troubleshooting
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
  - maxgent/fleet/src/core/scheduler/deliver.ts
  - maxgent/fleet/src/core/scheduler/scanner.ts
  - maxgent/client/webapp/src/i18n/locales/en.json
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Schedule Did Not Run

## Symptom

The user expected a scheduled task to run, but no result appeared, or the
Schedules row shows failed, paused, or expired.

## Likely Causes

- The schedule is paused or canceled.
- The schedule has no next run and is expired.
- The last run failed and shows an error in hover details.
- The schedule expression/timezone behavior is not what the user expected.
- The backing workspace or agent run failed.
- The run completed, but delivery back to the target Session or channel failed.
  This can appear as a `delivery: ...` warning while the run itself remains
  successful.
- The task belongs to a Session that is no longer active/runtime-bound, so it is
  not returned by the current Schedules list.
- The schedule was canceled from the row action and is no longer returned in the
  default task list.

## Recovery Steps

1. Open **left sidebar > Schedules**.
2. Find the schedule by name.
3. Check the visible status: active, failed, paused, or expired.
4. Review next run and last run. Capture visible error copy if the page shows
   one.
5. If it shows a `delivery:` warning, check the expected target Session or
   channel. Treat this as result-delivery troubleshooting, not automatically as
   a failed run.
6. If it is failed, capture the visible error and ask the user to retry or
   recreate the schedule through chat.
7. If it is paused/expired, ask the user to create a new schedule through chat
   and confirm it appears in the Schedules list.
8. If the task was created in an older Session and no longer appears, explain
   that the current list is not a full historical task archive.
9. If the task was canceled, explain that the current sidebar does not expose a
   restore control; recreate it through chat if needed.

## Escalate When

- The schedule is active with a past next-run time but never executes.
- The same schedule fails repeatedly with the same backend-visible error.
- Delivery warnings repeat even though the run itself appears successful.
- The user needs exact timezone/cron interpretation and no reference card exists.

Collect safe context: account email, current Session if visible,
schedule name, visible status, next-run/last-run details, visible error copy,
approximate expected run time, timezone, and a redacted screenshot.

## Do Not Say

- Do not guess the user's timezone.
- Do not claim there is a sidebar "New schedule" button unless product ships it.
- Do not promise pause, resume, edit, duplicate, or restore controls.
- Do not say a scheduled task ran inside the original chat; runs can be isolated
  and then deliver results back to a target Session.
- Do not ask for raw task logs, passwords, OAuth tokens, API keys, cookies,
  signed URLs, or private prompt contents.

## Related Cards

- `moclaw.reference.scheduled_tasks`
- `moclaw.how_to.manage_schedules`
- `moclaw.ui.workspace_sidebar`
