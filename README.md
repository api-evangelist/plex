# Plex

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Plex, Inc. is a personal-media and streaming company whose Plex Media Server organizes, transcodes and streams a user's own movies, TV, music and photos to Plex client apps on virtually every platform, alongside a free ad-supported live TV and on-demand catalog, Discover, Rentals, the Plexamp music player and the paid Plex Pass tier. In September 2025 Plex published official documentation for the Plex Media Server HTTP API for the first time — an OpenAPI 3.1 contract covering libraries, metadata, playlists, play queues, sessions, DVR/Live TV, transcoding and server administration — together with a new public-key JWT authentication flow on plex.tv, Plex Pass webhooks, and an OAuth-protected remote MCP server for agents.

**Areas:** Company · Media · Streaming · Video · Music · Media Server · Entertainment · Self-Hosted · Personal Media · Home Automation

## Plex on APIs.io

Everything profiled for Plex is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/plex/](https://apis.io/providers/plex/)** — or go straight to one of the APIs or properties below.

### APIs (31)

- [Plex Account and Authentication API](https://apis.io/apis/plex/plex-account-api/) — The plex.tv cloud API that issues and refreshes the credentials every Plex Media Server call depends on: PIN-based device linking, JWK public-key…
- [Plex MCP Server](https://apis.io/apis/plex/plex-mcp-server/) — A first-party remote Model Context Protocol server operated by Plex at https://plex.tv/internal/mcp. It advertises RFC 9728 protected-resource metadata, RFC…
- [Plex Activities API](https://apis.io/apis/plex/plex-activities-api/) — Activities provide a way to monitor and control asynchronous operations on the server. In order to receive real-time updates for activities, a client would…
- [Plex Butler API](https://apis.io/apis/plex/plex-butler-api/) — The butler is responsible for running periodic tasks. Some tasks run daily, others every few days, and some weekly. These includes database maintenance,…
- [Plex Collections API](https://apis.io/apis/plex/plex-collections-api/) — The Collections API from Plex — 1 operation(s) for collections.
- [Plex Content API](https://apis.io/apis/plex/plex-content-api/) — The actual content of the media provider
- [Plex Devices API](https://apis.io/apis/plex/plex-devices-api/) — Media grabbers provide ways for media to be obtained for a given protocol. The simplest ones are `stream` and `download`. More complex grabbers can have…
- [Plex Download Queue API](https://apis.io/apis/plex/plex-download-queue-api/) — The Download Queue API from Plex — 8 operation(s) for download queue.
- [Plex DV Rs API](https://apis.io/apis/plex/plex-dvrs-api/) — The DVR provides means to watch and record live TV. This section of endpoints describes how to setup the DVR itself
- [Plex EPG API](https://apis.io/apis/plex/plex-epg-api/) — The EPG (Electronic Program Guide) is responsible for obtaining metadata for what is airing on each channel and when
- [Plex Events API](https://apis.io/apis/plex/plex-events-api/) — The server can notify clients in real-time of a wide range of events, from library scanning, to preferences being modified, to changes to media, and many…
- [Plex General API](https://apis.io/apis/plex/plex-general-api/) — General endpoints for basic PMS operation not specific to any media provider
- [Plex Hubs API](https://apis.io/apis/plex/plex-hubs-api/) — The hubs within a media provider
- [Plex Library API](https://apis.io/apis/plex/plex-library-api/) — Library endpoints which are outside of the Media Provider API. Typically this is manipulation of the library (adding/removing sections, modifying…
- [Plex Library Collections API](https://apis.io/apis/plex/plex-library-collections-api/) — Endpoints for manipulating collections. In addition to these endpoints, `/library/collections/:collectionId/X` will be rerouted to…
- [Plex Library Playlists API](https://apis.io/apis/plex/plex-library-playlists-api/) — Endpoints for manipulating playlists.
- [Plex Live TV API](https://apis.io/apis/plex/plex-live-tv-api/) — LiveTV contains the playback sessions of a channel from a DVR device
- [Plex Log API](https://apis.io/apis/plex/plex-log-api/) — Logging mechanism to allow clients to log to the server
- [Plex Metadata Agents API](https://apis.io/apis/plex/plex-metadata-agents-api/) — The Metadata Agents API from Plex — 5 operation(s) for metadata agents.
- [Plex Play Queue API](https://apis.io/apis/plex/plex-play-queue-api/) — The playqueue feature within a media provider A play queue represents the current list of media for playback. Although queues are persisted by the server,…
- [Plex Playlist API](https://apis.io/apis/plex/plex-playlist-api/) — The playlist feature within a media provider Playlists are ordered collections of media. They can be dumb (just a list of media) or smart (based on a media…
- [Plex Preferences API](https://apis.io/apis/plex/plex-preferences-api/) — The Preferences API from Plex — 2 operation(s) for preferences.
- [Plex Provider API](https://apis.io/apis/plex/plex-provider-api/) — Media providers are the starting points for the entire Plex Media Server media library API. It defines the paths for the groups of endpoints. The…
- [Plex Rate API](https://apis.io/apis/plex/plex-rate-api/) — The rate feature within a media provider
- [Plex Search API](https://apis.io/apis/plex/plex-search-api/) — The search feature within a media provider
- [Plex Status API](https://apis.io/apis/plex/plex-status-api/) — The status endpoints give you information about current playbacks, play history, and even terminating sessions.
- [Plex Subscriptions API](https://apis.io/apis/plex/plex-subscriptions-api/) — Subscriptions determine which media will be recorded and the criteria for selecting an airing when multiple are available
- [Plex Timeline API](https://apis.io/apis/plex/plex-timeline-api/) — The actions feature within a media provider
- [Plex Transcoder API](https://apis.io/apis/plex/plex-transcoder-api/) — The Transcoder API from Plex — 5 operation(s) for transcoder.
- [Plex Ultra Blur API](https://apis.io/apis/plex/plex-ultrablur-api/) — Service provided to compute UltraBlur colors and images.
- [Plex Updater API](https://apis.io/apis/plex/plex-updater-api/) — This describes the API for searching and applying updates to the Plex Media Server. Updates to the status can be observed via the Event API.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Plex Webhooks](https://apis.io/asyncapis/plex/plex-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [plex](https://apis.io/servers/plex/plex/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Plex Agentic Access](https://apis.io/agentic-access/plex/plex-agentic-access/)

#### Collections (29)

Postman and Open Collection request collections.

- [Plex Media Server Activities API](https://apis.io/collections/plex/open-plex-activities-api/)
- [Plex Media Server Butler API](https://apis.io/collections/plex/open-plex-butler-api/)
- [Plex Media Server Collections API](https://apis.io/collections/plex/open-plex-collections-api/)
- [Plex Media Server Content API](https://apis.io/collections/plex/open-plex-content-api/)
- [Plex Media Server Devices API](https://apis.io/collections/plex/open-plex-devices-api/)
- [Plex Media Server Download Queue API](https://apis.io/collections/plex/open-plex-download-queue-api/)
- [Plex Media Server DV Rs API](https://apis.io/collections/plex/open-plex-dvrs-api/)
- [Plex Media Server EPG API](https://apis.io/collections/plex/open-plex-epg-api/)
- [Plex Media Server Events API](https://apis.io/collections/plex/open-plex-events-api/)
- [Plex Media Server General API](https://apis.io/collections/plex/open-plex-general-api/)
- [Plex Media Server Hubs API](https://apis.io/collections/plex/open-plex-hubs-api/)
- [Plex Media Server Library API](https://apis.io/collections/plex/open-plex-library-api/)
- [Plex Media Server Library Collections API](https://apis.io/collections/plex/open-plex-library-collections-api/)
- [Plex Media Server Library Playlists API](https://apis.io/collections/plex/open-plex-library-playlists-api/)
- [Plex Media Server Live TV API](https://apis.io/collections/plex/open-plex-live-tv-api/)
- [Plex Media Server Log API](https://apis.io/collections/plex/open-plex-log-api/)
- [Plex Media Server Metadata Agents API](https://apis.io/collections/plex/open-plex-metadata-agents-api/)
- [Plex Media Server Play Queue API](https://apis.io/collections/plex/open-plex-play-queue-api/)
- [Plex Media Server Playlist API](https://apis.io/collections/plex/open-plex-playlist-api/)
- [Plex Media Server Preferences API](https://apis.io/collections/plex/open-plex-preferences-api/)
- [Plex Media Server Provider API](https://apis.io/collections/plex/open-plex-provider-api/)
- [Plex Media Server Rate API](https://apis.io/collections/plex/open-plex-rate-api/)
- [Plex Media Server Search API](https://apis.io/collections/plex/open-plex-search-api/)
- [Plex Media Server Status API](https://apis.io/collections/plex/open-plex-status-api/)
- [Plex Media Server Subscriptions API](https://apis.io/collections/plex/open-plex-subscriptions-api/)
- …and 4 more published on APIs.io

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Plex Media Server Overlay](https://apis.io/overlays/plex/plex-media-server-overlay/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Plex Authentication](https://apis.io/security/plex/plex-authentication/)
- [Plex Domain Security](https://apis.io/security/plex/plex-domain-security/)
- [Plex Vulnerability Disclosure](https://apis.io/security/plex/plex-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Plex Scopes](https://apis.io/scopes/plex/plex-scopes/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.plex.tv/)
- [Documentation](https://developer.plex.tv/pms/)
- [Getting started](https://developer.plex.tv/pms/#section/API-Info/Authenticating-with-Plex)
- [API reference](https://developer.plex.tv/pms/)
- [Pricing](https://www.plex.tv/plans/)
- [Sign up](https://www.plex.tv/sign-up/)
- [Support](https://support.plex.tv/)
- [Blog](https://www.plex.tv/blog/)
- [Security](https://support.plex.tv/articles/reporting-security-issues/)
- [Terms of service](https://www.plex.tv/about/privacy-legal/plex-terms-of-service/)
- [Privacy policy](https://www.plex.tv/about/privacy-legal/)
- [GitHub](https://github.com/plexinc)
- [Status](https://status.plex.tv/)

## API Evangelist rating

**Kin Score 54.2** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 75.0 |
| Contract quality | 58.1 |
| Contract governance | 4.5 |
| Operational transparency | 60.5 |
| Developer ergonomics | 58.9 |
| Access clarity | 44.7 |

**Agent readiness 59.6** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | documented (partial credit) |
| MCP Server | verified |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | verified |
| Rate Limit Signal | verified |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | yes |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | mostly |

**Regulatory alignment 40.2** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/plex/](https://apis.io/providers/plex/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Plex: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/plex/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
