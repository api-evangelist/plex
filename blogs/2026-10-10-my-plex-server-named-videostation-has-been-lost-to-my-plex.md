---
title: "My Plex Server named VideoStation has been lost to my Plex.tv account since the recent update"
url: "https://forums.plex.tv/t/my-plex-server-named-videostation-has-been-lost-to-my-plex-tv-account-since-the-recent-update/944282#post_2"
date: "2026-10-10"
author: "@OttoKerner"
feed_url: "https://forums.plex.tv/posts.rss"
---
Ensure that your local DNS resolver doesn’t cause an issue with “DNS rebinding protection”: https://support.plex.tv/articles/206225077-how-to-use-secure-server-connections#toc-4 If you recently changes something about your home network (new router, new router firmware, devices added etc), ensure that Windows still uses “private” as the category of its network connection. It must not be “public”. Settings - [server name] - Network - ‘Show Advanced’ - Strict TLS configuration Then stop and restart your server.
