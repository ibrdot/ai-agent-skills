---
id: moclaw.reference.scheduled_tasks
title: Scheduled Tasks
type: reference
product_area: automation
audience: support
status: verified
owner: product
last_reviewed_at: 2026-07-09
source_paths:
  - maxgent/client/webapp/src/modules/schedules/components/schedules-page.tsx
  - maxgent/client/webapp/src/modules/schedules/components/schedules-page-view.tsx
  - maxgent/client/webapp/src/modules/schedules/components/schedules-tab.tsx
  - maxgent/client/webapp/src/api/maxclaw-adapter.ts
  - maxgent/client/webapp/src/api/maxclaw/workspace-api.ts
  - maxgent/client/webapp/src/api/types.ts
  - maxgent/client/webapp/src/modules/schedules/shared/lib/schedule-tool-display.ts
  - maxgent/client/webapp/src/i18n/locales/en.json
  - maxgent/server/app-server/app/domains/agent_runtime/routes/runtime_v2.py
  - maxgent/server/app-server/app/domains/agent_runtime/schemas/runtime_v2.py
  - maxgent/fleet/src/core/agent/cron-tool.ts
  - maxgent/fleet/src/core/scheduler/scanner.ts
  - maxgent/fleet/src/core/scheduler/deliver.ts
  - maxgent/fleet/src/modules/scheduled-tasks/service.ts
  - maxgent/fleet/src/config/db/schema.ts
  - product-kb/how-to/manage-schedules.md
  - product-kb/troubleshooting/schedule-did-not-run.md
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Scheduled Tasks

## Direct Answer

MoClaw scheduled tasks appear in **left sidebar > Schedules**, which opens the
Schedules page. The page is a viewer/manager for existing tasks, not a confirmed
dedicated schedule builder. The safe creation path is to ask MoClaw in chat to
schedule the task, then confirm it appears in **left sidebar > Schedules**.

Current user-visible schedule tool labels include **Create schedule** and
**Cancel schedule** in chat **Used tools** activity.

The runtime tool names are `create_schedule` and `cancel_schedule`. Older
recorded `create_task` / `cancel_task` names may be displayed with schedule
wording by the web UI, but runtime callers should use the schedule names.

## Current Data Flow

The current web adapter reads tasks from the user-level v2 task list:

- `GET /api/v2/tasks/list`

That endpoint scans the user's active runtime-bound Sessions and returns task
summaries with an app-session id for each task. The Schedules page then maps
those task summaries to the web `Schedule` shape:

- each row keeps the owning app-session id so cancellation targets the correct
  Session;
- `scheduleType: once` becomes **Once**;
- `scheduleType: interval` becomes **Recurring interval**;
- `scheduleType: cron` becomes **Recurring schedule**;
- task name, prompt preview, next run time, last activity, terminal status, and
  last error can drive the visible schedule row and hover details.

The runtime task summary includes `taskId`, `taskName`, `promptPreview`,
`scheduleType`, `status`, running/run-key metadata, retry metadata,
`lastErrorMessage`, `nextRunAt`, and `lastActivityAt`. The web adapter maps
these summaries into its generic `Schedule` shape for the Schedules page.

The Schedules page refreshes on task-stat events and schedule-source Session
lifecycle events, refetches periodically while open, and exposes a manual
refresh button. It is not a full historical task archive; it lists active
runtime-bound Session tasks returned by the current endpoint.

## Run Isolation And Result Delivery

Scheduled runs should be described as isolated executions. A run can create its
own run Session and execute without reusing prior chat context. In the current
agent-managed cron path, a task can also carry a delivery target:

- chat-created cron jobs default to delivering the final reply back to the
  conversation where the job was created;
- a delivery target can be cleared or pointed at an explicit Session by the
  agent/tool path when supported;
- UI/REST-created jobs may have no delivery target, so the run Session can be
  the only durable record;
- delivery failure is recorded as a `delivery: ...` last-error warning while the
  run status can remain successful; do not treat that as the task itself
  failing;
