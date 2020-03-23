---
layout: default
title: ddclient 
---

*   sudo vim /etc/ddclient.conf

```
daemon=1800
protocol=cloudflare
use=web
server=www.cloudflare.com
ssl=yes
login=*cloudflare-email*
password=*cloudflare-global-api-key*
zone=*cloudflare-domain*
*full-hostname*
```

[back](../)
