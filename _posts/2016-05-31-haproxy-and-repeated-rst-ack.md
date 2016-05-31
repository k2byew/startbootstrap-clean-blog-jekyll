---
title: "HAProxy and repeated [RST, ACK]"
date: 2016-05-31 18:29:15
layout: post
author: "k2byew"
---
Resolving connectivity issues which involves a HAProxy between two servers, and after doing a `tcpdump` (or actually `sudo tcpdump -i eth0 port not 22 -w capture.pcap` which removes SSH), you find that there are a lot of `[RST, ACK]` from the reverse proxy?


If these happen at 2s intervals, which matches the default health check interval of HAProxy, then it's likely that it's just HAProxy doing health checks - it's not trying to randomly reset connections. These health checks are enabled by simply appending `check` at the end of the server hostname in the backend section of `haproxy.cfg`.


More information [here](https://www.haproxy.com/doc/aloha/7.0/haproxy/healthchecks.html).
