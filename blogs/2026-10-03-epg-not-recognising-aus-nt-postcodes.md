---
title: "EPG not recognising Aus NT postcodes"
url: "https://forums.plex.tv/t/epg-not-recognising-aus-nt-postcodes/943852#post_3"
date: "2026-10-03"
author: "@bmanfield"
feed_url: "https://forums.plex.tv/posts.rss"
---
I’ve looked into this further, and it isn’t a postcode-parsing problem. Plex’s guide service simply has no lineups mapped to Northern Territory postcodes. Using the server’s lineup lookup (/livetv/epg/countries/aus/tv.plex.providers.epg.cloud/lineups?postalCode=…): NT postcodes 0800, 0810, 0820, 0830, 0840, 0850 (Katherine) and 0870 (Alice Springs) all return 0 lineups.
