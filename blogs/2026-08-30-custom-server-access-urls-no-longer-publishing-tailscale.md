---
title: "Custom server access URLs no longer publishing Tailscale IPs to api/resources"
url: "https://forums.plex.tv/t/custom-server-access-urls-no-longer-publishing-tailscale-ips-to-api-resources/942181?page=2#post_23"
date: "2026-08-30"
author: "@mathieu575"
feed_url: "https://forums.plex.tv/posts.rss"
---
Appreciate the link, but I don’t think it’s the same issue — what I’m running into isn’t intermittent connectivity or drops, it’s that Plex simply never publishes the Tailscale IP to api/resources at all, consistently and reproducibly, regardless of network mode, LAN Networks config, or whether anything’s manually added as Custom URL. The MagicDNS hostname, once set, works reliably and doesn’t have any stability issues — so this seems more specific to how PMS handles that address format than a broader remote access connectivity problem.
