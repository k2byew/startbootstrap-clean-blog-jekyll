---
title: "Running Headless JMeter on a Mac"
date: 2016-09-03 18:14:27
layout: post
author: "k2byew"
---
To install JMeter: `brew install jmeter --with-plugins`

To run JMeter headless: `jmeter -n -t myLoadTest.jmx -l myLoadTestResults.jtl`

Notes:
- To use the recorder, may need to run as root
- On a Mac, SSL cert generated here: `/usr/local/Cellar/jmeter/3.0/libexec/bin`
- Load it up in browser before recording.
