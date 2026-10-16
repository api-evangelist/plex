---
title: "Aftermarket remotes not working with new Plex app"
url: "https://forums.plex.tv/t/aftermarket-remotes-not-working-with-new-plex-app/944314#post_1"
date: "2026-10-10"
author: "@DitaVeloci"
feed_url: "https://forums.plex.tv/posts.rss"
---
NOTE - Write up done with A.I and tweaked where required because i am lazy… Fix: Aftermarket (Firetv, harmony, etc) TV Remote Select/Middle Button Broken in new Plex app The Problem After recent Plex updates, the middle/select button on certain remotes stops working inside the app. Some testing lead me to discover (at least in my case) the remote was using NUMPAD_ENTER on scancode 96. Plex now ignores NUMPAD_ENTER and strictly requires DPAD_CENTER (Keycode 23).
