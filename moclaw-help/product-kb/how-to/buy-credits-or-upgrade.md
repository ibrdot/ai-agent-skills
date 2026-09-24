---
id: moclaw.how_to.buy_credits_or_upgrade
title: Buy Credits Or Upgrade
type: how_to
product_area: billing
audience: user
status: verified
last_reviewed_at: 2026-06-09
applies_to:
  plans: [free, trial, pro]
  environments: [test, prod]
  platforms: [web]
---

# Buy Credits Or Upgrade

## Direct Answer

Use the credits/usage widget or **Settings > Usage**. The action changes by
account state: non-Pro users see an upgrade path, Pro users see **Buy Credits**,
and users whose subscription is set to cancel may see **Keep subscription** /
reactivation.

## Before You Start

- Credits and subscription entitlement are separate.
- Buying credits alone does not unlock usage if the account has no active
  entitlement.
- Active Trial users may be routed to upgrade instead of Credit Pack checkout.
- Checkout redirects through Stripe and returns to `/chat` after success.

## Steps

1. Open the credits badge or Settings.
2. Go to **Usage**.
3. Review total credits and credit buckets.
4. Click the primary action:
   - **Upgrade** / **Upgrade to Pro** if not subscribed.
   - **Buy Credits** if already on paid Pro.
   - **Keep subscription** if the subscription is canceling.
5. Complete the Stripe checkout or reactivation flow.
6. Return to `/chat` and wait for the checkout success/verification state.

## If You Cannot See It

- If the Usage panel cannot load, ask the user to retry or refresh.
- If the user has credits but cannot use the product, check entitlement status
  before suggesting a credit pack.
- If checkout succeeds but credits are missing, collect the account email and
  checkout session/invoice evidence for escalation.

## Do Not Say

- Do not say credit packs extend the subscription period.
- Do not promise exact refund or invoice behavior without a billing policy card.

## Related Cards

- `moclaw.ui.billing_and_usage_surfaces`
- `moclaw.reference.pricing_and_credits`
- `moclaw.reference.credit_pack_limits`
- `moclaw.reference.trials`
- `moclaw.troubleshooting.credits_locked`
