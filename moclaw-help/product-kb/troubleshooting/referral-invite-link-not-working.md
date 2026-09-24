---
id: moclaw.troubleshooting.referral_invite_link_not_working
title: Referral Invite Link Not Working
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

# Referral Invite Link Not Working

## Symptom

The user opens a referral link and sees **Referrals are not available yet**,
**This invite is invalid**, **Could not check this invite**, **We could not save
this invite in your browser**, **We saved the invite but could not claim it
yet**, or **This invite could not be claimed**.

## Direct Answer

Referral links are feature-gated, token-based, and reviewed before rewards are
granted. Opening a link is not enough by itself: the invitee must open a valid
link, sign up or log in, pass eligibility checks, and wait for review.

## User-Visible Accept Flow

- Inviter sees the referral CTA only when the referrals feature flag is enabled.
- The sidebar card says **Refer & earn credits** and opens an invite modal.
- The modal shows **Your referral link**, copy-link action, stats for approved,
  earned credits, pending review, and rejected referrals.
- Invite links use the short `/r/<token>` route, which renders the same accept
  page as `/referral/accept?token=<token>`.
- The accept page validates the invite before the invitee signs up or logs
  in.
- A valid invite page says **Your invite is ready** and offers **Sign up** and
  **Log in**.
- If the invitee is already authenticated, the page attempts to bind the invite
  immediately.
- If the invitee is not authenticated, MoClaw remembers the pending invite in the browser and sends the invitee to
  login.

## Visible States

| Visible State | Support Meaning |
|---|---|
| Referrals are not available yet | Referrals feature is disabled in the current environment/account. |
| This invite is invalid | Token is missing, malformed, expired, inactive, or no longer valid. |
| Could not check this invite | Public preview request failed; ask the user to refresh or retry later. |
| Your invite is ready | Token preview is valid; user should sign up or log in from the accept page. |
| Login is not configured in this environment | Current environment cannot complete login. |
| We could not save this invite in your browser | Browser session storage was unavailable, so MoClaw cannot safely carry the pending token through login. |
| We saved the invite but could not claim it yet | Binding failed or should be retried after login. |
| This invite could not be claimed | Binding completed but the invitee is ineligible for the shown reason. |

## Likely Causes

- Referrals are disabled by feature flag.
- The invite link token is missing, too long, contains whitespace, expired, or
  inactive.
- The inviter account is inactive.
- Browser storage is blocked by private mode, strict browser settings, or an
  extension.
- Login is not configured in the current environment.
- The invitee is not eligible: duplicate invitee, self-invite, prior referral
  reward, account too old for the bind window, prior completed API request
  before bind, or system/internal account.
- The relationship was created but is still pending review.
- The inviter-side reward cap was reached; the invitee-side reward may still be
  possible after approval.
- The active referral policy can change reward amount, inviter cap, bind window,
  review window, or approval conditions; use the current UI/policy values for
  support answers.

## Recovery Steps

1. Ask whether the user is the inviter or invitee.
2. If the CTA or invite page says referrals are unavailable, explain that the
   feature may not be enabled for that account/environment.
3. If the invite is invalid, ask the inviter to copy a fresh referral link from
   the current product UI.
4. If the page cannot save the invite, ask the user to keep the invite page
   open, enable browser storage, or retry in a normal non-private browser
   window.
5. If login is unavailable, direct the user to the normal production app URL or
   escalate the environment.
6. If binding failed after login, ask the invitee to reopen the original invite
   link and try again once.
7. If the relationship is pending review, explain that rewards are not instant.
8. If the invite could not be claimed, explain that eligibility checks can make
   a clicked link ineligible.

## Escalate When

- The invite is valid and the invitee completed login, but no bind state or
  review state appears.
- The user repeatedly sees **Could not check this invite**.
- The user sees a bind failure with a reason that does not match expected
  eligibility rules.
- The UI says rewards were approved but credits are still missing after refresh.

Collect inviter/invitee role, account email if known, visible invite page state,
approximate time and timezone, environment/URL path, and whether browser storage
was blocked. Do not ask for raw referral tokens outside the intended link, and
do not ask for passwords, OAuth tokens, cookies, or full browser storage.

## Do Not Say

- Do not promise referral rewards are instant after signup.
- Do not say every referral link is valid forever.
- Do not say the inviter always receives credits; cap and review can skip the
  inviter-side reward.
- Do not say referral rewards extend Pro or Trial entitlement.
- Do not ask users to paste raw referral tokens, passwords, OAuth tokens,
  cookies, or browser storage.

## Related Cards

- `moclaw.reference.referrals`
- `moclaw.reference.feature_flags`
- `moclaw.reference.authentication_and_login`
- `moclaw.troubleshooting.credits_locked`
- `moclaw.playbooks.ask_for_screenshot_or_reference_id`
