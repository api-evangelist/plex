---
name: Administer Plex server maintenance, scans and updates
description: Trigger and monitor library refreshes, run Butler maintenance tasks, read and set preferences, and check for server updates — the owner-only administrative surface.
api: openapi/plex-media-server-openapi.json
operations:
  - libraryGetSections
  - librarySectionPostRefresh
  - librarySectionDeleteRefresh
  - libraryPostSectionsRefresh
  - libraryDeleteSectionsAllRefresh
  - librarySectionPutAnalyze
  - butlerGetSlash
  - butlerPostTask
  - butlerDeleteTask
  - preferencesGetSlash
  - preferencesGetGet
  - preferencesPutSlash
  - updaterGetStatus
  - updaterPutCheck
  - activitiesGetSlash
---

# Administer Plex server maintenance, scans and updates

Every operation here requires the **server owner's** token. A shared-user token
gets `403`.

## Steps

1. **Find the section — `libraryGetSections`.**
   `GET /library/sections/all` to resolve the `sectionId` you intend to act on.

2. **Check nothing is already running — `activitiesGetSlash`.**
   `GET /activities`. Starting a second scan over a library that is mid-scan wastes
   the server's disk and produces no useful result.

3. **Refresh one section — `librarySectionPostRefresh`.**
   `POST /library/sections/{sectionId}/refresh` scans that library for new and
   changed files. `DELETE /library/sections/{sectionId}/refresh`
   (`librarySectionDeleteRefresh`) stops it.

   `libraryPostSectionsRefresh` (`POST /library/sections/refresh`) refreshes **all**
   sections, and `libraryDeleteSectionsAllRefresh`
   (`DELETE /library/sections/all/refresh`) stops all refreshes. Prefer the
   single-section form — the all-sections form can saturate the server for hours.

   `503` on `librarySectionPostRefresh` means the server cannot refresh a music
   library while signed out.

4. **Analyze media — `librarySectionPutAnalyze`.**
   `PUT /library/sections/{sectionId}/analyze` recomputes media properties. This is
   CPU-heavy; treat it like a scan.

5. **Butler maintenance tasks — `butlerGetSlash`, `butlerPostTask`,
   `butlerDeleteTask`.**
   `GET /butler` lists the scheduled maintenance tasks the server knows about.
   `POST /butler/{task}` starts one immediately; `DELETE /butler/{task}` stops it.
   Butler tasks are the deep-maintenance jobs (database optimisation, thumbnail
   generation, credit and intro detection) that normally run on a nightly window —
   running one on demand competes with playback transcoding.

6. **Preferences — `preferencesGetSlash`, `preferencesGetGet`,
   `preferencesPutSlash`.**
   `GET /:/prefs` returns every server preference with its type, default and
   allowed values. `GET /:/prefs/get` reads one. `PUT /:/prefs` sets them —
   setting a preference that does not exist returns `400` or `403`, so read the
   preference list first and write only names it returned.

7. **Updates — `updaterGetStatus`, `updaterPutCheck`.**
   `GET /updater/status` reports whether an update is available.
   `PUT /updater/check` re-checks.

   `updaterPutApply` (`PUT /updater/apply`) **restarts the server and interrupts
   every active stream.** It is deliberately excluded from this skill's
   operation list. Do not call it without explicit human instruction.

## Rules

- Scans, analyses and Butler tasks are **long-running and asynchronous**. They
  return immediately; poll `activitiesGetSlash` for progress. Do not re-issue the
  trigger because nothing appeared to happen.
- No idempotency key exists. A retried refresh starts a second scan.
- `403` almost always means "not the owner's token", not "wrong URL".
- Read `conventions/plex-conventions.yml` before writing any preference.
