---
id: moclaw.troubleshooting.voice_recording_not_working
title: Voice Recording Not Working
type: troubleshooting
product_area: chat
audience: user
status: verified
last_reviewed_at: 2026-06-08
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Voice Recording Not Working

## Symptom

The user cannot see the voice button, cannot start recording, sees a microphone
permission dialog, sees "Voice recording isn't supported in this browser", sees
"Recording too short", or sends a voice message and gets a transcription-failed
notice.

## Likely Causes

- Voice messages are disabled in the current environment by feature flag.
- The browser does not support `MediaRecorder` or microphone capture APIs.
- The user denied microphone permission.
- The recording was shorter than 1 second.
- The recording reached the 3-minute cap and was auto-stopped.
- Capture or audio conversion failed.
- The audio uploaded, but transcription failed or returned an empty transcript.

## Recovery Steps

1. If the voice button is missing, explain that voice recording may be hidden by
   environment or rollout state and suggest typing the message instead.
2. If permission was denied, ask the user to allow microphone access in browser
   settings, then refresh and try again.
3. If the browser is unsupported, try a modern desktop browser with microphone
   recording support.
4. If the recording was too short, record for at least 1 second.
5. If the 3-minute cap appears, split the message into shorter recordings or
   send text.
6. If transcription failed, explain that the voice message was still sent but
   MoClaw may not have the spoken text for that turn; ask the user to resend as
   text or record again.
7. If the issue repeats, collect browser name/version, approximate time, visible
   error copy, and whether microphone permission is allowed.

## Escalate When

- A supported browser with microphone permission still cannot start recording.
- Voice recordings upload but transcription fails repeatedly.
- The user sees unsupported-browser copy in a browser known to support
  `MediaRecorder`.
- The voice button is unexpectedly missing in an environment where voice is
  supposed to be enabled.

## Do Not Say

- Do not ask the user to paste secrets, tokens, signed URLs, or private audio
  transcripts into support chat.
- Do not claim transcription failure means the whole message failed.
- Do not promise the microphone works in every browser or mobile environment.
- Do not promise recordings longer than 3 minutes are supported.

## Related Cards

- `moclaw.reference.chat_composer_controls`
- `moclaw.reference.message_display_and_actions`
- `moclaw.how_to.upload_or_reference_file`
- `moclaw.playbooks.ask_for_screenshot_or_reference_id`
