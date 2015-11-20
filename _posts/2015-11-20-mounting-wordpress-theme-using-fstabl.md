---
title: "Mounting WordPress Theme Using fstab"
date: 2015-11-20 18:02:56
layout: post
author: "k2byew"
---
Got [XAMPP](http://www.apachefriends.org) and working on a WordPress theme, but also need to commit to git repository?

Add this line in /etc/fstab to easily commit changes.

`/opt/lampp/apps/wordpress/htdocs/wp-content/themes /home/uername/git-repository/my-website/wp-content/themes none bind`
