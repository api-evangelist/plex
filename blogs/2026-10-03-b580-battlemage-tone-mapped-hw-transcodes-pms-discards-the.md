---
title: "B580 (Battlemage): tone-mapped HW transcodes, PMS discards the finished job and silently restarts"
url: "https://forums.plex.tv/t/b580-battlemage-tone-mapped-hw-transcodes-pms-discards-the-finished-job-and-silently-restarts/941533#post_4"
date: "2026-10-03"
author: "@rulleeeee"
feed_url: "https://forums.plex.tv/posts.rss"
---
Same abort on an Arrow Lake iGPU with hevc_vaapi output, still present in 1.43.4.10903 (Drafted with Claude Code, which I used to debug) Not Arc-specific and not H.264-specific. Minisforum MS-02 Ultra, Core Ultra 9 285HX integrated graphics ( 8086:7d67 ) under i915 , PMS in an unprivileged Debian 13 LXC on Proxmox VE 9.2.11, kernel 7.0.14-12-pve, /dev/dri/renderD128 passed through. The client is an NVIDIA SHIELD TV transcoding 2160p Dolby Vision (profile 8) / HDR10 HEVC to 4K HEVC SDR.
