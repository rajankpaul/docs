---
layout: default
title: transmission
---

*   Something

```
sudo apt install transmission-daemon
sudo systemctl stop transmission-daemon
sudo mkdir -p /home/ubuntu/torrent-inprogress
sudo mkdir -p /home/ubuntu/torrent-complete
sudo chown -R ubuntu:ubuntu /home/ubuntu/torrent-inprogress
sudo chown -R ubuntu:ubuntu /home/ubuntu/torrent-complete
sudo vim /etc/transmission-daemon/settings.json
{
"incomplete-dir": "/home/ubuntu/torrent-inprogress",
"download-dir": "/home/ubuntu/torrent-complete",
"incomplete-dir-enabled": true,
"rpc-password": "Your_Password",
"rpc-username": "Your_Username",
"rpc-whitelist": "192.168.*.*",
}

sudo vim /etc/init.d/transmission-daemon
USER=ubuntu
sudo vim /etc/systemd/system/multi-user.target.wants/transmission-daemon.service
user=ubuntu
sudo systemctl daemon-reload
sudo chown -R ubuntu:ubuntu /etc/transmission-daemon

sudo mkdir -p /home/ubuntu/.config/transmission-daemon/
sudo ln -s /etc/transmission-daemon/settings.json /home/ubuntu/.config/transmission-daemon/
sudo chown -R ubuntu:ubuntu /home/ubuntu/.config/transmission-daemon/
sudo systemctl start transmission-daemon
```

[back](../)
