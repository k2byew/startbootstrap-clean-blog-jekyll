---
title: "List and Save Installed Debian Packages"
date: 2016-07-26 18:51:16
layout: post
author: "k2byew"
---
List and save installed Debian packages:

`dpkg --get-selections | grep -v deinstall > installed-pkg.txt`