- silent runs are recorded but should not be promised as visible delivered
  messages.

Do not say a scheduled run executes inside the original chat. The safer wording
is: the run is isolated, and its result may be delivered back into the target
Session when the job has a delivery target.

## What The Schedules Page Shows

The Schedules page can show:

- **No schedules** when there are no current tasks to display;
- schedule name;
- status dot;
- formatted cadence such as **Once**, **Recurring interval**, **Recurring
  schedule**, plus next-run metadata when available;
- relative next-run copy such as `in 10min`, `tomorrow`, or `2d ago`;
- next run and last run fields;
- a **Cancel** action when the adapter exposes cancellation.

The view component can format common raw cron or `every N min/h` expressions,
but the current v2 adapter maps runtime `scheduleType` to the broader labels
above. Do not promise daily/weekly cron wording unless the current UI actually
shows it.

The panel sorts non-expired schedules before expired ones and then by schedule
time metadata.

## Display States

| State | Source Rule | User Meaning |
|---|---|---|
| Active | Not failed, not paused, not expired | The task is scheduled/running/retryable or has a next run. |
| Failed | `last_result.success === false` | The last terminal task run failed and may show an error in hover details. |
| Paused | `enabled === false` | The task is disabled/paused. |
| Expired | Has `last_run_at` and no `next_run_at` | A one-time/completed task or a task with no future run. |

## Cancellation

Cancellation from the row calls:

- `POST /api/v2/sessions/{session_id}/tasks/{task_id}/delete`

On success, the web UI removes the schedule from the local list and reloads the
page. This HTTP delete path soft-deletes the durable prompt-task row so default
task queries stop returning it.

This is different from a chat **Cancel schedule** tool call: `cancel_schedule`
targets active schedule work, can project the task as aborted, and may keep a
final cancellation state in the runtime task surface. Do not describe both paths
as the same UI operation.

Do not promise self-serve pause, edit, duplicate, or resume controls unless
current UI sources confirm them.

## Creation Guidance

User-facing creation wording:

> Ask MoClaw in chat to schedule the task, then check **left sidebar > Schedules**
> to confirm it appears.

Good prompts include the task, timing, and delivery expectation, such as:

- "Every weekday at 9 AM, summarize my calendar and unread Gmail."
- "Tomorrow at 5 PM, remind me to send the invoice."
- "Every 2 hours during work hours, check this website for changes."

Do not promise exact timezone interpretation unless the user has provided the
timezone or the UI shows one.

If the user cares where the result appears, ask them to include that expectation
in the chat request, for example "send the result back here" or "post the result
to this channel." Do not promise a visible Schedules-page control for changing
the delivery target unless current UI sources confirm it.

Runtime schedule inputs support `once`, `cron`, and `interval` schedules.
Relative one-off delays are measured from the `create_schedule` tool execution
time. Intervals without `startAt` use a relative first run rather than snapping
to the next wall-clock boundary.

## Do Not Say

- Do not claim there is a dedicated **New schedule** button in the sidebar.
- Do not promise pause, resume, edit, duplicate, or timezone controls in the
  current Schedules page.
- Do not describe Schedules as a complete account-wide historical task archive;
  current web data comes from active runtime-bound Sessions.
- Do not say scheduled runs reuse the original chat context; runs are isolated,
  and result delivery is a separate target-Session behavior.
- Do not guess the user's timezone or cron interpretation when it is not shown.
- Do not promise a canceled task can be restored from the current UI.
- Do not ask users to send secrets when recreating a scheduled task prompt.
- Do not call internal task logs a customer-facing self-serve Run History
  surface.

## Related Cards

- `moclaw.how_to.manage_schedules`
- `moclaw.troubleshooting.schedule_did_not_run`
- `moclaw.ui.workspace_sidebar`
- `moclaw.reference.cloud_and_local_tools`
- `moclaw.playbooks.ask_for_screenshot_or_reference_id`
