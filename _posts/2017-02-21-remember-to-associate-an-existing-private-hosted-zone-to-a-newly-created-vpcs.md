---
title: "Remember to Associate an Existing Private Hosted Zone to a Newly Created VPCs"
date: 2017-02-21 18:44:18
layout: post
author: "k2byew"
---
DNS records inside a private hosted zone cannot be resolve for EC2 instances inside a newly created VPC

The new VPC needs to be manually associated to a previously created private hosted zones before DNS will be resolved, doable via Route53 web console

Also need to enable enableDnsHostnames, doable via VPC web console


References:

[http://docs.aws.amazon.com/Route53/latest/DeveloperGuide/hosted-zones-private.html](http://docs.aws.amazon.com/Route53/latest/DeveloperGuide/hosted-zones-private.html)

[http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/vpc-dns.html#vpc-dns-updating](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/vpc-dns.html#vpc-dns-updating)

[https://forums.aws.amazon.com/message.jspa?messageID=606504](https://forums.aws.amazon.com/message.jspa?messageID=606504)
