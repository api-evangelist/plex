---
title: "UltraBlurProcessor crashes on transparent PNG artwork (clearLogos/clearArt)"
url: "https://forums.plex.tv/t/ultrablurprocessor-crashes-on-transparent-png-artwork-clearlogos-clearart/939397#post_5"
date: "2026-09-06"
author: "@Spaatz"
feed_url: "https://forums.plex.tv/posts.rss"
---
Update: Still reproducible on PMS 1.43.4.10903 Server version: 1.43.4.10903-e5521bd8c Platform: Windows 10.0, build 26220 This issue remains present on the latest Plex Pass beta available to me. Graylog (system logging too) recorded 28,390 UltraBlurProcessor log lines in 24 hours , including 1,720 in one hour and bursts exceeding 225 lines per minute . The repeating sequence is: [UltraBlurProcessor] Failed to get color palette: Empty pixels when quantize [UltraBlurProcessor] Failed to select colors These messages originate from Plex Media Server.log .
