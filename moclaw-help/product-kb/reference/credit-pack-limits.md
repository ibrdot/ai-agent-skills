---
id: moclaw.reference.credit_pack_limits
title: Credit Pack Limits
type: reference
product_area: billing
audience: support
status: verified
last_reviewed_at: 2026-07-23
applies_to:
  plans: [pro]
  environments: [test, prod]
  platforms: [web]
---

# Credit Pack Limits

## Direct Answer

Credit Packs are one-time credit top-ups. They add usage credits, but they do
not unlock, reactivate, extend, or replace Pro/Trial entitlement.

The current pricing dialog shows Credit Packs to paid Pro users as a top-up
path. The current UI slider supports up to **$200**, equal to **20,000 credits**
at **100 credits per $1**.

## Current Limits

| Rule | Current Source-Backed Value |
|---|---|
| Conversion | $1 = 100 credits |
| UI default | $10 / 1,000 credits |
| UI slider step | $10 increments |
| UI displayed marks | None, $100, $200 |
| UI maximum | $200 / 20,000 credits |
| Maximum single purchase | 20,000 credits; larger purchases are rejected |
| Checkout type | Stripe one-time payment for credit-pack-only checkout |
| Fulfillment wallet | `addon` wallet |
| Fulfillment transaction | `addon_purchase` |
| Current expiry implementation | 365 days / 1 year for Stripe Credit Pack addon wallets |

## Who Sees Credit Pack Checkout

- The most reliable customer-facing rule is: paid Pro users can use the
  **Buy Credits** / Credit Pack top-up path.
- Chat usage-gate logic sends active paid Pro users to the Credit Pack dialog
  when they run out of credits.
- Chat usage-gate logic sends active Trial users to the Pro upgrade dialog, not
  the Credit Pack dialog.
- **Settings > Usage** and the New Chat usage badge can show different primary
  actions depending on subscription state: **Upgrade**, **Buy Credits**, or
  **Keep subscription**.

If a user cannot see **Buy Credits**, ask them to check **Settings > Account**
and **Settings > Usage** before assuming a billing failure.

## Fulfillment And Visibility

- Checkout redirects through Stripe and returns to `/chat`.
- Fulfillment can happen through the Stripe webhook or the checkout verification
  route after redirect.
- **Settings > Usage** shows purchased credits as the Credit Pack / purchased
  credits bucket.
- **Settings > Billing** shows Credit Pack payment-history rows when the local
  order or provider invoice data is available.
- **Settings > Usage** credit history labels Credit Pack grants as
  `addon_purchase` / Credit pack purchase and can include the pack ID.

## Relationship To Other Billing Rules

- Credit Pack credits are consumed after bonus credits and subscription/trial
  credits.
- Credit Pack credits can remain visible even when entitlement is inactive.
- A visible Credit Pack balance can still be locked if the account has no active
  product entitlement.
- Credit Pack refund, proration, charge dispute, and invoice correction questions
  require billing review.

## Known Conflict

The current implementation creates Stripe Credit Pack addon wallets with a
365-day expiry. A stale backend docstring still says Credit Pack purchases
"never expire." Until billing/product confirms the public policy, say the
current implementation shows a 1-year expiry and tell users to check
**Settings > Usage** for account-specific dates. Credit history grant rows can
show an expiry date when the backend returns one.

Do not infer "never expires" from generic UI copy such as "No expiration date"
unless it appears on the user's actual Credit Pack wallet/row and billing has
confirmed the account-specific state.

## Do Not Say

- Do not say Credit Packs unlock MoClaw without Pro/Trial entitlement.
- Do not say Credit Packs extend the Pro billing period or Trial period.
- Do not say Credit Pack credits are consumed before monthly credits.
- Do not say Credit Packs never expire.
- Do not say no visible expiry date proves a Credit Pack has no expiry.
- Do not promise refund, proration, charge-dispute, or invoice-correction
  outcomes.
- Do not say every account can see or buy Credit Packs regardless of plan state.

## Related Cards

- `moclaw.reference.pricing_and_credits`
- `moclaw.reference.credit_expiry_and_consumption_order`
- `moclaw.reference.billing_plan_lifecycle`
- `moclaw.how_to.buy_credits_or_upgrade`
- `moclaw.troubleshooting.credits_locked`
- `moclaw.troubleshooting.checkout_payment_not_updated`
- `moclaw.playbooks.billing_refund_escalation`
