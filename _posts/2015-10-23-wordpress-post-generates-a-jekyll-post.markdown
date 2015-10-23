---
title: "Wordpress post generates a Jekyll post"
date: 2015-10-23 11:07:47
layout: post
author: "k2byew"
---
Thought it would be interesting to generate static blog posts for Jekyll, every time a new post is added in Wordpress.

1. Add Wordpress webhook plugin HookPress to trigger when a new post is published
2. A Node.js app on Heroku listens for webhooks (https://github.com/k2byew/webhook-to-md)
3. Node.js app commits a new *.md post in a Jekyll blog repository (https://github.com/k2byew/startbootstrap-clean-blog-jekyll)
4. Codeship builds the Jekyll blog after each Jekyll blog repository commit, and uploads to surge.sh which hosts the static blog