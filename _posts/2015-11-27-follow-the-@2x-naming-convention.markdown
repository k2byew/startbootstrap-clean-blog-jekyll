---
title: "Follow the @2x naming convention"
date: 2015-11-27 18:35:58
layout: post
author: "k2byew"
---
Normal logo file: `logo.png`
High resolution logo file: `logo2x.jpg`
Can't load high resolution file even though WordPress plugin/themes support it? Especially after you've already selected the high resolution version manually?
Rename high resolution file to `logo@2x.jpg`, and make sure it's sitting in the same path as logo.png

Using a WordPress theme which uses (`retina.js`)[http://imulus.github.io/retinajs/]?
Make sure the filename convention follows Apple's `@2x` naming scheme.

A theme might let you upload a higher resolution logo but without the right name, retina.js won't be able to grab the file for you.
