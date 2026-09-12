---
title: "Expired certificate and rate limiting"
url: "https://forums.plex.tv/t/expired-certificate-and-rate-limiting/942610#post_1"
date: "2026-09-06"
author: "@BetaChess"
feed_url: "https://forums.plex.tv/posts.rss"
---
I’m running Plex Media Server on Fedora Linux, version 1.43.0.10492 . My cert-v2.p12 has expired, and certificate renewal is currently failing with: Failed to upload CSR: 429 I found this thread describing what appears to be the same issue: https://forums.plex.tv/t/unable-to-connect-to-server-securely/942579 I’ve verified that the Plex data directory and Cache directory are owned by the plex user and are writable. I’ve also stopped Plex Media Server, backed up and removed Cache/cert-v2.p12 , and have left PMS stopped for now.
