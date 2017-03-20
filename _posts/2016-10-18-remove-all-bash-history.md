---
title: "Remove All Bash History"
date: 2016-10-18 18:52:13
layout: post
author: "k2byew"
---
When building AWS AMI, or when taking EC2 snapshots you want to remove all bash history, here's a one-liner:

`cat /dev/null > ~/.bash_history && history -c && exit`


Reference:

[http://askubuntu.com/questions/191999/how-to-clear-bash-history-completely](http://askubuntu.com/questions/191999/how-to-clear-bash-history-completely)
