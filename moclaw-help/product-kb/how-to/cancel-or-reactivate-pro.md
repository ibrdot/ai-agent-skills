---
id: moclaw.how_to.cancel_or_reactivate_pro
title: Cancel Or Reactivate Pro
type: how_to
product_area: billing
audience: user
status: verified
last_reviewed_at: 2026-06-09
applies_to:
  plans: [trial, pro]
  environments: [test, prod]
  platforms: [web]
---

# Cancel Or Reactivate Pro

## Direct Answer

Open **Settings > Account** and use the current plan action. Active paid Pro can
show **Cancel**. A paid Pro subscription that is already set to cancel can show
**Resubscribe** / **Keep subscription**.

Paid Pro cancellation is scheduled for the end of the current billing period.
Trialing Pro cancellation is immediate and revokes remaining trial credits.

## Before You Start

- Subscription entitlement and credit balance are separate.
- **Settings > Account** is the cancellation surface. Usage surfaces may show
  **Keep subscription**, **Buy Credits**, or **Upgrade**, depending on state.
- A paid Pro subscription set to cancel can keep access until the current period
  ends.
- Once a subscription has fully ended, reactivation can fail; the user should
  subscribe again through checkout.
- Refunds are not defined by this card.
- Current reviewed UI sources do not show a visible Stripe Billing Portal entry
  for cancellation or refund handling.

## Steps

1. Open `/chat`.
2. Open **Settings**.
3. Go to **Account**.
4. Find the current plan row.
5. If the action says **Cancel**, click it.
6. Confirm the cancellation dialog.
7. If the plan is already canceling and the action says **Resubscribe** or
   **Keep subscription**, click it to reactivate.
8. Refresh or reopen Settings after the action completes.

## If You Cannot See It

- If subscription state is still loading, wait or refresh.
- If the user is on Free, route them to the visible paywall or upgrade action
  instead of cancel.
- If **Keep subscription** or **Resubscribe** fails, ask the user to refresh
  **Settings > Account**. The old subscription may already have ended.
- If the subscription already fully ended, ask the user to subscribe again
  through checkout.
- If the action fails, collect account email, approximate time, plan state, and
  visible error copy for escalation.

## Do Not Say

- Do not promise refunds, prorations, or invoice outcomes.
- Do not say paid Pro cancellation immediately removes all access.
- Do not say Pro trial cancellation behaves like paid Pro cancellation; trial
  cancellation is immediate in current server code.
- Do not say buying a credit pack reactivates a canceled subscription.
- Do not say **Cancel anytime** promises an automatic refund or proration.
- Do not invent a visible Stripe Billing Portal button unless the current UI is
  re-verified.

## Related Cards

- `moclaw.reference.pricing_and_credits`
- `moclaw.reference.billing_plan_lifecycle`
- `moclaw.reference.trials`
- `moclaw.how_to.buy_credits_or_upgrade`
- `moclaw.playbooks.billing_refund_escalation`
