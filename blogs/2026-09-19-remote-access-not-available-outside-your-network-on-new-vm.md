---
title: "Remote Access: Not available outside your network on new VM machine"
url: "https://forums.plex.tv/t/remote-access-not-available-outside-your-network-on-new-vm-machine/943079#post_4"
date: "2026-09-19"
author: "@alxj1"
feed_url: "https://forums.plex.tv/posts.rss"
---
Yep, this worked. I already verified I had full port forwarding so I tried this issue next. I went to /var/lib/plexmediaserver/Library/Application Support/Plex Media Server/ , deleted the entire Cache file, and now it’s able to connect to the internet.
