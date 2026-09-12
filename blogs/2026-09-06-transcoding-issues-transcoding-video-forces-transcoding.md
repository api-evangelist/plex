---
title: "Transcoding Issues: Transcoding Video Forces Transcoding Audio & Dropping HDR"
url: "https://forums.plex.tv/t/transcoding-issues-transcoding-video-forces-transcoding-audio-dropping-hdr/942596#post_4"
date: "2026-09-06"
author: "@OttoKerner"
feed_url: "https://forums.plex.tv/posts.rss"
---
IcyMidnight: I had to turn on hardware acceleration to see the HEVC option, but even with it turned on, H264 persisted as the output. For this to work, your server hardware needs to have support for hardware transcoding and hardware encoding to HEVC in HDR with 10-bit color. And even then, your Docker config needs to properly pass through this ability into the Plex container.
