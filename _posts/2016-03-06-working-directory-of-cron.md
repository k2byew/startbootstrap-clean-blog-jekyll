---
title: "Working Directory of Cron"
date: 2016-03-06 20:14:27
layout: post
author: "k2byew"
---
Got a bash script that is run periodically by cron but... doesn't actually work?

It can be because cron assumes the working directory is the HOME directory.


A bash script `/home/username/dir/test.sh` with the command `echo "test" > test.txt` won't write the file to `/home/username/dir` when this bash script is called by cron.
The file will be in `/home/username/test.txt` instead of `/home/username/dir/test.txt`
