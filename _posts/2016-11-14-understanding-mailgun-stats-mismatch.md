---
title: "Understanding Mailgun Stats Mismatch"
date: 2016-11-14 18:15:32
layout: post
author: "k2byew"
---
Mails not dropped or suppressed, but incoming mail doesn't match the accepted count? All mails are accepted and also delivered as well?

Turns out the mail logs from the past month shows the difference between incoming and accepted being those that had an envelope. Sender field of "None", NDRs, OOOs, and other random system messages are discarded.
