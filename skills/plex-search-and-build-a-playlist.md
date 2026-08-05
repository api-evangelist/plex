---
name: Search a Plex server and build a playlist from the results
description: Run a cross-library search, resolve the results to ratingKeys, create a playlist, add and reorder items, and clean up.
api: openapi/plex-media-server-openapi.json
operations:
  - hubsGetSearch
  - libraryMetadataGetSlash
  - playlistPostSlash
  - playlistGetSlash
  - playlistGetPlaylist
  - playlistPutItems
  - playlistGetItems
  - playlistPutItemsMove
  - playlistPutPlaylist
  - playlistDeleteItems
  - playlistDeletePlaylist
---

# Search a Plex server and build a playlist from the results

## Steps

1. **Search — `hubsGetSearch`.**
   `GET /hubs/search?query=<term>` returns results grouped into hubs across every
   library the token can see. Each hub carries a `type` and its own item array.
   Do not assume a flat result list; walk the hubs.

   `hubsSearchGetVoice` (`GET /hubs/search/voice`) is the voice-oriented variant
   when the query came from speech.

2. **Resolve each candidate — `libraryMetadataGetSlash`.**
   Search results are summaries. `GET /library/metadata/{ids}` gives the full
   metadata object for a `ratingKey`, including `guid`, duration and media parts.
   `{ids}` accepts a comma-separated list — resolve a batch in one call rather than
   one call per hit.

3. **Create the playlist — `playlistPostSlash`.**
   `POST /playlists` creates the playlist. Playlists are typed (`audio`, `video`,
   `photo`) and Plex will not mix types, so decide the type from the items you
   resolved in step 2 before you create it.

4. **Add items — `playlistPutItems`.**
   `PUT /playlists/{playlistId}/items` appends. **This write is not idempotent** —
   Plex documents no idempotency key, so calling it twice with the same items
   appends them twice. Read back with `playlistGetItems`
   (`GET /playlists/{playlistId}/items`) to confirm rather than retrying blind.

5. **Reorder — `playlistPutItemsMove`.**
   `PUT /playlists/{playlistId}/items/{playlistItemId}/move`. Note the identifier:
   the `playlistItemId` is the item's identity *inside this playlist*, which is not
   the `ratingKey`. Take it from the `playlistGetItems` response.

6. **Rename or retitle — `playlistPutPlaylist`.**
   `PUT /playlists/{playlistId}`.

7. **Clean up.**
   `playlistDeleteItems` (`DELETE /playlists/{playlistId}/items`) clears the
   playlist; `playlistDeletePlaylist` (`DELETE /playlists/{playlistId}`) removes it.
   Both are destructive and unconfirmable — there is no soft delete and no undo.
   Confirm with a human before calling either.

8. **List what exists — `playlistGetSlash`.**
   `GET /playlists` returns every playlist for the authenticated user; use it to
   avoid creating a duplicate.

## Rules

- Paginate `playlistGetItems` with `X-Plex-Container-Start` /
  `X-Plex-Container-Size` on large playlists, and verify the response really was
  paginated.
- `409 Conflict` on a playlist or collection rename means the target name is
  already taken.
- Send `Accept: application/json`; XML is the default.
- See `conventions/plex-conventions.yml` for the full pagination and header
  contract, and `errors/plex-problem-types.yml` for the status-code semantics.
