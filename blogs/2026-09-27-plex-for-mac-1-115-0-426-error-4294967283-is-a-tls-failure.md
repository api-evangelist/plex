---
title: "Plex for Mac 1.115.0.426: error 4294967283 is a TLS failure caused by a stale bundled CA file"
url: "https://forums.plex.tv/t/plex-for-mac-1-115-0-426-error-4294967283-is-a-tls-failure-caused-by-a-stale-bundled-ca-file/943508#post_1"
date: "2026-09-27"
author: "@thebluecircle"
feed_url: "https://forums.plex.tv/posts.rss"
---
Server Version#: 1.43.4.10903-e5521bd8c (macOS 26.7, Apple silicon) Player Version#: Plex for Mac 1.115.0.426-4e960a1d (macOS 27.0) I think there have been a few related topics on this, however the Plex Mac App is failing due to an old, bundled encryption certificate: Symptom Every title fails immediately with “An unknown error occurred (4294967283)”. Plex Web, iOS and TV clients play the same items from the same server without problems. Direct Play and Direct Stream are enabled; turning hardware decoding off makes no difference.
