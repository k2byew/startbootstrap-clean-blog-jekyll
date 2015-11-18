---
title: "Deploying Node.js app into Heroku"
date: 2015-10-23 17:55:06
layout: post
author: "k2byew"
---
Expect the unexpected:

- Use `var port = process.env.PORT || 9000;` Heroku sets its own PORT env variable, and exposes it to you as port 80. Don't try to define or access a custom port.
- No way to SSH into running app
- Start a new dyno and SSH into it: `heroku run bash --app webhook-to-md`
- Restart: heroku restart --app webhook-to-md
- View logs: `heroku logs --tail --app webhook-to-md`
- After deployment or restart, can see: Stopping all processes with SIGTERM and Process exited with status 143. Don't worry, app is still running. These logs just comes a bit late.
- Crash your app? It restarts automatically. Do it too much or fatally? Heroku shows error page and stop the restarts.