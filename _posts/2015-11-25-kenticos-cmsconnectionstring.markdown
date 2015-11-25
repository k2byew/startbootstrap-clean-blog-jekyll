---
title: "Kentico's CMSConnectionString"
date: 2015-11-25 18:14:08
layout: post
author: "k2byew"
---
What's wrong with: `Server=tcp:servername.database.com:1433;Database=myDatabase;User ID=username;Password=password;Trusted_Connection=False;Encrypt=True;Connection Timeout=30;Max Pool Size=180`?

It's using `:` before the port number, instead of `,` Not exactly what's expected!

The correct CMSConnectionString is `Server=tcp:servername.database.com,1433;Database=myDatabase;User ID=username;Password=password;Trusted_Connection=False;Encrypt=True;Connection Timeout=30;Max Pool Size=180`
