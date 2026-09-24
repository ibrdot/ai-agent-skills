---
id: moclaw.troubleshooting.checkout_payment_not_updated
title: Checkout Payment Or Credits Not Updated
type: troubleshooting
product_area: billing
audience: support
status: verified
last_reviewed_at: 2026-06-09
applies_to:
  plans: [free, trial, pro]
  environments: [test, prod]
  platforms: [web]
---

# Checkout Payment Or Credits Not Updated

## Symptom

The user completed Stripe checkout or saw a MoClaw payment-success state, but
their credits, Pro access, trial state, payment history, or invoice row does not
look updated in the UI.

## Direct Answer

Ask the user to return to `/chat`, refresh **Settings > Usage**, then check
**Settings > Account** for plan state and **Settings > Billing** for payment
history. If the state still looks wrong, collect safe billing review details and
escalate.

Do not treat the success dialog alone as proof that the wallet or subscription
has finished refreshing. Do not treat a not-yet-credited verification result as
proof of failure; fulfillment is idempotent and may already have been processed
by the webhook or a previous verify call.

## What Happens After Checkout

1. Stripe redirects back to `/chat?checkout=success&session_id=...`.
2. The web app shows the checkout-success UI, closes the pricing dialog, removes
   the query string, and runs a checkout verification request when a
   `session_id` is present.
3. The verify endpoint retrieves the Stripe Checkout Session, confirms it
   belongs to the current user, and accepts only `paid` or `no_payment_required`
   payment states.
4. If the session is still pending, verify returns `status: pending` and does
   not grant credits yet.
5. For paid or no-payment-required sessions, fulfillment runs through the shared
   webhook/verify code path and is idempotent.
6. Fulfillment can activate Pro, start the Stripe trial, grant Credit Pack
   credits, update the local order to paid, and store provider identifiers.
7. The frontend then runs a full credits refetch: balance, usage, subscription,
   transactions, subscription sync, and provider keys.

## Likely Causes

- The UI has not completed its post-checkout refetch yet.
- The browser returned without a `session_id`, so the app can refetch but cannot
  call checkout verify.
- Stripe still reports the Checkout Session as pending.
- The session ID is invalid or belongs to a different signed-in user.
- The signed-in account changed between checkout and return; checkout verify
  checks the session metadata `user_id` against the current user.
- The webhook or a previous verify call already fulfilled the session, so a
  later verification can report not-credited even though the grant is already
  settled.
- Payment history is filtered, Stripe invoice data is unavailable, or an older
  one-time payment has only a receipt URL fallback.
- Credits are visible but product entitlement is inactive, so usage remains
  blocked.

## Recovery Steps

1. Ask the user to return to `/chat`.
2. Ask the user to open **Settings > Usage** and refresh/retry if the panel shows
   stale or failed data.
3. Ask the user to open **Settings > Account** and check the plan/subscription
   state.
4. Ask the user to open **Settings > Billing** and check **Payment History**;
   remind them to check filters such as **All**, **Subscription**, or
   **Credit Pack**.
5. If the user bought a Credit Pack, check whether the purchased credits bucket
   and credit-history entry appeared in **Settings > Usage**.
6. If the user upgraded or started a trial, check whether Account shows the new
   plan state and current period.
7. If state is still wrong after refresh, escalate with safe billing details.

## Escalation Fields

Ask only for:

- account email;
- approximate checkout time and timezone;
- purchase type: Pro subscription, Stripe Pro trial, or Credit Pack;
- charge amount and charge date;
- checkout session, invoice, receipt, or payment-history reference if visible;
- screenshot of **Settings > Usage**, **Settings > Account**, or
  **Settings > Billing** if helpful;
- exact visible error copy if checkout verify, billing status, or usage refresh
  failed.

## Do Not Ask For

- full card number;
- CVV;
- password;
- API keys;
- OAuth tokens;
- signed URLs or unrelated personal data.

## Do Not Say

- Do not promise that a payment-success dialog means credits are already visible.
- Do not say a not-yet-credited verification result always means the checkout failed.
- Do not say an empty Payment History tab proves there was no charge.
- Do not promise refunds, duplicate-charge corrections, proration, or manual
  credit compensation.
- Do not say buying credits unlocks MoClaw when entitlement is inactive.

## Related Cards

- `moclaw.reference.credit_pack_limits`
- `moclaw.reference.billing_plan_lifecycle`
- `moclaw.reference.billing_invoices`
- `moclaw.reference.credit_expiry_and_consumption_order`
- `moclaw.troubleshooting.credits_locked`
- `moclaw.playbooks.billing_refund_escalation`
