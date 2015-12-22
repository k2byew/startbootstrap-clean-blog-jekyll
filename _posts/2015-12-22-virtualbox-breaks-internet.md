---
title: "VirtualBox Breaks Internet"
date: 2015-12-22 17:42:18
layout: post
author: "k2byew"
---
Load up VirtualBox using Vagrant on Ubuntu, but guest has no internet access through NAT, and the usual tricks with Vagrant config doesn't work:

    config.vm.provider "virtualbox" do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
    end

Then... actually host lost internet due to DNS unresolved. Only a restart can fix the issue?
Turns out, there are some issues with vboxdrv, so just do a few `sudo /etc/init.d/vboxdrv restart` to bring back internet to the host and guest.
