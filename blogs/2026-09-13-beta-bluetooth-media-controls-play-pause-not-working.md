---
title: "[BETA] Bluetooth media controls (play/pause) not working reliably"
url: "https://forums.plex.tv/t/beta-bluetooth-media-controls-play-pause-not-working-reliably/942413#post_14"
date: "2026-09-13"
author: "@elan"
feed_url: "https://forums.plex.tv/posts.rss"
---
Progress, and it may be the same root cause as another report today. The old app declared a media button receiver and the rewrite dropped it, which means a press only lands if we are the session Android currently considers in charge. When a Bluetooth route drops that is briefly not us, and the press has nowhere to go, which fits your dropped presses and the Sony needing a throwaway first one.
