---
layout: default
title: Samba 
---

```
sudo apt install samba samba-common-bin -y

sudo vim /etc/samba/smb.conf
[share_name]
    path = /home/pi/shared
    read only = no
    public = no
    writable = yes
    
sudo smbpasswd -a configpaul
sudo systemctl restart smbd
```

```bash
sudo chmod 0700 /root/.secrets/
sudo chmod 0400 /root/.secrets/samba.credentials
```

(in fstab)
//ip_address/share_name /media/mount_folder cifs credentials=/roots/.secrets/samba.credentials, 0 0
//<host>/<share> /mnt/<host>/<user>/<share> cifs _netdev,noauto,comment=systemd.automount,credentials=/etc/samba.<user>,uid=<user>,gid=<user>,forceuid,forcegid     0 0

(in credentials file)
username=
password=

[back](../)
