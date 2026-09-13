---
title: "Plexamp [Beta] 4.50.3 not recognized by Samsung Routines as media player any longer"
url: "https://forums.plex.tv/t/plexamp-beta-4-50-3-not-recognized-by-samsung-routines-as-media-player-any-longer/942431#post_3"
date: "2026-09-13"
author: "@elan"
feed_url: "https://forums.plex.tv/posts.rss"
---
Sorry for the slow reply, and you were right about the cause. The old app declared a media button receiver and the rewrite dropped it, so Android no longer has anything to hand a “start playing” request to. That is why we fell off the Routines list.
