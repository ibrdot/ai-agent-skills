---
id: moclaw.troubleshooting.sandbox_capacity_full
title: Sandbox Capacity Full
type: troubleshooting
product_area: workspace
audience: user
status: verified
last_reviewed_at: 2026-06-08
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Sandbox Capacity Full

## Symptom

The user sees **Workspace capacity is temporarily full** or the backend code
`SANDBOX_CAPACITY_EXHAUSTED`.

## Likely Causes

- The sandbox provider has temporarily exhausted capacity.
- The app cannot allocate a new AI Cloud Computer right now.

## Recovery Steps

1. Tell the user capacity usually clears quickly.
2. Ask the user to retry now.
3. If it keeps failing, wait about a minute and retry again.
4. If it persists, collect account email, time, environment, and any visible
   trace/reference id for escalation.

## Escalate When

- Capacity remains full after several retries over a few minutes.
- Many users report the same error.
- The error appears on an account that should already have an active workspace.

## Do Not Say

- Do not tell the user to restart the workspace for capacity exhaustion.
- Do not blame the user's plan or credits unless there is separate billing
  evidence.
- Do not expose backend provider names unless support needs them internally.

## Related Cards

- `moclaw.troubleshooting.workspace_unavailable`
- `moclaw.concepts.ai_cloud_computer`
