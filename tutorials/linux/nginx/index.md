---
layout: default
title: NGINX 
---

# NGINX

> pronounced "engine-x"
> A light-weight webserver/reverse-proxy

## Installation

```
sudo apt-get install nginx -y 
```

## Setup
*   Generate DH params
```
sudo openssl dhparam -out /etc/ssl/certs/dhparam.pem 2048
```

*   Create new configuration file and link it to _sites-enabled_
```
sudo ln -s /etc/nginx/sites-available/example.com.conf /etc/nginx/sites-enabled/
```

### Example Configuration File

```
# Redirect HTTP requests to HTTPS 
server {
    listen 80;
    server_name  example.com;
    return 301 https://$host$request_uri;
}
  
# For ssl
server {
    ssl on;
    ssl_certificate /etc/letsencrypt/live/example.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/example.com/privkey.pem;
    ssl_protocols TLSv1 TLSv1.1 TLSv1.2 TLSv1.3;
    ssl_prefer_server_ciphers on;
    ssl_dhparam /etc/ssl/certs/dhparam.pem;
    ssl_ciphers 'ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:DHE-DSS-AES128-GCM-SHA256:kEDH+AESGCM:ECDHE-RSA-AES128-SHA256:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES128-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES256-SHA:ECDHE-ECDSA-AES256-SHA:DHE-RSA-AES128-SHA256:DHE-RSA-AES128-SHA:DHE-DSS-AES128-SHA256:DHE-RSA-AES256-SHA256:DHE-DSS-AES256-SHA:DHE-RSA-AES256-SHA:AES128-GCM-SHA256:AES256-GCM-SHA384:AES128-SHA256:AES256-SHA256:AES128-SHA:AES256-SHA:AES:CAMELLIA:DES-CBC3-SHA:!aNULL:!eNULL:!EXPORT:!DES:!RC4:!MD5:!PSK:!aECDH:!EDH-DSS-DES-CBC3-SHA:!EDH-RSA-DES-CBC3-SHA:!KRB5-DES-CBC3-SHA';
    ssl_session_timeout 1d;
    ssl_session_cache shared:SSL:50m;
    ssl_stapling on;
    ssl_stapling_verify on;
    add_header Strict-Transport-Security max-age=15768000;
      
    default_type  application/octet-stream;
      
    listen 443;
    server_name  example.com;
  
    root /var/www/example.com;
  
    location ~ /.well-known {
        allow all;
    }
  
    location / {
        include proxy_params;
        proxy_pass http://192.168.0.X;
    }
}
```

```
sudo ln -s /etc/nginx/sites-available/example.conf /etc/nginx/sites-enabled/
```
[back](../)
