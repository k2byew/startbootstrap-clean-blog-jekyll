---
title: "S3 with CloudFront requires public S3 access"
date: 2016-06-02 17:25:14
layout: post
author: "k2byew"
---
Got CloudFront in-front of S3 to speed up website hosting?
Need to make S3 publicly accessible? Yes!
Updating S3 bucket policy also restricts CloudFront access.
So can IP restrict on S3 bucket, and make CloundFront less accessible!

Steps to quickly setup S3 hosting with CloudFront:
Name the bucket to match website domain name, CloudFront CNAME to match domain name, then in Route53, point an A-record alias to CloudFront.
