---
title: "Update and Test logrotate Config"
date: 2016-09-12 18:44:32
layout: post
author: "k2byew"
---
Got lots of logs written into /var/log/messages?

Might need to tune logrotate configuration for this specific log file.

Default values in /etc/logrotate.conf might not be suitable.

Eg. weekly log rotation, no compression - this will fill up a 8GB EC2 system drive before you know it!


To update config:

Remove `/var/log/messages` from `/etc/logrotate.d/syslog`

Create new config: `nano /etc/logrotate.d/syslog-messages`

Potential `syslog-messages` content:

    /var/log/messages {
        daily
        rotate 10
        missingok
        notifempty
        compress
        sharedscripts
        postrotate
            /bin/kill -HUP `cat /var/run/syslogd.pid 2> /dev/null` 2> /dev/null || true
        endscript
    }


To test out the config: `logrotate -d /etc/logrotate.d/syslog-messages -f`

To actually force run the config right now: `logrotate -v /etc/logrotate.d/syslog-messages -f`

Be careful that a pre-existing large log might mean you run out of hdd space, or CPU hogged for a while.


Notes:

[http://stackoverflow.com/questions/9679085/understanding-syslogd](http://stackoverflow.com/questions/9679085/understanding-syslogd)

[http://serverfault.com/questions/116201/logrotate-does-not-compress-var-log-messages](http://serverfault.com/questions/116201/logrotate-does-not-compress-var-log-messages)
