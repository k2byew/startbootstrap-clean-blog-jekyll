---
title: "Enable Javascript Gzip Compression on AWS Elastic Beanstalk's Nginx"
date: 2016-05-02 18:31:35
layout: post
author: "k2byew"
---
Elastic Beanstalk already got an option to enable compression in its web console.

However, currently it only compress these MIME types:

`text/html text/plain text/css application/json application/x-javascript text/xml application/xml application/xml+rss text/javascript`

This can be seen in `/etc/nginx/conf.d/00_elastic_beanstalk_proxy.conf`


Their default is missing `application/javascript`, which can result in *.js not being compressed even when the option is enabled.

Until AWS update their AMI, a configuration file in the `.ebextensions` directory can be used to add any additional MIME type:


    files:
      /etc/nginx/conf.d/custom-gzip-types.conf:
        content: |
          gzip_types text/html text/plain text/css application/json application/x-javascript text/xml application/xml application/xml+rss text/javascript application/javascript;
    
    container_commands:
      remove_default_aws_nginx_gzip_types:
        command: |
          sed -i '/gzip_types/d' /tmp/deployment/config/#etc#nginx#conf.d#00_elastic_beanstalk_proxy.conf
