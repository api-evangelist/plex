---
title: "Plex Check IP Address Or Domains"
url: "https://forums.plex.tv/t/plex-check-ip-address-or-domains/942271#post_5"
date: "2026-08-30"
author: "@Volts"
feed_url: "https://forums.plex.tv/posts.rss"
---
This won’t work how you’re thinking. For Plex to be accessible inbound from the Internet over the normal WAN IP, the Plex server’s default outbound route must also be the normal WAN path. When a client connects to the external WAN IP, the WAN router translates that connection to Plex’s internal IP.
