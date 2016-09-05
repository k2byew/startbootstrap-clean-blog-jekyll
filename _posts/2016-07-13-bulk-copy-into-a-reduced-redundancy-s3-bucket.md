---
title: "Bulk Copy into a Reduced Redundancy S3 Bucket"
date: 2016-07-13 18:01:54
layout: post
author: "k2byew"
---
Quickly bulk copy data onto S3 with Reduced Redundancy for some quick Lambda processing:

`aws s3 cp --storage-class REDUCED_REDUNDANCY . s3://to-be-processed-with-lambda/`
