---
title: "Decrypt SSL Certificates Before Loading it Into Nginx"
date: 2016-06-29 18:11:13
layout: post
author: "k2byew"
---
During service eg. nginx restarts, it'll ask for password. You don't know it? Then site stays down...

Decrypte it first then load it: `openssl rsa -in encrypted.key -out decrypted.key`
