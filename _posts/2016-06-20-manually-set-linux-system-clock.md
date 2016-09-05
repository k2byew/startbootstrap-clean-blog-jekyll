---
title: "Manually Set Linux System Clock"
date: 2016-06-20 18:15:44
layout: post
author: "k2byew"
---
Quickly manually update system time, when NTP decides to not work!

To update the clock with a slight drift (within the same day):

`date && sudo date +%T -s "12:34:56" && date`
