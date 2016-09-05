---
title: "IAM Policies Fail to Lock Down S3 Buckets"
date: 2016-08-09 18:25:34
layout: post
author: "k2byew"
---
Locked down IAM policies on S3, but still got access to some S3 buckets?

Might be allowed by individual S3 bucket policies.

S3 buckets open to the world, obviuosly won't be limited to IAM user just because the user has limited access locked down by IAM

More info: https://blogs.aws.amazon.com/security/post/TxPOJBY6FE360K/IAM-policies-and-Bucket-Policies-and-ACLs-Oh-My-Controlling-Access-to-S3-Resource
