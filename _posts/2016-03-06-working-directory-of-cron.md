---
title: "Working Directory of Cron"
date: 2016-03-06 20:14:27
layout: post
author: "k2byew"
---
Got a bash script that is run periodically by cron but... doesn't actually work?

It can be because cron assumes the working directory is the HOME directory, which breaks any relative paths that might have been used in the script.


A bash script `/home/username/dir/test.sh` with the command `echo "test" > test.txt` won't write the file to `/home/username/dir` when this bash script is called by cron.

The file will be in `/home/username/test.txt` instead of `/home/username/dir/test.txt`

A quick way to make the bash script work with cron, add `cd $(dirname $0)` to the begining of the bash script, so the script enters into the directory where the script is, and all relative paths will work again.
