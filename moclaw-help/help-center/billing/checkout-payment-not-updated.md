---
id: help.billing.checkout_payment_not_updated
title: Checkout Payment Or Credits Not Updated
audience: user
status: verified
source_cards:
  - moclaw.troubleshooting.checkout_payment_not_updated
  - moclaw.reference.credit_pack_limits
  - moclaw.reference.billing_plan_lifecycle
  - moclaw.reference.billing_invoices
  - moclaw.troubleshooting.credits_locked
  - moclaw.playbooks.billing_refund_escalation
last_reviewed_at: 2026-06-09
---

# Checkout Payment Or Credits Not Updated

If you completed checkout but MoClaw still looks unchanged, refresh the billing
and usage state before assuming the payment failed.

## Check Your Account

1. Return to `/chat`.
2. Open **Settings > Usage** and refresh/retry if the panel shows stale or failed
   data.
3. Open **Settings > Account** and check your current plan state.
4. Open **Settings > Billing** and check **Payment History**.
5. If you bought a Credit Pack, check the purchased-credits bucket and credit
   history in **Settings > Usage**.

Payment history may be filtered. Check **All**, **Subscription**, and
**Credit Pack** if those tabs are visible.

## Why It Can Lag

After Stripe redirects back to MoClaw, the app verifies the checkout session and
refreshes credits, usage, subscription state, and payment history. A success
message can appear before every panel has finished refreshing.

If the browser returns without a checkout session id, MoClaw can still refresh
account state but cannot verify that specific session from the page. If the
checkout session belongs to a different signed-in account, the verify step will
not apply it to the current user. Support can review safe checkout references;
do not resend payment-card details.

## If It Still Looks Wrong

Contact support with:

- account email;
- approximate checkout time and timezone;
- what you bought: Pro subscription, Pro trial, or Credit Pack;
- charge amount and charge date;
- checkout session, invoice, receipt, or payment-history reference if visible;
- screenshot of **Settings > Usage**, **Settings > Account**, or
  **Settings > Billing** if helpful.

Do not send full card numbers, CVV, passwords, API keys, or OAuth tokens.

## Related Articles

- `billing/buy-credit-packs.md`
- `billing/find-usage-billing-and-invoices.md`
- `billing/cancel-reactivate-refunds.md`
- `troubleshooting/common-errors.md`
