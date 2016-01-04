---
title: "Maven2 Together with Maven3"
date: 2016-01-05 17:12:33
layout: post
author: "k2byew"
---
This [post](http://dev-maziarz.blogspot.co.nz/2012/09/ubuntu-1204-installing-both-maven3-and.html) shows how Maven2 can be installed alongside Maven3.

Install Maven 2 as an alternative in `/usr/share/maven2`:

    cd /usr/share
    wget http://archive.apache.org/dist/maven/binaries/apache-maven-2.2.1-bin.tar.gz
    tar xzvf apache-maven-2.2.1-bin.tar.gz
    mv apache-maven-2.2.1 maven2
    rm apache-maven-2.2.1-bin.tar.gz


Want Maven3 by default, so set Maven2's priority to 100 and manually select it later:
`update-alternatives --install /usr/bin/mvn mvn /usr/share/maven2/bin/mvn 100 --slave /usr/bin/mvnDebug mvnDebug /usr/share/maven2/bin/mvnDebug`

To change which Maven version is used:
`update-alternatives --config mvn`

To view alternatives:
`update-alternatives --display mvn`
