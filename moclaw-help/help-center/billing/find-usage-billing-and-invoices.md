---
id: help.billing.find_usage_billing_invoices
title: Find usage, billing, and invoices
audience: user
status: verified
source_cards:
  - moclaw.ui.billing_and_usage_surfaces
  - moclaw.reference.billing_invoices
  - moclaw.ui.settings
last_reviewed_at: 2026-08-06
---

# Find usage, billing, and invoices

MoClaw splits usage, payment history, plan state, and API keys across several
**Settings** sections.

On desktop, Settings uses tabs on the left. On mobile, the same sections are
stacked in one sheet, so scroll to the section name instead of looking for a
left-side tab.

## Usage And Credits

1. Open **Settings**.
2. Go to **Usage**.
3. Review total credits, credit buckets, usage action, **Show on home**, and
   credit history.

The **Usage** section can show an action such as **Upgrade**, **Buy Credits**,
or **Keep subscription**, depending on your account state. It can also show
retry or stale-data notices if usage refresh fails.

If the credits badge is visible in the New Chat header, you can open it and
jump to **Usage**. You can hide or show it from **Settings > Usage** with
**Show on home**. Session and feature pages do not show this badge.

## Plan And Subscription

1. Open **Settings**.
2. Go to **Account**.
3. Review your current plan, status, validity period, and available subscription
   action.

Cancellation, reactivation, trial, and upgrade actions may appear here
depending on your account state.

## Payment History And Invoices

1. Open **Settings**.
2. Go to **Billing**.
3. Use **Payment History**.
4. Filter by **All**, **Subscription**, or **Credit Pack**.
5. Open the PDF or hosted invoice/receipt link if one is shown.

Some payments may not have every link. The UI only shows **Download PDF** or
**View Invoice** when the billing provider returns those URLs. An empty tab is
not proof that no charge exists; it may be filtered, still loading, unavailable
from the billing provider, or affected by a load error.

## Which Section Should I Use?

| Need | Go to |
|---|---|
| Current credits, credit buckets, usage action, credit history | **Settings > Usage** |
| Hide or show the New Chat usage badge | **Settings > Usage > Show on home** |
| Current plan, subscription status, validity period, cancel/reactivate action | **Settings > Account** |
| Payment history, invoice PDF, hosted invoice/receipt link | **Settings > Billing** |

## Important Notes

- This article only explains where to find billing and usage information.
- Use the pricing and credits article for product-access, trial, Credit Pack,
  or credit-expiry rules.
- Refunds, prorations, charge disputes, and invoice corrections require billing
  review; do not treat the Settings UI as a refund decision.

## Related Articles

- `billing/pricing-credits-trials.md`
- `billing/credit-expiry-and-usage-order.md`
- `billing/invoices-and-payment-history.md`
- `billing/checkout-payment-not-updated.md`
- `billing/cancel-reactivate-refunds.md`
