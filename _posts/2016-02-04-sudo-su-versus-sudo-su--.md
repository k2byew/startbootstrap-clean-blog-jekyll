---
title: "sudo su versus sudo su -"
date: 2016-02-04 17:14:12
layout: post
author: "k2byew"
---
`sudo su` and `sudo su -` [mean different things](http://askubuntu.com/questions/376199/sudo-su-vs-sudo-i-vs-sudo-bin-bash-when-does-it-matter-which-is-used).

The resulting `$PATH` can be different too, so scripts relying on specific $PATH may have issues:

    [myUsername@myServer ~]$ echo $PATH
    /usr/local/bin:/bin:/usr/bin:/home/myUsername/bin
    
    [myUsername@myServer ~]$ sudo echo $PATH
    /usr/local/bin:/bin:/usr/bin:/home/myUsername/bin
    
    [myUsername@myServer ~]$ sudo su
    [root@myServer myUsername]# echo $PATH
    /usr/bin:/bin
    
    [myUsername@myServer ~]$ sudo su -
    [root@myServer ~]# echo $PATH
    /usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/root/bin
