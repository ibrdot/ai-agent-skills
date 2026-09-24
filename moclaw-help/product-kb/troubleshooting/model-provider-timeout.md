---
id: moclaw.troubleshooting.model_provider_timeout
title: Model Provider Timeout
type: troubleshooting
product_area: chat
audience: user
status: verified
last_reviewed_at: 2026-06-08
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Model Provider Timeout

## Symptom

The user sees **The model provider timed out. Please retry.** A failed message
may be classified as `upstream_timeout`.

## Likely Causes

- The upstream model provider did not respond in time.
- The proxy returned a 504 timeout.
- The request was long, complex, or depended on a slow external provider.
- The provider or route was temporarily degraded.

## Recovery Steps

1. Ask the user to retry the same message.
2. If the prompt is very large, suggest splitting it into smaller steps.
3. If the request depends on files or web pages, retry after confirming those
   inputs are still available.
4. If the user is on a selectable model tier, try another available tier only
   when retrying the same tier keeps timing out.
5. If the timeout repeats, collect account email, approximate time, model tier,
   and a short description of the prompt.

## Escalate When

- The same prompt times out repeatedly across retries.
- Multiple model tiers or accounts time out.
- The user reports a time-sensitive paid workflow blocked by repeated upstream
  timeouts.

## Do Not Say

- Do not say the user's workspace is broken unless there is a sandbox error.
- Do not promise a timeout means the provider completed or did not complete the
  task.
- Do not promise credit/refund behavior without a billing policy card.

## Related Cards

- `moclaw.reference.model_tiers`
- `moclaw.troubleshooting.model_tier_unavailable_or_switch_failed`
- `moclaw.troubleshooting.workspace_unavailable`
- `moclaw.troubleshooting.credits_locked`
