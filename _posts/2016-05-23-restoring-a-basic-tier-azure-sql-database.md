---
title: "Restoring a Basic Tier Azure SQL Database"
date: 2016-05-23 18:25:39
layout: post
author: "k2byew"
---
Importing/restoring BACPAC to create new Azure SQL database?

If the new database is a Basic (SLOW database), the import will take a long time.

Make sure the process is fully finished before actually using the database.

Tip: It is also possible to make the target database a higher tier to havae a quick import, then reduce it back down.
