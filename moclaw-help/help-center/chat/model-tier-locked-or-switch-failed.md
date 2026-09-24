---
id: help.chat.model_tier_locked_or_switch_failed
title: Model Tier Locked Or Switch Failed
audience: user
status: verified
source_cards:
  - moclaw.troubleshooting.model_tier_unavailable_or_switch_failed
  - moclaw.reference.model_tiers
  - moclaw.concepts.credits_entitlement
  - moclaw.troubleshooting.credits_locked
  - moclaw.troubleshooting.checkout_payment_not_updated
last_reviewed_at: 2026-08-06
---

# Model Tier Locked Or Switch Failed

MoClaw shows model choices as tiers: **Fast**, **Standard**, and **Ultra**.
Exact provider/model names can change, so use the current tier menu as the
source for your account.

## Why A Tier Is Locked Or Missing

- Free or inactive accounts can use **Fast**. **Standard** and **Ultra**
  require active Pro entitlement.
- Active Pro users can use **Standard** and **Ultra**.
- A subscription that looks active but has passed its entitlement period may be
  treated as inactive for model-tier authorization.

## If Switching Fails

1. Retry the tier switch once.
2. Check **Settings > Account** for active Pro state.
3. If you just completed checkout, refresh **Settings > Account** and
   **Settings > Usage**.
4. Refresh the page if the selector and account state look out of sync.

MoClaw may automatically return to an authorized tier if your stored selection is
not available for your current account state.

The tier selector is not the final authority for the runtime model. MoClaw's
server authorizes the request, updates the active session, and returns the
effective tier.

## Contact Support

If it still fails, send:

- account email;
- current plan state shown in **Settings > Account**;
- tier you tried to select;
- approximate time and timezone;
- exact visible error copy.

Do not send provider API keys, passwords, OAuth tokens, full card numbers, or
CVV.

## Related Articles

- `chat/model-tiers.md`
- `billing/pricing-credits-trials.md`
- `billing/checkout-payment-not-updated.md`
- `troubleshooting/common-errors.md`
