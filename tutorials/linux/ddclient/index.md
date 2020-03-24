---
layout: default
title: ddclient 
---

*   sudo apt install libdata-validate-ip-perl libjson-any-perl sendmail
*   sudo vim /etc/ddclient.conf

```
daemon=1800
pid=/var/run/ddclient.pid
protocol=cloudflare
use=web, web=checkip.dyndns.com
server=api.cloudflare.com/client/v4
ssl=yes
login=*cloudflare-email*
password=*cloudflare-global-api-key*
zone=*cloudflare-domain*
*full-hostname*
```

*   sudo ddclient -daemon=0 -debug -verbose -noquiet

[back](../)
