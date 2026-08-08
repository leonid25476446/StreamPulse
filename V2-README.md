# StreamPulse v2.0.0 — development build

v2 expands StreamPulse from a countdown overlay into a stream interaction toolkit.

## Included in this build

- Independent OBS chat Browser Source (`chat-v2.html`).
- Local admin prototype (`admin-v2.html`).
- YouTube/Twitch-style chat events for local testing.
- TTS settings model: 10-message allowance and 5-minute cooldown.
- Streamer Override model for temporary TTS/VIP grants.
- Event testing for subscriptions, followers and donations.
- Existing v1 countdown remains unchanged.

## Important

This is the v2 development build, not the final stable release yet.

The local chat/admin bridge uses `BroadcastChannel` and `localStorage` so it can be tested without a server. Real YouTube/Twitch authentication, live chat ingestion, persistent viewer watch-time, TTS playback, donation providers and OBS WebSocket scene switching require their respective connectors and must not be simulated as if they were already connected.

## Quick test

1. Open `admin-v2.html` in Chrome or Edge.
2. Open `chat-v2.html` in another tab/window.
3. Send a test chat message from the admin page.
4. Verify that it appears in the chat Browser Source.
5. Test TTS settings and event buttons.
6. For OBS, add `chat-v2.html` as a separate Browser Source. Keep `admin-v2.html` out of the scene.

## Planned connectors

- YouTube Live Chat API + OAuth.
- Twitch chat/EventSub + OAuth.
- OBS WebSocket scene switching.
- Persistent viewer accounts, watch time, rewards and moderation storage.
- Production TTS provider/browser speech integration.

These are intentionally listed as pending until implemented and tested end-to-end.
