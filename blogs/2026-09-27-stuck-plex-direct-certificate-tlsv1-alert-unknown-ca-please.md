---
title: "Stuck plex.direct certificate — tlsv1 alert unknown ca — please reset (Docker/WSL)"
url: "https://forums.plex.tv/t/stuck-plex-direct-certificate-tlsv1-alert-unknown-ca-please-reset-docker-wsl/943460#post_9"
date: "2026-09-27"
author: "@mjlauk"
feed_url: "https://forums.plex.tv/posts.rss"
---
Solved, thanks! I enabled Strict TLS configuration, moved cert-v2.p12 aside and restarted. The new cert chains YR2 → Root YR → ISRG Root X1 (cross-signed) and verifies with return code 0.
