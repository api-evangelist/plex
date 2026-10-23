---
title: "Android TV Plex App: External SRT Subtitles Not Displaying Special Characters"
url: "https://forums.plex.tv/t/android-tv-plex-app-external-srt-subtitles-not-displaying-special-characters/944506#post_10"
date: "2026-10-17"
author: "@pshanew"
feed_url: "https://forums.plex.tv/posts.rss"
---
On BSDs, Linux, macOS, WSL, the conversion can fairly easily be scripted using the file and iconv commands. For example, encoding = file -b --mime-encoding input.srt will show the input file’s current encoding. This can be used directly as an input to iconv : iconv -f "${encoding}" -t UTF-8 input.srt > output.srt There’s additional logic needed (converting the “encoding” value to lower-case, testing for errors, handling naming, etc.).
