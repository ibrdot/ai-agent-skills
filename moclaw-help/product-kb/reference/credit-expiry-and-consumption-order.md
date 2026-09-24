---
id: moclaw.reference.credit_expiry_and_consumption_order
title: Credit Expiry And Consumption Order
type: reference
product_area: billing
audience: support
status: verified
last_reviewed_at: 2026-06-08
applies_to:
  plans: [free, trial, pro]
  environments: [test, prod]
  platforms: [web]
---

# Credit Expiry And Consumption Order

## Direct Answer

MoClaw credits live in wallets. When a completed request is billed, active
wallets are consumed in this order:

1. bonus/promo credits;
2. subscription or trial credits;
3. purchased Credit Pack credits.

Within the same wallet type, MoClaw consumes the earliest-expiring wallet first
and uses no-expiry wallets last.

This means a paid user's current subscription credits are normally consumed
before purchased Credit Pack credits. Do not tell users that buying a Credit
Pack makes those purchased credits spend first.

## Wallet Types

| Wallet Type | User-Facing Meaning | Expiry Source |
|---|---|---|
| `promo` | Bonus credits, including referral rewards and admin promo grants | Referral rewards expire after 3 days in current referral code; admin promo topups can set a custom expiry |
| `monthly` | Trial or Pro monthly allowance | Expires at the subscription/trial period end |
| `addon` | Purchased Credit Pack or admin addon topup | Current Stripe Credit Pack and admin addon topups create 1-year expiry wallets |

## Balance And Usage Display

- **Settings > Usage** shows total available credits and separate buckets for
  bonus credits, monthly quota, and purchased credits.
- The total-credit tooltip says credits are used in this order: bonus credits,
  subscription credits, then credit packs.
- Usage bucket labels are **Bonus credits**, **Subscription credits**, and
  **Credit packs**.
- Positive credit-history rows can show an expiry date from the wallet. Credit
  Pack grants are labeled `addon_purchase` / **Credit pack purchase** and can
  include the pack ID.
- The full Usage bucket row currently shows expiry tooltip copy for bonus and
  monthly buckets; purchased-credit expiry is most directly visible through the
  credit-history row when the backend returns an `expires_at`.
- The balance endpoint includes zero-balance unexpired wallets, so a fully
  consumed monthly allowance can still render as consumed for the current
  period instead of disappearing from the UI.
- The usage endpoint summarizes completed billed requests in the current
  subscription period by provider.
- The transaction endpoint returns the newest credit-history entries first and
  supports credit/debit filtering.

## Answer Pattern For Credit Pack Expiry

Use this wording shape:

> Current implementation creates purchased Credit Pack wallets with a 1-year
> expiry. Check **Settings > Usage** for the expiry date shown on your account,
> especially the credit bucket and credit-history rows.

If the user says they do not see an expiry date, ask for the visible credit
bucket, credit-history row, purchase amount, and approximate purchase date. Do
not infer "never expires" from a missing visible date.

## Credit History Terms

Credit-history rows describe events such as monthly subscription credits
granted, trial credits granted or revoked, usage deductions, period credits
expiring, Credit Pack purchases, support-applied top-ups, and referral bonus
credits.

## Edge Cases

- Credits and entitlement are separate. A user can have credits but still be
  blocked if their Trial/Pro access is inactive.
- The settler allows the last active wallet to go negative up to a configured
  debt ceiling when finalizing a completed request. Do not expose this as a
  user-facing promise; treat it as backend settlement tolerance.
- Monthly credits do not roll over. Renewal handling retires prior active
  monthly wallet balance before creating the fresh monthly wallet.
- Credit Pack credits do not extend Pro or Trial access.

## Do Not Say

- Do not say Credit Pack credits are always consumed first.
- Do not say purchased credits extend the subscription period.
- Do not say every account has referral credits or promo credits.
- Do not promise "no expiry" for Credit Packs; current Stripe and admin addon
  topups use a 1-year expiry.
- Do not say a missing visible expiry date means the credit never expires.
- Do not expose backend wallet IDs, debt ceilings, or settlement internals to
  users.

## Related Cards

- `moclaw.ui.billing_and_usage_surfaces`
- `moclaw.reference.pricing_and_credits`
- `moclaw.reference.credit_pack_limits`
- `moclaw.reference.trials`
- `moclaw.reference.referrals`
- `moclaw.troubleshooting.credits_locked`
