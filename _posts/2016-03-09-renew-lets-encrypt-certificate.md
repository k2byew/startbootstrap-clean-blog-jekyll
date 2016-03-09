---
title: "Renew Let's Encrypt Certificate"
date: 2016-03-09 20:16:13
layout: post
author: "k2byew"
---
Cheatsheet to renew Let's Encrypt certificate using [letsencrypt-nosudo](https://github.com/diafygi/letsencrypt-nosudo) and load it into nginx.

As root, in the directory where your Let's Encrypt `user.pub` resides:
    
    # Get new certificate for "mydomain.net"
    openssl genrsa 4096 > domain.key
    openssl req -new -sha256 -key domain.key -subj "/" -reqexts SAN -config <(cat /etc/ssl/openssl.cnf <(printf "[SAN]\nsubjectAltName=DNS:mydomain.net,DNS:www.mydomain.net")) > domain.csr
    wget https://raw.githubusercontent.com/diafygi/letsencrypt-nosudo/master/sign_csr.py
    python sign_csr.py --public-key user.pub domain.csr > signed.crt
    
    # Create chained certificate for nginx
    wget https://letsencrypt.org/certs/lets-encrypt-x1-cross-signed.pem
    cat signed.crt lets-encrypt-x1-cross-signed.pem > chained.pem
    
    # Archive old certificates
    mkdir /etc/nginx/ssl/expired-$(date -I)
    mv /etc/nginx/ssl/chained.pem /etc/nginx/ssl/expired-$(date -I)/
    mv /etc/nginx/ssl/domain.key /etc/nginx/ssl/expired-$(date -I)/

    # Copy certificate to nginx directory
    cp chained.pem /etc/nginx/ssl/
    cp domain.key /etc/nginx/ssl/
    
    # Cleanup and archive
    mkdir created-$(date -I)
    mv domain.key created-$(date -I)/
    mv domain.csr created-$(date -I)/
    mv signed.crt created-$(date -I)/
    mv chained.pem created-$(date -I)/
    
    # Restart nginx to load new certificates
    /etc/init.d/nginx restart
