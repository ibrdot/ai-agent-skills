---
id: moclaw.reference.referrals
title: Referrals
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

# Referrals

## Direct Answer

The referral MVP is link-based, feature-flagged, and manually reviewed before
reward credits are granted. Production rollout is not implied unless the
referral feature is enabled in the current environment/account.

## User-Visible Flow

1. Inviter opens the referral CTA when it is enabled.
2. Inviter copies a shareable referral link.
3. Invitee opens `/r/<token>` or `/referral/accept?token=<token>`.
4. The public accept page previews the invite without exposing inviter email,
   internal user IDs, token digest, or relationship IDs.
5. Invitee signs up or logs in.
6. Backend binds the invite relationship when the invitee is eligible.
7. Operator reviews the relationship.
8. Approval grants promo credits.

## Reward Rules From Current Sources

| Rule | Current Source Value |
|---|---|
| Default reward | 500 promo credits to invitee and inviter after approval; active policy can override the default and is returned to UI. |
| Inviter cap | Default 5 rewarded invitees; active policy can override the default and is returned to UI. |
| 6th+ approved invitee | Invitee can still receive reward; inviter reward skipped. |
| Expiry | Newly granted referral promo wallets expire 3 days after grant. |
| Wallet type | `promo`. |
| Bind window | Default 24 hours from invitee account creation; active policy can override. |
| Review | Review window defaults to 24 hours; approval/grant is idempotent. |

## Eligibility Caveats

Referral eligibility is not just "clicked a link." Current source checks include
new-user state, no duplicate invitee relationship, bind window, no prior
completed API request before bind, no prior referral reward, non-system account
type, and inviter/invitee not being the same active user.

## Accept Page States

- **Referrals are not available yet** means the referral feature is disabled.
- **This invite is invalid** means the token is missing, invalid, inactive, or
  no longer valid.
- **Could not check this invite** means the public preview request failed.
- **Your invite is ready** means the invite preview is valid and the user should
  sign up or log in from that page.
- **We could not save this invite in your browser** means browser session
  storage was unavailable; the app stops before login so the pending token is
  not silently lost.
- **We saved the invite but could not claim it yet** means binding failed or
  should be retried after login.
- **This invite could not be claimed** means binding completed but the invitee
  was ineligible for the shown reason.

## Feature Flag Rule

Referrals are disabled unless rollout enables both app-server and webapp flags.
Current deployment values show test/preview enabled and production default-off
until explicitly enabled.

## Do Not Say

- Do not promise referrals are live for every user.
- Do not promise instant credits after signup.
- Do not say the inviter always receives credits; cap and review can skip it.
- Do not say referral rewards extend Pro entitlement.
- Do not ask users to share raw tokens except through the intended invite link.
- Do not say browser storage errors are harmless; they can prevent carrying the
  invite through login.

## Related Cards

- `moclaw.reference.feature_flags`
- `moclaw.reference.pricing_and_credits`
- `moclaw.troubleshooting.referral_invite_link_not_working`
- `moclaw.troubleshooting.credits_locked`
