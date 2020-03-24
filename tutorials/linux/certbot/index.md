---
layout: default
title: certbot 
---

*   Something

```
sudo chmod 0700 /root/.secrets/
sudo chmod 0400 /root/.secrets/cloudflare.ini
dns_cloudflare_email = "youremail@example.com"
dns_cloudflare_api_key = "4003c330b45f4fbcab420eaf66b49c5cbcab4"
sudo apt-get install certbot python-certbot-nginx python3-certbot-dns-cloudflare

sudo certbot certonly --dns-cloudflare --dns-cloudflare-credentials /root/.secrets/cloudflare.ini -d example.com,*.example.com --preferred-challenges dns-01

sudo certbot -i nginx --dns-cloudflare --dns-cloudflare-credentials /root/.secrets/cloudflare.ini -d example.com,*.example.com --preferred-challenges dns-01

certbot renew --dry-run

sudo crontab -e
#e stands for edit
14 5 * * * /usr/bin/certbot renew --quiet --post-hook "/usr/sbin/service nginx reload" > /dev/null 2>&1
```

[back](../)
