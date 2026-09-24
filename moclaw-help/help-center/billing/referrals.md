---
id: help.billing.referrals
title: Referral Rewards
audience: user
status: verified
source_cards:
  - moclaw.reference.referrals
  - moclaw.troubleshooting.referral_invite_link_not_working
  - moclaw.reference.feature_flags
  - moclaw.reference.pricing_and_credits
last_reviewed_at: 2026-06-09
---

# Referral Rewards

Referral rewards are feature-gated. If you do not see a referral or invite
entry in the current product UI, referrals may not be enabled for your account
or environment.

## How Referrals Work

When enabled:

1. The inviter copies a referral link.
2. The invitee opens the link and signs up or logs in.
3. MoClaw checks whether the invitee is eligible.
4. The referral goes through review.
5. After approval, promo credits are granted.

## Reward Rules

Current source defaults describe 500 promo credits for the invitee and 500 promo
credits for the inviter after approval. The UI reads the active referral policy,
so use the values currently shown in the product for account-specific answers.
Newly granted referral promo wallets expire 3 days after grant in the current
implementation.

The inviter reward has a default cap of 5 rewarded invitees. After the cap, the
invitee can still receive the invitee-side reward after approval, but the
inviter-side reward is skipped.

## Important Caveats

- Rewards are not instant.
- A referral must pass eligibility and review.
- Referral credits are promo credits.
- Referral rewards do not extend Pro or Trial entitlement.
- Production availability depends on rollout. Referrals may not be enabled
  for every account or environment yet.

## If The Link Does Not Work

If the invite says **This invite is invalid**, ask the inviter to copy a fresh
link from MoClaw. If the page says **We could not save this invite in your
browser**, retry in a normal browser window with browser storage enabled.

If you sign in but the invite is not claimed, reopen the original invite link
and try once more. Some invites are ineligible or still waiting for review.

## What To Send Support

- Account email.
- Whether you are the inviter or invitee.
- The visible referral state or error.
- Approximate time the invite link was opened.

Do not paste private tokens, passwords, or unrelated personal data.

## Related Articles

- `billing/pricing-credits-trials.md`
- `billing/referral-invite-link-not-working.md`
- `product/feature-availability.md`
