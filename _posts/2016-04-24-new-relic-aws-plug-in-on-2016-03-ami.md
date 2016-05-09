---
title: "New Relic AWS plug-in on 2016.03 AMI"
date: 2016-04-24 18:11:26
layout: post
author: "k2byew"
---
Following the steps here not enough:

https://github.com/newrelic-platform/newrelic_aws_cloudwatch_plugin


Got some tips here:

http://d.hatena.ne.jp/torazuka/20150724/ec2
http://stackoverflow.com/questions/6277456/nokogiri-installation-fails-libxml2-is-missing

End up doing something similar to:
    
    sudo gem install bundler
    sudo yum install -y ruby-devel gcc-c++ libxml2-devel libxslt libxslt-devel
    gem install nokogiri -v '1.5.9'
    gem install io-console
    bundle install


Perhaps installed a bit too many things through `yum install` but so far this works.
