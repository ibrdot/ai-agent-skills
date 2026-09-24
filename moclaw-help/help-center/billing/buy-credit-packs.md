---
id: help.billing.buy_credit_packs
title: Buy Credit Packs
audience: user
status: verified
source_cards:
  - moclaw.reference.credit_pack_limits
  - moclaw.troubleshooting.checkout_payment_not_updated
  - moclaw.how_to.buy_credits_or_upgrade
  - moclaw.reference.credit_expiry_and_consumption_order
  - moclaw.reference.pricing_and_credits
  - moclaw.reference.billing_plan_lifecycle
  - moclaw.troubleshooting.credits_locked
last_reviewed_at: 2026-06-09
---

# Buy Credit Packs

Credit Packs add usage credits. They do not extend your Pro subscription or
Trial, and they do not unlock MoClaw if your account does not have active
product access.

## Buy Credits

1. Open the credits badge or **Settings**.
2. Go to **Usage**.
3. Click **Buy Credits** if the action is available.
4. Choose an amount in the Credit Pack checkout.
5. Complete Stripe checkout.
6. Return to `/chat` and wait for the checkout success state.

Current UI sources show Credit Packs at 100 credits per $1, with a maximum
slider value of $200 / 20,000 credits.

## If You Do Not See Buy Credits

The primary action changes by account state:

- Paid Pro users can see **Buy Credits**.
- Trial users may be sent to **Upgrade** instead of Credit Pack checkout.
- A canceling paid Pro subscription may show **Keep subscription** /
  **Resubscribe**.
- Free or inactive accounts may need to upgrade or subscribe again before
  credits can be used.

Check **Settings > Account** for plan state and **Settings > Usage** for credit
balance and credit buckets.

## Expiry And Usage Order

MoClaw uses credits in this order:

1. bonus credits;
2. subscription or trial credits;
3. purchased Credit Pack credits.

Purchased Credit Pack credits currently use a 1-year expiry in the billing
implementation. Check **Settings > Usage** for your account's dates, especially
the credit bucket and credit-history rows when they show expiry information.

Credit Packs are used after bonus credits and subscription/trial credits. If
your monthly subscription credits are still available, MoClaw may use those
before using the credits you bought.

## If Credits Do Not Appear

Return to `/chat`, refresh **Settings > Usage**, and check **Settings > Billing**
for the payment-history row.

If credits still do not appear, contact support with your account email,
checkout/session or invoice reference if visible, charge amount, and charge
date. Do not send full card numbers, CVV, passwords, API keys, or OAuth tokens.

## Related Articles

- `billing/checkout-payment-not-updated.md`
- `billing/credit-expiry-and-usage-order.md`
- `billing/find-usage-billing-and-invoices.md`
- `billing/cancel-reactivate-refunds.md`
