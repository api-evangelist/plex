---
name: Connect to a Plex Media Server and browse its libraries
description: Authenticate against a Plex Media Server, confirm its identity, enumerate library sections, and page through the items in a section without exhausting the server.
api: openapi/plex-media-server-openapi.json
operations:
  - getIdentity
  - getSlash
  - libraryGetSections
  - librarySectionGetSection
  - librarySectionGetAll
  - libraryMetadataGetSlash
---

# Connect to a Plex Media Server and browse its libraries

Plex Media Server is **self-hosted**. There is no shared production host — you are
always talking to one specific server, reached either on the LAN
(`http://<server-ip>:32400`) or through Plex's wildcard TLS domain
(`https://<ip-with-dashes>.<machineIdentifier>.plex.direct:32400`).

## Before you start

- A server base URL.
- A Plex token — a legacy long-lived token or a 7-day Plex JWT. See
  `authentication/plex-authentication.yml`.
- Send `X-Plex-Client-Identifier` on **every** request. It is effectively required.
- Send `Accept: application/json`. The server returns **XML by default**; JSON is
  only returned when explicitly requested.

## Steps

1. **Confirm you are talking to the right server — `getIdentity`.**
   `GET /identity` returns the server's `machineIdentifier` and version. This
   endpoint does not require a token on most local networks, so use it as your
   reachability check before you spend a credential.

2. **Read server capabilities — `getSlash`.**
   `GET /` returns the root `MediaContainer` with the friendly name, platform,
   version and the feature flags the server has enabled. Branch on these rather than
   assuming an endpoint exists — DVR, Live TV and transcoding operations 401 or 404
   on servers where the feature is off.

3. **Enumerate the libraries — `libraryGetSections`.**
   `GET /library/sections/all` returns one `Directory` per library section, each
   with a numeric `key` (the `sectionId`), a `type` (`movie`, `show`, `artist`,
   `photo`) and a `title`.

4. **Inspect one section — `librarySectionGetSection`.**
   `GET /library/sections/{sectionId}` returns the section's own directory listing
   (`all`, `unwatched`, `recentlyAdded`, genre and year facets).

5. **Page through the items — `librarySectionGetAll`.**
   `GET /library/sections/{sectionId}/all` is the workhorse. **Always paginate.**
   Send both:
   - `X-Plex-Container-Start: 0`
   - `X-Plex-Container-Size: 50`

   Then read `X-Plex-Container-Total-Size` from the response, and `size`,
   `totalSize` and `offset` from the `MediaContainer` body.

   **Check whether the response was actually paginated.** Plex documents that a
   response may not be paginated at all, or may return a different number of items
   than you asked for. Never assume the page you requested is the page you got.

   Send `X-Plex-Container-Size: 0` when you only want the total count.

   If you do not need the true total, prefer the `limit` query parameter — the
   server does not have to compute the collection size, so the request is cheaper.
   `limit` and the container headers compose:
   `?limit=1000` with `X-Plex-Container-Size: 20` pages 20 at a time within the
   first 1000 items.

6. **Fetch one item — `libraryMetadataGetSlash`.**
   `GET /library/metadata/{ids}` takes the `ratingKey` from the listing. Use
   `includeOptionalFields` to add normally-omitted fields, or `includeFields` to
   restrict the response to only the fields you name.

   > **Version trap.** Before API 1.0.0, `includeFields` meant "additionally
   > include". It now means "include only these". Declare the version you expect
   > with the `X-Plex-Pms-Api-Version` header — when you send no header the server
   > assumes `0.0` and the old semantics.

## Rules

- **Errors carry no body.** Plex returns no `problem+json` and no machine-readable
  error code. Error responses declare `text/html` or no content at all. Branch on
  the HTTP status: `400` malformed, `403` not permitted for this token, `404` no
  such section or ratingKey, `500` server-side failure. See
  `errors/plex-problem-types.yml`.
- **Retries are not safe by contract.** Plex documents no idempotency key. Only
  retry `GET` operations; never blind-retry a write.
- **There is no rate limit to respect and no quota to exhaust** — but you are
  hitting someone's home hardware. Page, do not enumerate everything at once.
- Never put the token in a query string in production. Plex's own docs warn it
  leaks into logs and browser history; use the `X-Plex-Token` header.
