+++
chapter = false
title = "nginx configuration"
weight = 5
+++

# NGINX configuration

NGINX is a web server which can also be used as a reverse proxy, load balancer, mail proxy and HTTP cache.
The NGINX *alias* directive defines a replacement for the specified location.
For example, with the following configuration:
```
location /app/ {
        alias /var/www/app/;
}
```
on request of `/app/top.gif`, the file `/var/www/app/top.gif` will be sent.
But, if the location doesn't ends with directory separator (i.e. /):
```
location /app {
        alias /var/www/app/;
}
```
on request of `/app../secret/config.py`, the file `/var/www/secret/config.py` will be sent.
The incorrect configuration of the alias could allow an attacker to read file stored outside the target folder.
