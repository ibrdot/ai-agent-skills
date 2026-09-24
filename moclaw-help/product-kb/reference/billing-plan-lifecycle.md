---
id: moclaw.reference.billing_plan_lifecycle
title: Billing Plan Lifecycle
type: reference
product_area: billing
audience: support
status: verified
last_reviewed_at: 2026-06-09
applies_to:
  plans: [free, trial, pro]
  environments: [test, prod]
  platforms: [web]
---

# Billing Plan Lifecycle

## Direct Answer

MoClaw billing lifecycle answers must separate four layers:

- plan entitlement;
- Stripe subscription state;
- credit wallets;
- visible UI action.

Use **Settings > Account** for the current plan action. Use **Settings > Usage**
for balances, credit buckets, credit history, and usage-driven upgrade/buy/keep
actions. A visible credit balance does not by itself mean the account has active
product entitlement.

## User-Facing States

| State | Access / Action |
|---|---|
| Free or no active subscription | No paid Pro entitlement. The current public posture is paywall / **Upgrade to Pro**, not a public 30-day no-card Trial. |
| Legacy or account-specific trial entitlement | Trial states can still exist in code or account history. Answer from the visible account state, but do not describe a 30-day no-card MoClaw Trial as a current public offer. |
| Pro checkout trialing | Stripe Pro trialing is a Pro subscription trial state. Current server cancellation cancels it immediately and revokes remaining trial credits. |
| Paid Pro active | Active paid Pro can show **Cancel**. Cancellation schedules the Stripe subscription to end at the current period end. |
| Paid Pro canceling / grace period | If the subscription is set to cancel at period end and the period has not ended, access can continue until period end. The UI can show **Resubscribe** or **Keep subscription**. |
| Fully canceled or ended | Reactivation can fail after the subscription has already ended. The user should subscribe again through checkout. |
| Credit Pack only | Credit Pack credits can exist without active entitlement. Buying credits does not reactivate, extend, or replace Pro/Trial access. |

## How The UI Decides Which Action To Show

The web UI derives subscription display from the current subscription, period
end, and whether the provider is set to cancel at period end:

- Paid Pro access requires a non-free, non-trial paid plan with active access.
- Usage subscription access requires a non-free plan with active access.
- The account is in a grace period when the current period has not ended and
  either the provider is canceling at period end or the local status is
  canceled.
- The account counts as canceling when it is already canceling or in the grace
  period.

Account action priority is:

1. reactivate / keep subscription when paid Pro is canceling;
2. cancel when paid Pro is active and not already canceling;
3. upgrade otherwise.

The Usage badge and **Settings > Usage** action are related but not identical:

- canceling paid subscriptions can show **Keep subscription**;
- active paid Pro can show **Buy Credits**;
- trial/free/non-paid states can show **Upgrade** or account-specific
  checkout copy.

Do not describe the Usage action as the canonical cancellation control. Use
**Settings > Account** for canceling, and use Usage for balances, credit
history, upgrade/top-up, and keep-subscription prompts.

## Cancellation And Reactivation Behavior

- Paid Pro cancellation asks the billing provider to cancel at the end of the
  current billing period.
- Stripe Pro trial cancellation is immediate; the account reverts to the free
  plan and remaining trial credits are revoked.
- If the provider subscription is already ended, local state is synced to
  canceled and reactivation should not be promised.
- Reactivation before the period ends clears the scheduled cancellation.
- Reactivation after Stripe reports `canceled` or `incomplete_expired` returns
  a conflict-style response and tells the user to subscribe again.
- Canceling an already-ended upstream subscription is treated as idempotent
  success after local state is synced to canceled.
- The server reports the provider's cancel-at-period-end state so the UI can show the
  correct current action.
- The old self-serve MoClaw Trial service and UI copy are not the current public
  support posture. Do not promise a 30-day no-card Trial or a one-time
  1,000-credit Trial grant.

## Support Routing

- For "how do I cancel or keep Pro?" use
  `moclaw.how_to.cancel_or_reactivate_pro`.
- For refund, proration, duplicate charge, charge dispute, or invoice correction
  questions, use `moclaw.playbooks.billing_refund_escalation` and
  `moclaw.reference.refund_policy`.
- For "I still have credits but cannot use the product," use
  `moclaw.troubleshooting.credits_locked` and the credit entitlement cards.
- For trial duration and eligibility questions, use `moclaw.reference.trials`.

## Do Not Say

- Do not say paid Pro cancellation immediately removes all access.
- Do not say trialing Pro cancellation waits until the trial or billing period
  ends.
- Do not say there is a current public 30-day no-card MoClaw Trial.
- Do not say MoClaw Trial credits refill daily or that a public Trial credit
  grant is currently available.
- Do not say buying a Credit Pack reactivates or extends Pro/Trial entitlement.
- Do not say cancellation automatically refunds a charge.
- Do not say reactivation is always possible after the subscription has ended.
- Do not say **Cancel anytime** means automatic refund or proration.
- Do not say the Usage badge is where users cancel Pro; use **Settings >
  Account** for cancellation.

## Related Cards

- `moclaw.how_to.cancel_or_reactivate_pro`
- `moclaw.reference.pricing_and_credits`
- `moclaw.reference.credit_expiry_and_consumption_order`
- `moclaw.reference.credit_pack_limits`
- `moclaw.reference.trials`
- `moclaw.reference.refund_policy`
- `moclaw.troubleshooting.credits_locked`
