---
layout: default
title: Uncomplicated Firewall 
---

# Uncomplicated Firewall (UFW)

## Initial Setup
```
sudo vim /etc/default/ufw #IPV6=no
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

## Configure SSH
*   Something
```
sudo ufw allow in from X.X.X.X/24 to any port 22
```
[back](../)
