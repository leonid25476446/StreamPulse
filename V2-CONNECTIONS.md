# StreamPulse v2 — live connections

## YouTube
1. Create a YouTube Data API v3 key in Google Cloud.
2. Enable YouTube Data API v3 for the project.
3. Start the live stream first.
4. In `admin-v2.html`, enter the API key and the live video ID.
5. Click `Подключить YouTube`.

The connector resolves the active `liveChatId` and polls YouTube at the interval requested by the API. Messages are forwarded to `chat-v2.html` through BroadcastChannel/localStorage.

## Twitch
The connector uses Twitch IRC over WebSocket. Enter an OAuth access token with `chat:read`, the Twitch username associated with the token, and the target channel. The token is kept in `sessionStorage` only.

For production OAuth, a Twitch application/backend should be used to obtain short-lived user tokens; do not publish a client secret in this static repository.

## OBS
OBS Studio 28+ includes WebSocket 5.x. Enable the WebSocket server and enter its address and password in the admin panel. StreamPulse performs the OBS v5 Hello/Identify handshake and can call `SetCurrentProgramScene`.

When the browser page is served from HTTPS, browsers can block a plain `ws://` connection as mixed content. In that case run the admin page locally or use a secure WebSocket endpoint.

## Chat Browser Source
Add `chat-v2.html` as a separate OBS Browser Source. It is independent from the Countdown Browser Source, so switching the main scene does not remove the chat source if it is present in the target scene.

## TTS
The chat source uses the browser Speech Synthesis API and processes messages in a queue. The admin panel sends TTS events with a configurable limit/cooldown. Persistent viewer entitlement, watch-time accounting, automatic rewards and payment/donation verification require a backend and platform OAuth/webhook integration; they are not faked by the static client.

## Security
Never commit Twitch access tokens, OAuth client secrets, YouTube keys with unrestricted usage, or OBS passwords to GitHub. The v2 admin stores Twitch/YouTube/OBS credentials in the current browser session or fields only; a production hosted version should move secrets and OAuth to a backend.