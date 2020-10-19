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
sudo mkdir /var/www/example.com
sudo chown www-data:www-data /var/www/example.com
```

## Setup
*   Generate DH params
```
sudo openssl dhparam -out /etc/ssl/certs/dhparam.pem 2048
```

*   Create new configuration file and link it to _sites-enabled_
```
sudo ln -s /etc/nginx/sites-available/example.conf /etc/nginx/sites-enabled/
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
    listen 443 ssl http2;
    server_name  example.com;

    ssl_certificate /etc/letsencrypt/live/example.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/example.com/privkey.pem;
    ssl_session_timeout 1d;
    ssl_session_cache shared:SSL:10m; # about 40000 sessions
    ssl_session_tickets off;
    
    # path/to/dhparam
    ssl_dhparam /etc/ssl/certs/dhparam.pem;
    
    # intermediate configuration
    ssl_protocols TLSv1.2 TLSv1.3;;
    ssl_ciphers ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:DHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384;
    ssl_prefer_server_ciphers off;
    
    # HSTS (ngx_http_headers_module is required) (63072000 seconds)
    add_header Strict-Transport-Security "max-age=63072000" always;
    
    # OCSP stapling
    ssl_stapling on;
    ssl_stapling_verify on;
    
    # verify chain of trust of OCSP response using Root CA and Intermediate certs
    # ssl_trusted_certificate /path/to/root_CA_cert_plus_intermediates;

    # replace with the IP address of your resolver
    # resolver 127.0.0.1;
      
    default_type  text/html;
  
    root /var/www/example.com;

    location / {
        include proxy_params;
        proxy_pass http://X.X.X.X;
    }
}
```
[back](../)
