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

```
cp ddclient /usr/sbin/
mkdir /etc/ddclient
mkdir /var/cache/ddclient
cp sample-etc_ddclient.conf /etc/ddclient/ddclient.conf
vi /etc/ddclient/ddclient.conf
-- and change hostnames, logins, and passwords appropriately

## For those using systemd:
cp sample-etc_systemd.service /etc/systemd/system/ddclient.service
## enable automatic startup when booting
systemctl enable ddclient.service
## start the first time by hand
systemctl start ddclient.service
```

[back](../)
