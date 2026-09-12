---
title: "Remote Watch Pass incorrectly triggered for local playback (app.plex.tv)"
url: "https://forums.plex.tv/t/remote-watch-pass-incorrectly-triggered-for-local-playback-app-plex-tv/942604#post_2"
date: "2026-09-06"
author: "@pshanew"
feed_url: "https://forums.plex.tv/posts.rss"
---
My first thought is that it’s likely due to DNS rebinding protection in your router’s DNS server. This will prevent *.plex.direct IP addresses from being resolved, which will cause the behavior you’re seeing (because it will fall back to trying a remote connection). To test this, set the DNS for the Wi-Fi connection on your iMac to a public DNS provider, such as 1.1.1.1 (CloudFlare) or 8.8.8.8 (Google), or both.
