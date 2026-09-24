---
id: moclaw.reference.pricing_and_credits
title: Pricing, Credits, And Entitlement
type: reference
product_area: billing
audience: user
status: verified
owner: product
last_reviewed_at: 2026-08-06
source_paths:
  - maxgent/client/webapp/src/routes/_authenticated/chat.tsx
  - maxgent/client/webapp/src/lib/chat-usage-gate.ts
  - maxgent/client/webapp/src/stores/credits-store.ts
  - maxgent/server/app-server/app/routers/subscription_checkout.py
  - maxgent/server/app-server/app/routers/stripe_webhook.py
  - maxgent/client/webapp/src/components/subscription/pricing-table.tsx
  - product-kb/reference/credit-pack-limits.md
  - maxgent/client/webapp/src/i18n/locales/en.json
applies_to:
  plans: [free, trial, pro]
  environments: [test, prod]
  platforms: [web]
---

# Pricing, Credits, And Entitlement

## Direct Answer

Explain MoClaw billing in separate layers:

- Pro is the primary paid plan for product access / cloud-computer entitlement;
  current checkout code prices it at $20/month.
- Credits are usage balance.
- A Credit Pack only adds credits; it does not extend Pro or Trial entitlement.
- Without active entitlement, credits are locked and cannot be used.
- Current public support posture is no 30-day no-card MoClaw Trial and no
  one-time 1,000-credit Trial grant. New users without active entitlement should
  expect the paywall / upgrade entry point.

## Rules

| Item | Current Rule |
|---|---|
| Pro price | $20/month in checkout code |
| Pro monthly credits | 1,000 credits in current UI/checkout fulfillment |
| Credit packs | One-time purchase, current UI max $200 / 20,000 credits, dynamic `credits_XXXX` up to 20,000 in checkout code; current wallet code gives Stripe Credit Pack addon wallets a 1-year expiry |
| Referral credits | Existing docs mention 500 each after approval, 3-day expiry |
| Refund | Needs dedicated policy card; current seed says refund only affects the specific Pro purchase |

## Edge Cases

- A user can have a visible balance but still be blocked because entitlement expired.
- Buying credits alone does not unlock the product.
- In `/chat`, if the account has no active non-free subscription, the
  subscription/access gate takes priority over a "credits exhausted" answer,
  even when the balance is also 0.
- **Billing status is temporarily unavailable** means the billing/subscription
  state could not be confirmed and the app is retrying; it is not by itself a
  final payment failure, cancellation, or zero-credit proof.
- Cancelling subscription and refunding are different operations.
- Legacy Trial credits and Pro checkout credits can both use `trial_grant` in
  some code paths, so support answers should avoid ledger-internal wording and
  should not infer a public 30-day Trial offer from ledger names.
- A stale Stripe webhook docstring says addon credits "never expire," but the
  implemented wallet currently sets a 365-day expiry. For public answers, route
  users to **Settings > Usage** for account-specific expiry dates.

## Do Not Say

- Do not say credits are the same as subscription.
- Do not say Credit Pack extends Pro.
- Do not say a temporary billing-status outage means the user has no credits or
  the charge failed.
- Do not promise exact refund behavior without checking the active billing policy.
- Do not say Credit Packs never expire or that missing visible expiry copy proves
  no expiry.
- Do not say MoClaw currently offers a public 30-day no-card Trial or a
  one-time 1,000-credit Trial grant.

## Related Cards

- `moclaw.ui.billing_and_usage_surfaces`
- `moclaw.reference.credit_pack_limits`
- `moclaw.reference.trials`
- `moclaw.concepts.credits_entitlement`
- `moclaw.reference.credit_expiry_and_consumption_order`
- `moclaw.troubleshooting.credits_locked`
