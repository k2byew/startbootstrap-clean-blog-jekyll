---
title: "Let's Encrypt, Let's Try and Encrypt"
date: 2015-12-04 21:54:34
layout: post
author: "k2byew"
---
[Let’s Encrypt](https://letsencrypt.org) is now in public beta so time to give it go!

1. Tried IP only, but got the error: `Issuance for IP addresses not supported`. This matches what was mentionend in the [forum](https://community.letsencrypt.org/t/certificate-for-static-ip/84).
2. Ran `./letsencrypt-auto`, got `InsecurePlatform` warning since python was tool old (<2.7.9). Check python version with `python -V`. Turns out there were notes about this [here](https://github.com/kennwhite/install-letsencrypt#urllib3).
3. Was trying to do this on Wheezy, and looks like it's not as trivial as it should be. Some helper scripts [here](https://github.com/kennwhite/install-letsencrypt).
4. `letsencrypt-auto` kept stopping and showing `Killed`. Use `bash +x letsencrypt-auto` to troubleshoot. Turns out no RAM left when doing certain pip installs since this was being tested on a very tiny server.
5. [letsencrypt-nosudo](https://github.com/diafygi/letsencrypt-nosudo) was a quick and light solution! Also won't install things automatically like `letsencrypt-auto` does.
6. Used a dynamic domain from [FreeDNS](http://freedns.afraid.org), and wanted both the www and non-www url to have certificates.
7. The script wanted to reach the python server via the `www` URL which doesn't work due to how the DNS was setup.
8. Just generate the certificate for the non-www domain, but resulted in the error: `{"type":"urn:acme:error:rateLimited","detail":"Error creating new cert :: Too many certificates already issued for: [freedns domain]","status":429}
`
9. ...time to find another way to try this out without spending money.
