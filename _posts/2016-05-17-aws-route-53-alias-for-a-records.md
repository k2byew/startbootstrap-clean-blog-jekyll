---
title: "AWS Route 53 Alias for A Records"
date: 2016-05-17 18:11:41
layout: post
author: "k2byew"
---
When setting up a A record in AWS Route53, there is an "alias" option which means no CNAME is required to ELB, EBS, or S3 endpoints.

For a client, the alias will resolve to an IP directly, one less DNS lookup by client compared to using eg. a CNAME to the Elastic Beanstalk URL.

For more information and tips [here](https://cloudnative.io/blog/2015/03/aws-route-53-best-practices).
