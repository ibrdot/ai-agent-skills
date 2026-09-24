---
id: moclaw.reference.model_tiers
title: Model Tiers
type: reference
product_area: chat
audience: support
status: verified
last_reviewed_at: 2026-08-06
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Model Tiers

## Direct Answer

MoClaw's user-facing model choices are tiers: **Fast**, **Standard**, and
**Ultra**. Support answers should explain tier availability by plan, not by a
long static provider/model list.

## Current User-Facing Tiers

| Tier | User-facing description | Availability rule |
|---|---|---|
| Fast | Fast responses for everyday tasks | Shown as the non-Pro baseline in the selector; sending still requires active entitlement |
| Standard | Balanced quality and speed | Active Pro plans |
| Ultra | Highest capability for complex work | Active Pro plans |

## Current Platform Mapping

The current app-server tier config maps platform tiers this way:

| Tier | Current platform model |
|---|---|
| Fast | `deepseek-v4-flash` |
| Standard | `claude-sonnet-4-6` |
| Ultra | `claude-opus-4-6` |

This table is for support verification and should not be the first thing shown
to users unless they ask which model a tier uses.

## Plan Rules

- Non-Pro users can select Fast in the selector, but selecting it does not
  bypass the usage gate: without active entitlement, sending is still blocked.
  Other tiers are shown as upgrade-locked.
- Active Pro users can select Standard and Ultra.
- Active Pro users do not select Fast in the web UI; the Pro baseline is
  Standard.
- A subscription row with `status: active` but an expired current period is not
  entitled for model-tier authorization.
- If a stored tier is not authorized for the current account state, app-server
  coerces it to the authorized fallback.
- Expired or inactive Pro entitlement should be treated as non-Pro for tier
  selection.

## Runtime Authority

- The client asks the server to update the session's model tier.
- The server authorizes the requested tier before updating the runtime session.
- Non-Pro or expired users are coerced to **Fast**.
- Active Pro users requesting **Fast** are coerced to **Standard**.
- Explicit unauthorized persisted tiers are self-healed on session binding so
  the stored tier, runtime model, and client store can converge.

## Support Implications

- If a user cannot choose Standard or Ultra, check whether their Pro
  subscription is active.
- If a tier switch fails, ask them to retry; collect account state and the
  failed tier for escalation.
- If the UI and runtime tier disagree briefly after switching, app-server is the
  authority and the session should reconcile.
- If a stored or requested tier is unauthorized for the current account state,
  app-server can return an authorized fallback such as Fast or Standard.

## Do Not Say

- Do not promise an exhaustive model list from stale docs.
- Do not say Pro users should choose Fast; current client hides Fast for Pro.
- Do not say the client selector alone proves the runtime tier; app-server is
  authoritative.
- Do not hardcode model names in normal support answers unless the user asks for
  model identity.
- Do not ask for API keys, OAuth tokens, Codex device codes, ChatGPT passwords,
  cookies, or browser storage.

## Related Cards

- `moclaw.concepts.credits_entitlement`
- `moclaw.reference.openai_codex_device_auth`
- `moclaw.troubleshooting.model_tier_unavailable_or_switch_failed`
- `moclaw.reference.pricing_and_credits`
