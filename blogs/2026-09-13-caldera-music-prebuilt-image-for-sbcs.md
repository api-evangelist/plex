---
title: "Caldera Music Prebuilt Image for SBCs"
url: "https://forums.plex.tv/t/caldera-music-prebuilt-image-for-sbcs/939605?page=4#post_68"
date: "2026-09-13"
author: "@Joo"
feed_url: "https://forums.plex.tv/posts.rss"
---
Joo: speaker-test -c2 -twave Okay, I was able to solve the problem. Maybe this will help someone who runs into the same issue. The crucial point was that, in my setup, the HiFiBerry Digi output reports 44.1 kHz in the ALSA device list but actually only outputs 48 kHz reliably.
