---
title: "Elastic Beanstalk Time Drift"
date: 2015-11-01 18:06:23
layout: post
author: "k2byew"
---
Turns out AWS Elastic Beanstalk requires internet access so it can reach NTP servers. Without keeping the time in sync, deployments can stop working.

When the time drifts into the future even by 2 minutes, the deployment messages from the queue are disgarded since they are considered too old!

Having weird Elastic Beanstalk deployment issues? Check the time with `date` command.