---
id: moclaw.reference.refund_policy
title: Refund Policy
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

# Refund Policy

## Direct Answer

The current KB does not contain an owner-reviewed public refund policy.
Support answers must separate known product mechanics from refund outcome, then
escalate refund, proration, invoice correction, charge dispute, or credit
compensation requests to the billing owner.

Reviewed app sources do not show a self-serve refund, proration, chargeback, or
invoice-correction control for users.

## Confirmed Product Mechanics

- Paid Pro cancellation is scheduled for the end of the current billing period.
- Trialing Pro cancellation is immediate and revokes remaining trial credits.
- Credits and subscription entitlement are separate.
- Buying a Credit Pack does not reactivate or extend Pro/Trial entitlement.
- Cancellation and refund are different operations.
- Product copy can say **Cancel anytime**, but that is not a refund or proration
  promise in the current KB.
- Checkout success, invoice visibility, and cancellation state do not determine
  refund outcome by themselves.
- A backend Stripe Billing Portal session endpoint exists, but reviewed current
  UI sources do not show it as a visible user support path.

## Escalation Fields

Ask only for safe billing review fields:

- account email;
- charge amount and charge date;
- invoice, receipt, or checkout-session reference if visible;
- current plan state shown in **Settings > Account**;
- whether the user canceled, reactivated, upgraded, or bought credits;
- exact visible error copy if cancellation/reactivation/checkout failed;
- approximate time and timezone if an action failed.

## Do Not Ask For

- full card number;
- CVV;
- password;
- API keys;
- OAuth tokens.

## Do Not Say

- Do not promise a refund.
- Do not promise proration or invoice correction.
- Do not say cancellation automatically refunds a charge.
- Do not say **Cancel anytime** means automatic refund or proration.
- Do not say support can manually add credits without billing-owner approval.
- Do not say a chargeback outcome is controlled by MoClaw support.
- Do not promise that invoices or billing records can be deleted or removed.
- Do not invent a self-serve refund/proration portal or Stripe Billing Portal
  button from backend-only traces.

## Related Cards

- `moclaw.playbooks.billing_refund_escalation`
- `moclaw.reference.billing_plan_lifecycle`
- `moclaw.how_to.cancel_or_reactivate_pro`
- `moclaw.reference.pricing_and_credits`
