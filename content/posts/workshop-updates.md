---
title: "Workshop Updates After Maker Faire 2019"
date: 2019-05-21
tags: ["workshop", "software", "hardware"]
summary: "The Maker Faire workshop went well — all robots went home able to dispense liquids. Here are some configuration fixes and improvements."
---

The Maker Faire workshop was a lot of fun, and many lessons were learned!

On the plus side, I think that all of the robots went home able to dispense liquids. Yay!

I am working on some tweaks, improvements, patches, and bug fixes. I will be uploading a new SD card image, and instructions to write it to your SD card. Or I can send you a new SD card — email me at Rich.Gibson at gmail.com if you would like to swap out your SD card.

## Configuration Fixes

The initial "big changes" to get the Bartendro admin mode to work is to change your `/etc/hosts` file:

```
127.0.0.1    localhost
::1          localhost ip6-localhost ip6-loopback
ff02::1      ip6-allnodes
ff02::2      ip6-allrouters
127.0.0.1    hellodrinkbot
```

And update `/etc/nginx/sites-available/bartendro.conf`:

```nginx
upstream hellodrinkbot {
    server 127.0.0.1:8080;
}

# Listen on all interfaces of eth0
server {
    root        /usr/share/nginx/www;
    server_name hellodrinkbot;
    access_log  /var/log/nginx/bartendro-combined.log combined;
    error_log   /var/log/nginx/bartendro-error.log notice;

    location / {
        proxy_pass http://hellodrinkbot;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        # For first-time setup via IP address:
        proxy_set_header Host $server_addr;
        # If you have custom DNS, use this instead:
        # proxy_set_header Host "bartendro.example.com";
        proxy_redirect off;
    }
}

# Listen on the Bartendro private wifi and redirect all traffic
server {
    listen      10.0.0.1:80;
    root        /usr/share/nginx/www;
    server_name hellodrinkbot;
    access_log  /var/log/nginx/bartendro-combined.log combined;
    error_log   /var/log/nginx/bartendro-error.log notice;
    error_page  404             /404.html;
    error_page  500 502 503 504 /50x.html;

    location / {
        proxy_pass http://hellodrinkbot;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header Host "hellodrinkbot";
        proxy_redirect off;
    }
}

server {
    listen 10.0.0.1:80 default_server;
    server_name _;
    rewrite ^ http://hellodrinkbot? redirect;
}
```

This is a bit of a kludge — I am tweaking a sample conf file and I'm pretty sure there are better ways to do this. Please let me know if you have a better version!
