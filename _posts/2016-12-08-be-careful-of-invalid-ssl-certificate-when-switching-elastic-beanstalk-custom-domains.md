---
title: "Be Careful of Invalid SSL Certificate When Switching Elastic Beanstalk Custom Domains"
date: 2016-12-08 18:29:24
layout: post
author: "k2byew"
---
Switching domain name for an API running on Elastic Beanstalk, but the client/front-end not ready to swap at the same time?

1. Create Route53 alias A-records to have both the old.domain and new.domain to point to the same Elastic Beanstalk application.
2. Create a HTTPS certificate, with additional DNS names to cover both the old.domain and new.domain to avoid outdated clients pointing to the old.domain getting security warning/errors.


When requesting new HTTPS certificate from AWS Certificate Manager, sometimes verification emails can be sent to the wrong address.

eg. dev-api.old.domain verification might be sent to webmaster@dev-api.old.domain instead of webmaster@old.domain

Use CLI instead of the web console:

`aws acm request-certificate --domain-name dev-api.old.domain --subject-alternative-names dev-api.new.domain staging-api.old.domain staging-api.new.domain --domain-validation-options DomainName=dev-api.old.domain,ValidationDomain=old.domain DomainName=staging-api.old.domain,ValidationDomain=old.domain DomainName=dev-api.new.domain,ValidationDomain=new.domain DomainName=staging-api.new.domain,ValidationDomain=new.domain`
