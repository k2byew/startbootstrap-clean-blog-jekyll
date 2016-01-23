---
title: "Demux Audio From MP4 and Encode Into MP3"
date: 2016-01-14 18:13:54
layout: post
author: "k2byew"
---
Got a bunch of *.mp4 in a directory and want to strip out the audio and encode them as MP3?

`for i in *.mp4; do avconv -i "${i}" -vn -f mp3 -q:a 5 "${i%.mp4}.mp3"; done`

Quality is set using `-q:a 5`, which equals to LAME's `-V5`

[Quality flag conversion chart](https://trac.ffmpeg.org/wiki/Encode/MP3)
