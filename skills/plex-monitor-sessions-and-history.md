---
name: Monitor Plex playback sessions and playback history
description: Read who is streaming right now, inspect background tasks and activities, read playback history, and terminate a session — the read-mostly observability surface of a Plex server.
api: openapi/plex-media-server-openapi.json
operations:
  - statusGetSlash
  - statusGetBackground
  - statusGetHistoryAll
  - statusGetHistory
  - statusPostTerminate
  - activitiesGetSlash
  - activitiesDeleteActivity
  - livetvSessionsGetSlash
---

# Monitor Plex playback sessions and playback history

## Steps

1. **Who is streaming now — `statusGetSlash`.**
   `GET /status/sessions` returns the active playback sessions with the player,
   the user, the media, and the transcode decision in effect. This is the endpoint
   every Plex dashboard is built on. It is a snapshot — poll it, or subscribe to the
   push streams instead (see below).

2. **What the server is doing to itself — `statusGetBackground` and
   `activitiesGetSlash`.**
   `GET /status/sessions/background` lists background tasks;
   `GET /activities` lists running activities (scans, analysis, thumbnail
   generation) with progress. Check these before starting anything expensive — a
   library scan already in flight is why a refresh appears to hang.

3. **Playback history — `statusGetHistoryAll` and `statusGetHistory`.**
   `GET /status/sessions/history/all` lists historical sessions.
   **Paginate it** with `X-Plex-Container-Start` / `X-Plex-Container-Size`; on a
   long-lived server this collection is very large. `GET
   /status/sessions/history/{historyId}` returns a single entry.

4. **Live TV sessions — `livetvSessionsGetSlash`.**
   `GET /livetv/sessions` covers tuner sessions, which do not appear in
   `/status/sessions`.

## Destructive operations — confirm with a human first

- **`statusPostTerminate`** — `POST /status/sessions/terminate` stops someone
  else's stream mid-playback. It returns `401` when the server does not have the
  feature enabled. This is a user-visible interruption; never call it autonomously.
- **`activitiesDeleteActivity`** — `DELETE /activities/{activityId}` cancels a
  running activity, which may leave a partial scan or analysis.

## Prefer push over polling

Plex ships two server-push channels rather than making you poll `/status/sessions`:

- `websocketGetSlash` — `GET /:/websocket/notifications` (WebSocket)
- `eventsourceGetSlash` — `GET /:/eventsource/notifications` (Server-Sent Events)

Both are declared operations but Plex publishes **no message schema** for either,
so you must discover the payload shape empirically. For account-level events
outside the server, Plex Pass accounts can register webhooks — twelve documented
events, catalogued in `asyncapi/plex-webhooks.yml`.

## Rules

- Everything in step 1–3 is read-only and safe for an agent to call unattended.
- Everything under "Destructive operations" needs human confirmation.
- No idempotency contract exists; do not retry `statusPostTerminate` or
  `activitiesDeleteActivity` on a timeout — read state back instead.
