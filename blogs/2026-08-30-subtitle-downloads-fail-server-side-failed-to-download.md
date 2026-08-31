---
title: "Subtitle downloads fail server-side (\"Failed to download subtitle\") — metadata.provider.plex.tv retu"
url: "https://forums.plex.tv/t/subtitle-downloads-fail-server-side-failed-to-download-subtitle-metadata-provider-plex-tv-retu/941728#post_4"
date: "2026-08-30"
author: "@reallove"
feed_url: "https://forums.plex.tv/posts.rss"
---
I’m seeing the exact same issue on a native Synology installation. Server: Plex Media Server 1.43.3.10896-cb3ebc72d Platform: Synology DS1525+, DSM 7.4.1 Subtitle searches succeed and return multiple OpenSubtitles results, but selecting any result fails in the client with “Uh-oh! There was an error.” With debug logging enabled, PMS accepts the download request with HTTP 200, but receives only 99 bytes: Activity: registered new activity ...
