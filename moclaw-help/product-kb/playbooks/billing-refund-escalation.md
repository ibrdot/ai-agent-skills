---
id: moclaw.playbooks.billing_refund_escalation
title: Billing And Refund Escalation
type: playbook
product_area: billing
audience: support
status: verified
last_reviewed_at: 2026-06-09
applies_to:
  plans: [free, trial, pro]
  environments: [test, prod]
  platforms: [web]
---

# Billing And Refund Escalation

## When To Use

Use this playbook when the user asks about refunds, unexpected charges,
subscription cancellation outcome, invoice mismatch, missing purchased credits,
or whether a billing action can be reversed.

## Response Pattern

1. Acknowledge the billing concern plainly.
2. Separate product mechanics from billing policy.
3. State only confirmed mechanics from the billing cards.
4. Ask for the minimum escalation details.
5. Hand off to the billing owner when policy, Stripe state, or refund outcome is
   required.

## Confirmed Mechanics

- Paid Pro cancellation is scheduled for the end of the current billing period.
- Trialing Pro cancellation is immediate and revokes remaining trial credits.
- Credit Pack purchases add credits but do not extend Pro or Trial entitlement.
- Credits and subscription entitlement are separate.
- Buying credits alone does not reactivate an ended subscription.
- **Cancel anytime** is cancellation availability copy, not a refund/proration
  policy.
- Reactivation can fail after the old Stripe subscription has already ended;
  the user may need to subscribe again through checkout.
- Refund outcome is not defined by the current KB and needs billing-owner
  confirmation.
- Reviewed current UI sources do not show a self-serve refund/proration or
  Stripe Billing Portal path for users.

## Ask For

- Account email.
- Charge amount and charge date.
- Invoice, receipt, or checkout-session reference if visible.
- Current plan state shown in **Settings > Account**.
- Whether the user canceled, reactivated, upgraded, or bought credits.
- Approximate time and timezone if an action failed.
- Exact visible error copy if **Cancel**, **Keep subscription**, checkout
  verify, billing status, or usage refresh failed.

## Do Not Ask For

- Full card number.
- Payment CVV.
- Password.
- API keys or OAuth tokens.

## Forbidden Claims

- Do not promise a refund, proration, chargeback outcome, or invoice correction.
- Do not say cancellation and refund are the same operation.
- Do not say paid Pro cancellation immediately removes access.
- Do not say trialing Pro cancellation waits until the end of the trial.
- Do not say a credit pack unlocks or extends Pro access.
- Do not say **Cancel anytime** means automatic refund or proration.
- Do not invent self-serve billing controls not visible in the current UI.
- Do not treat backend-only billing portal traces as a visible customer support
  path.

## Example

> I can help separate what the product did from what needs billing review. In
> current product behavior, paid Pro cancellation is scheduled for the end of the
> billing period, while trialing Pro cancellation is immediate. Refund outcomes
> need a billing review, so please send the account email, charge amount/date,
> and any invoice or checkout reference you see.

## Related Cards

- `moclaw.how_to.cancel_or_reactivate_pro`
- `moclaw.how_to.buy_credits_or_upgrade`
- `moclaw.reference.pricing_and_credits`
- `moclaw.reference.trials`
- `moclaw.troubleshooting.checkout_payment_not_updated`
