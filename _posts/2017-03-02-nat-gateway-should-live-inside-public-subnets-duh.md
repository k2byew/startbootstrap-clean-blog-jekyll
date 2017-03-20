---
title: "NAT Gateway Should Live Inside Public Subnets, Duh!"
date: 2017-03-02 18:12:32
layout: post
author: "k2byew"
---
When creating a NAT Gateway, even though it's used by a private subnet, remember to create it inside a public subnet.

It is just a NAT instance replacement, but AWS allows you to create it in a private subnet (or more proceisly, in a subnet currently associated to a routing table without a 0.0.0.0/0 route to a internet gateway) with no warnings or errors, even though it'll never reach the internet.

This makes complete sense, except when the brain automatically selects the private subnet when creating the NAT gateway, thinking that this is the subnet you are creating a NAT gateway for...
