---
title: "Cronet ERR_NAME_NOT_RESOLVED with Private DNS"
url: "https://forums.plex.tv/t/cronet-err-name-not-resolved-with-private-dns/942255#post_2"
date: "2026-08-30"
author: "@TotoRoux"
feed_url: "https://forums.plex.tv/posts.rss"
---
After further investigations, it seems that DoT DNS servers like Adguard do not return records for plex.direct hostnames (some of them return an RFC1918 address). The error happens for theses hostnames, and the app does not try other server registered endpoints. I fixed my problem by configuring my custom DoT server to allow RFC1918 address to be returned.
