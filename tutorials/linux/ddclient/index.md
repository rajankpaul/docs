---
layout: default
title: ddclient 
---

*   sudo vim /etc/ddclient.conf

```
daemon=1800
pid=/var/run/ddclient.pid
protocol=cloudflare
use=web
server=api.cloudflare.com/client/v4
ssl=yes
login=*cloudflare-email*
password=*cloudflare-global-api-key*
zone=*cloudflare-domain*
*full-hostname*
```

[back](../)
