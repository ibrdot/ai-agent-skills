---
id: moclaw.troubleshooting.model_tier_unavailable_or_switch_failed
title: Model Tier Unavailable Or Switch Failed
type: troubleshooting
product_area: chat
audience: support
status: verified
last_reviewed_at: 2026-08-06
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Model Tier Unavailable Or Switch Failed

## Symptom

The user cannot see or choose **Standard** or **Ultra**; sees **Pro** badges in
the tier menu; sees **Could not switch model tier. Try again.**; or selects a
tier but the selector returns to another tier.

## Direct Answer

Model availability is controlled by the user's current plan and entitlement
period. Answer by user-facing tier names and current UI state. Do not promise a
long static provider/model list.

## Current Selection Rules

| Account State | Expected Tier Menu |
|---|---|
| Free / no active Pro entitlement | Fast is available; Standard and Ultra are upgrade-locked. |
| Active Pro entitlement | Standard and Ultra are available; Fast is hidden from the Pro menu. |
| Expired or inactive Pro entitlement | Treated as non-Pro for runtime authorization. |

The client menu may briefly reflect stale state after plan changes. The
app-server authorization result is the source of truth for the runtime tier.

## Server Fallback Rules

- App-server is the authority for the actual runtime tier.
- If an unauthorized tier is requested, app-server coerces it to the authorized
  fallback.
- Non-Pro users fall back to **Fast**.
- An active-looking Pro row with an expired billing period is not treated as
  entitled and can fall back to **Fast**.

## Recovery Steps

1. Ask the user to open the tier selector in the chat input and check which rows
   are shown or locked.
2. If **Standard** or **Ultra** is locked, ask them to check **Settings >
   Account** for active Pro entitlement.
3. If the selector returns to **Fast** or **Standard**, explain that the server
   may have corrected an unauthorized stored tier for the current account state.
4. If the tier should be unlocked after checkout but the plan still looks
   inactive, use the checkout-payment troubleshooting card.
5. If the UI shows **Could not switch model tier. Try again.**, ask them to
   retry and collect safe diagnostic details if it repeats.

## Escalate When

- Active Pro is visible in **Settings > Account**, but Standard or Ultra remains
  locked.
- A tier switch repeatedly shows **Could not switch model tier. Try again.**
- The selector and runtime response disagree after refresh.

Collect account email, current plan state, selected tier, approximate time, and
the exact visible error copy.

## Do Not Say

- Do not give an exhaustive model list from stale docs.
- Do not say Pro users should choose Fast; current client hides Fast for Pro.
- Do not say a fallback to Fast or Standard always means the switch failed; it
  can be server authorization correction.
- Do not say the client selector alone proves the runtime tier.
- Do not ask users to send provider API keys.
- Do not ask users to send browser storage or full raw logs for tier switching.

## Related Cards

- `moclaw.reference.model_tiers`
- `moclaw.reference.openai_codex_device_auth`
- `moclaw.concepts.credits_entitlement`
- `moclaw.troubleshooting.credits_locked`
- `moclaw.troubleshooting.model_provider_timeout`
- `moclaw.troubleshooting.checkout_payment_not_updated`
