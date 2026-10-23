---
title: "Plex Media Server 1.43.4.10903 on Ubuntu 26.04.1 LTS — Remote Access“Not available” bug"
url: "https://forums.plex.tv/t/plex-media-server-1-43-4-10903-on-ubuntu-26-04-1-lts-remote-access-not-available-bug/944556#post_15"
date: "2026-10-17"
author: "@retro1982"
feed_url: "https://forums.plex.tv/posts.rss"
---
I am running my plex through a haproxy, which handles my wildcard certificate. Sine I have used this configuration, remote access is reporting in the admin web ui as failed. Nether the less, it is working ever since, it is only the check which is failing (I think because of the unknown cert which is delivered instead of the plex certificate) What I wanted to say is, check if it is working from the outside (without relay) and if it is, it may just been the test which is failing.
