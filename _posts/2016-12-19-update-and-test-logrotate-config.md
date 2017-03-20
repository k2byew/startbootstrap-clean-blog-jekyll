---
title: "Update and Test Logrotate Config"
date: 2016-12-19 18:22:43
layout: post
author: "k2byew"
---
Tomcat can auto-reload the *.war in its webapps directory. To automatically run `sbt pckage` and update Tomcat's *.war after you save your code on macOS:

`brew install fswatch`

`fswatch -o -r /src-directory-to-watch/ | xargs -n1 -- sh -c 'sbt package && rm -f /path-to-tomcat/webapps/ROOT.war && ln -s /path-to-project/target/my-project-SNAPSHOT.war /path-to-tomcat/webapps/ROOT.war'`


To run Tomcat and output its logs to console to watch auto-deploy happening:

`./catalina.sh run`
