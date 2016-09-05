---
title: "HowTo: Lose all your DNS records with Namecheap"
date: 2016-09-04 18:27:12
layout: post
author: "k2byew"
---
1. Have a domain with WhoisGuard on
2. Keep the domain active but let WhoisGuard expire
3. Wait a few days until ICAAN error page appear
4. Purchase WhoisGuard again
4. Stuck scratching your head confused why their help page says with WhoisGuard there shouldn't be any ICAAN errors
5. Be shocked that all DNS records are gone!

WHOIS details not verified can lead to a ICAAN error page. So once WhoisGuard expires then yes, a verification is required.

But NameCheap ends up removing all your DNS recrod sets, and replace it with two A-records to display the error page.

Turns out you can't get your records back by pressing some buttons, apparently you can wait a few days for them to revert it...

Of course buying WhoisGuard again, and manually adding all the records back will get things working again.
