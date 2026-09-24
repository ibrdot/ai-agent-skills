---
id: help.automation.manage_schedules
title: Manage Scheduled Tasks
audience: user
status: verified
source_cards:
  - moclaw.reference.scheduled_tasks
  - moclaw.how_to.manage_schedules
  - moclaw.troubleshooting.schedule_did_not_run
  - moclaw.ui.workspace_sidebar
last_reviewed_at: 2026-07-09
---

# Manage Scheduled Tasks

MoClaw shows scheduled tasks in **left sidebar > Schedules** when schedules are
available from your active chat Sessions.

The Schedules page is mainly for viewing and managing existing schedules. If
you want to create a schedule, the safest path is to ask MoClaw in chat to
schedule the task, then confirm that it appears in **left sidebar > Schedules**.

## Create A Schedule

Ask MoClaw in chat to schedule the task. Include what to do, when to do it, and
where you expect the result.

Examples:

- "Tomorrow at 5 PM, remind me to send the invoice."
- "Every weekday at 9 AM, summarize my calendar and unread email."
- "Every 2 hours during work hours, check this website for updates."

After MoClaw creates it, open **left sidebar > Schedules** and confirm the task is
listed.

Schedules created from chat can deliver their result back to that conversation.
If you need the result somewhere specific, say that in the request.

## View Schedules

1. Open `/chat`.
2. Open the left sidebar.
3. Click **Schedules**.
4. Review schedule names, status dots, frequency, next run, and last run.
5. Use **Refresh** if the list looks stale.
6. Use **Cancel** when cancellation is available.

Schedules may show **Once**, **Recurring interval**, **Recurring schedule**, or
readable timing when detailed schedule expressions are available. In the
current runtime-backed view, many rows use the broader labels plus next-run
metadata.

## Cancel A Schedule

Open the schedule row and choose **Cancel** when that option is available.
After cancellation succeeds, the schedule is removed from the list.

The current Schedules page does not promise pause, resume, edit, duplicate, or restore
controls. If you still need the scheduled task, ask MoClaw in chat to create a
new one.

## If A Schedule Did Not Run

Check the schedule status first:

- **Active**: confirm the next run time and wait if it has not arrived.
- **Failed**: capture the visible error or last-run details.
- **Delivery warning**: the run may have completed, but MoClaw could not deliver
  the result back to the target chat or channel.
- **Paused** or **Expired**: create or ask for a new schedule.
- **Canceled**: it will not run again.

If the schedule is active with a past next-run time but no result appeared,
contact support with the schedule name, visible status, last-run details,
account email, and approximate time.

The Schedules list is not a full historical archive. If an older task was tied
to a Session that is no longer active/runtime-bound, it may not appear in the
current list.

## Do Not Assume

Do not assume there is a dedicated **New schedule** button in the sidebar. Use
the current UI and chat flow. Do not guess the timezone if it is not shown or
not included in the user's request.

## Related Articles

- `workspace/cloud-and-local-tools.md`
- `troubleshooting/common-errors.md`
