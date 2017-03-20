---
title: "Can't Do Multiple greps? Do Multiple awks!"
date: 2016-10-28 18:32:43
layout: post
author: "k2byew"
---
eg. `tail -f log.file | grep server1 | grep server2` won't work...


Instead try awk with regex pattern placed inside slashes:

eg. `tail -f log.file | awk '/server1/ && /server2/'`

eg. `tail -f /var/log/pihole.log | awk '/query\[A\]/ && /10.8.0/'`
