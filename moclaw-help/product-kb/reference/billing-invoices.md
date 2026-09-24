---
id: moclaw.reference.billing_invoices
title: Billing Invoices And Payment History
type: reference
product_area: billing
audience: support
status: verified
last_reviewed_at: 2026-06-09
applies_to:
  plans: [trial, pro]
  environments: [test, prod]
  platforms: [web]
---

# Billing Invoices And Payment History

## Direct Answer

MoClaw has a **Settings > Billing** payment-history section. It lists paid
subscription and Credit Pack orders, plus paid Stripe renewal invoices that may
not have a matching local order row. When Stripe provides links, the row can
show a PDF download and a hosted invoice/receipt link.

## UI Behavior

| UI Item | Current Behavior |
|---|---|
| Section label | **Payment History** |
| Tabs | All, Subscription, Credit Pack |
| Row fields | date, order type, payment status, amount |
| Paid status | shown as **Paid** when status is `paid` |
| Links | PDF download when `invoice_pdf` exists; hosted invoice/receipt when `hosted_invoice_url` or fallback receipt exists |
| Error state | shows a load failure and retry action |
| Empty state | shows no invoices for the selected tab |

## How Payment History Is Assembled

- Payment history first shows paid orders recorded for the current user.
- It also includes Stripe invoices for the user's Stripe customer when Stripe
  is configured.
- Stripe draft invoices are ignored.
- Stripe manual invoices for Credit Pack purchases are skipped as renewal items
  to avoid duplicate rows, because the local Credit Pack order is already shown.
- Subscription renewals can be shown from Stripe even when there is no matching
  local order row.
- For older one-time payments without Stripe invoice creation, payment history
  may fall back to the charge receipt link.

## Support Boundaries

- Do not promise that every payment row has a PDF. Some rows may only have a
  hosted invoice/receipt link, and some may have no link if Stripe did not
  provide one.
- Do not treat an empty payment-history tab as proof that no charge exists.
  It may be filtered by tab, unavailable from Stripe, or affected by loading
  state.
- Do not promise refund, proration, invoice correction, or charge-dispute
  outcomes from this card. Route those to the billing escalation playbook.

## Related Cards

- `moclaw.ui.billing_and_usage_surfaces`
- `moclaw.reference.refund_policy`
- `moclaw.playbooks.billing_refund_escalation`
- `moclaw.reference.pricing_and_credits`
- `moclaw.reference.credit_pack_limits`
- `moclaw.troubleshooting.checkout_payment_not_updated`
