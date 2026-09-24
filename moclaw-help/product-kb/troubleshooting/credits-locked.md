---
id: moclaw.troubleshooting.credits_locked
title: Credits Visible But Locked
type: troubleshooting
product_area: billing
audience: user
status: verified
owner: product
last_reviewed_at: 2026-08-06
source_paths:
  - maxgent/client/webapp/src/routes/_authenticated/chat.tsx
  - maxgent/client/webapp/src/lib/chat-usage-gate.ts
  - maxgent/client/webapp/src/stores/credits-store.ts
  - maxgent/client/webapp/src/i18n/locales/en.json
  - maxgent/server/app-server/app/routers/credits.py
  - product-kb/reference/credit-pack-limits.md
  - product-kb/troubleshooting/checkout-payment-not-updated.md
applies_to:
  plans: [free, trial, pro]
  environments: [test, prod]
  platforms: [web]
---

# Credits Visible But Locked

## Symptom

The user can see credits or a balance, but sending a message or using a feature
is blocked.

Visible chat banners can include:

- **No active subscription.** / **Resubscribe**
- **Credits exhausted.** / **Get credits** or upgrade copy
- **Billing status is temporarily unavailable. We are retrying.**

## Likely Causes

- Pro or legacy/account-specific trial entitlement expired, or the current
  account has no active non-free subscription state.
- The balance is already 0.
- The user bought only a Credit Pack without active computer entitlement.
- Billing/subscription state is temporarily unavailable, so the frontend shows a
  billing-status retry notice instead of making a final zero-balance claim.
- The current model or feature requires Pro.
- The previous user message failed with `payment_required` before
  balance/subscription state finished refreshing; the frontend can use that
  failure as a temporary usage-gate signal and refetch billing state.

## Current Chat Gate Rules

- If both balance/subscription have loaded, chat sending is blocked when
  `total_balance <= 0` or there is no active non-free subscription.
- When there is no active subscription and the balance is also 0, the
  subscription gate takes priority. Say the user needs to restore/upgrade
  access, not only "buy credits."
- **Billing status is temporarily unavailable** shows a retry notice and keeps
  refetching; do not describe it as cleared credits, failed payment, or canceled
  subscription.

## Recovery Steps

1. Ask the user to open **Settings -> Usage** to check credits.
2. Ask the user to open **Settings -> Account** to check current plan,
   subscription state, and validity period.
3. Ask the user to open **Settings -> Billing** to check whether recent payment
   history is visible.
4. If **Billing status is temporarily unavailable** appears, wait for automatic
   retry and refresh **Settings > Usage** before drawing conclusions.
5. If entitlement expired, the user needs to restore or upgrade Pro access.

## Escalate When

- Billing shows active, but sending is still blocked.
- The user just paid successfully, but entitlement/credits did not refresh.
- The user sees a reference ID, payment error, or checkout verify failure.
- **Billing status is temporarily unavailable** persists and does not recover.

## Do Not Say

- Do not say credits disappeared.
- Do not say buying credits always restores access.
- Do not say a temporary billing-status outage means payment failed or the
  subscription was canceled.
- Do not promise manual compensation unless the billing owner confirms it.

## Related Cards

- `moclaw.reference.pricing_and_credits`
- `moclaw.reference.credit_pack_limits`
- `moclaw.reference.billing_plan_lifecycle`
- `moclaw.reference.credit_expiry_and_consumption_order`
- `moclaw.troubleshooting.checkout_payment_not_updated`
