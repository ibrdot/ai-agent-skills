---
id: help.chat.model_tiers
title: Model Tiers
audience: user
status: verified
source_cards:
  - moclaw.reference.model_tiers
  - moclaw.troubleshooting.model_tier_unavailable_or_switch_failed
  - moclaw.troubleshooting.model_provider_timeout
  - moclaw.concepts.credits_entitlement
last_reviewed_at: 2026-08-06
---

# Model Tiers

MoClaw shows models as user-facing tiers such as **Fast**, **Standard**, and
**Ultra**.

Exact provider and model names can change. For normal support answers, use the
tier names and the current UI instead of promising a long static model list.

## What Each Tier Means

| Tier | Meaning |
|---|---|
| Fast | Fast baseline responses for everyday tasks. |
| Standard | Balanced quality and speed for active Pro users. |
| Ultra | Higher capability for complex work for active Pro users. |

## Why A Tier May Be Locked

- Your Pro subscription or entitlement is not active.
- Your subscription row looks active but its entitlement period has ended.
- The stored tier is no longer authorized for the current account state.
- The current environment or account configuration does not expose that tier.

If a tier switch returns to **Fast** or **Standard**, MoClaw may have corrected a
stored or requested tier that is not authorized for the current account state.

## If A Model Times Out

Retry the message. If the prompt is very large, split it into smaller steps. If
timeouts repeat, send support the account email, model tier, approximate time,
and a short description of the prompt.

## Related Articles

- `billing/connect-openai-codex.md`
- `chat/model-tier-locked-or-switch-failed.md`
- `billing/pricing-credits-trials.md`
- `troubleshooting/common-errors.md`
