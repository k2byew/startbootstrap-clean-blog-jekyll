---
title: "Stop cron Logging into auth.log and syslog"
date: 2016-12-20 18:12:43
layout: post
author: "k2byew"
---
Sometimes too much logs is as good as no logs...

Update `/etc/syslog.conf` and restart syslog:

From

`*.*;auth,authpriv.none`	-/var/log/syslog`

To

`*.*;cron,auth,authpriv.none	-/var/log/syslog`

Can also add a new line to put cron logs somewhere else:

`cron.*	/var/log/cron`

Can also logrotate the new cron log by including it in `/etc/logrotate.d/syslog`


References:

[http://serverfault.com/questions/31334/how-can-i-prevent-cron-from-filling-up-my-syslog](http://serverfault.com/questions/31334/how-can-i-prevent-cron-from-filling-up-my-syslog)

[https://ubuntuforums.org/showthread.php?t=1256801](https://ubuntuforums.org/showthread.php?t=1256801)
