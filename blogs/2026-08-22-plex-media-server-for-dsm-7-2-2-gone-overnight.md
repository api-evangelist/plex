---
title: "Plex Media Server for DSM 7.2.2 gone overnight"
url: "https://forums.plex.tv/t/plex-media-server-for-dsm-7-2-2-gone-overnight/941996#post_5"
date: "2026-08-22"
author: "@OptiZonion"
feed_url: "https://forums.plex.tv/posts.rss"
---
Well I found the cause : it seems that after an update of my NAS ealier this week (Tuesday I think), an adguard container started, although I remembered disabling its autostart as I didn’t complete the config just yet. Weirdly enough, it seems that it started to impact my Plex connectivity some time yesterday, starting with the media scrapping before blocking the server; perhaps some adguard list was updated, blocking Plex related addresses. I stopped the adguard container (and unthicked the autostart option), restarted the Plex package and the server was back on.
