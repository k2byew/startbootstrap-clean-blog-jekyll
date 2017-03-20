---
title: "Sync Time With NTPD When Using a AWS NAT Gateway"
date: 2016-11-25 18:05:26
layout: post
author: "k2byew"
---
Using a AWS NAT Gateway instead of creating a NAT Instance, but for some reason system clock goes out of sync, and potentially Elastic Beanstalk applications are failing health checks?

It may be that the Network ACL governing the NAT Gateway doesn't have NAT Gateway's ephemeral ports opened. More specifically, it's UDP ephemeral ports opened since that's what NTP will use.

The Network ACL should allow incoming and outgoing traffic on UDP port 123 for the EC2 instance trying to sync time, and also incoming UDP ports 1024-65535 for the NAT Gateway. If the ephemeral ports are not opened for the NAT Gateway, incoming replies from NTP servers won't be received. This step wasn't necessary before with the NAT Instance.

Some NTP troubleshooting may include:

Check if ntpd is successfully syncing the time.

`ntpstat` - checks current synchronisation status

Syncing successfully:
    synchronised to NTP server (171.66.97.126) at stratum 2
       time correct to within 533 ms
       polling server every 1024 s

Syncing failed:
    unsynchronised
      time server re-starting
       polling server every 8 s

Manually trigger a sync to troubleshoot:
`ntpdate -u` - will not use UDP port 123, it will use a non-previleged port
`sudo /etc/init.d/ntpd stop`
`sudo ntpdate -s 0.amazon.pool.ntp.org` - will use UDP port 123, but only works when ntpd is stopped

`ntpdate` will log into Syslog instead of stdout, to view: `sudo tail -f /var/log/messages`
Fails: `ntpdate: no server suitable for synchronization found`
Working: `ntpdate: adjust time server 45.33.91.95 offset -0.006298 sec`

Check if updates are actually sending traffic: `sudo tcpdump -i eth0 dst port 123 or src port 123 -nn`

Everything using UDP port 123, so check if Security Group and Network ACLs are allowing this through.

Security group is stateful so don't have to worry about incoming, Network ACLs are stateless and UDP port 123 should be opened for incoming and outgoing traffic.

Network ACL for the NAT Gateway should have its ephemeral ports opened: TCP and UDP 1024-65535.

`sudo /etc/init.d/ntpd restart` - after updating Network ACLs, restart ntpd service then verify sync with `ntpstat`
