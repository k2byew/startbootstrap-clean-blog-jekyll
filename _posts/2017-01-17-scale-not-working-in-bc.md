---
title: "scale Not Working in bc?"
date: 2017-01-17 18:12:25
layout: post
author: "k2byew"
---
Using `bc` but `scale` isn't working? Have to use divide for for scale to work:

    fiftyPercent=$(bc <<< "scale=0;$fullAmount * 0.5 / 1")
    ninetyPercent=$(bc <<< "scale=0;$fullAmount * 0.9 / 1")
    hundredAndTenPercent=$(bc <<< "scale=0;$fullAmount * 1.1 / 1")


Reference

[http://askubuntu.com/questions/217570/bc-set-number-of-digits-after-decimal-point](http://askubuntu.com/questions/217570/bc-set-number-of-digits-after-decimal-point)
