---
layout: default
title: Samba 
---

```
sudo apt install samba samba-common-bin -y
```

```bash
sudo chmod 0700 /root/.secrets/
sudo chmod 0400 /root/.secrets/samba.credentials
```

(in fstab)
//ip_address/share_name /media/mount_folder cifs credentials=/roots/.secrets/samba.credentials, 0 0

(in credentials file)
username=
password=

[back](../)
