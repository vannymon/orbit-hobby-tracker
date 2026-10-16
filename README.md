# Orbit

Orbit is a low-pressure hobby tracker for curious people. Pick a focus, log what you do, and let other hobbies rest without guilt.

**Try the prototype:** https://vannymon.github.io/orbit-hobby-tracker/

This is a clickable web prototype of the iPhone app, used to test the design before the real build. It runs entirely in the browser. Your taps, logs and photos are saved in that browser only, and nothing is uploaded.

## Testing it

- Open the link on a phone for the real feel. On a laptop it shows in a phone frame, with a short list of things to try beside it.
- It starts with example hobbies. On a laptop, "Reset example data" in the side notes brings them back. To start empty, use Settings → Delete all data.
- Photos are kept in browser storage, which fills up after roughly 20–40 photos. The real app stores them as files.
- Not built yet: trials, revisit dates, onboarding and real notifications.

## Files

- `index.html`: the whole prototype in one file, with no build step.
- `docs/requirements.md`: the v1.0 product requirements the prototype follows.

## Plan

The real app will be built with Expo (React Native) and data stored on the device, aiming for the App Store in Q1 2027.
