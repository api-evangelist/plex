---
title: "Audio Track Loudness Analysis Slow - loudnorm vs. ebur128"
url: "https://forums.plex.tv/t/audio-track-loudness-analysis-slow-loudnorm-vs-ebur128/944015?page=2#post_24"
date: "2026-10-10"
author: "@OttoKerner"
feed_url: "https://forums.plex.tv/posts.rss"
---
To do it properly, the transcoder needs to know about peak levels over the course of the whole video. Which is why it has to be analysed in advance. Without that information, you’ll either don’t get the levels as high they could be, or you may encounter “compressor pumping”.
