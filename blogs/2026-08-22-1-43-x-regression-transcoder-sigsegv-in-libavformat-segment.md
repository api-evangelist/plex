---
title: "[1.43.x regression] Transcoder SIGSEGV in libavformat segment muxer (matroska/ssegment)"
url: "https://forums.plex.tv/t/1-43-x-regression-transcoder-sigsegv-in-libavformat-segment-muxer-matroska-ssegment/942004#post_1"
date: "2026-08-22"
author: "@Niklas_2604"
feed_url: "https://forums.plex.tv/posts.rss"
---
Server Version#: 1.43.3.10896-cb3ebc72d (Docker, lscr.io/linuxserver/plex ) Player Version#: Dont know the version of the player, its from another persons Fire TV Stick (newest app with new ui) Summary Every transcode session that outputs Matroska segments ( -segment_format matroska -f ssegment ) crashes the Plex Transcoder with SIGSEGV before a single segment is written. PMS logs Unable to create output stream for transcode session, no segments found and playback fails on the client. mpegts segments, DASH, and -f null all work fine.
