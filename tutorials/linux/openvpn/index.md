---
layout: default
title: OpenVPN 
---

*   Something

```
# disable ipv6 to prevent leaks
sudo vim /etc/sysctl.conf
{
...
net.ipv6.conf.all.disable_ipv6=1
net.ipv6.conf.default.disable_ipv6=1
net.ipv6.conf.lo.disable_ipv6=1
}

sudo vim /etc/default/ufw
{
IPV6=no
}

sudo apt install openvpn openssl openresolv
mv openvpn.ovpn CG_XX.conf
sudo cp CG_XX.conf /etc/openvpn/
sudo cp ca.crt /etc/openvpn/
sudo cp client.crt /etc/openvpn/
sudo cp client.key /etc/openvpn/

cd /etc/openvpn
sudo vim user.txt
{
<Username>
<Password>
}

sudo nano CG_XX.conf
{
auth-user-pass /etc/openvpn/user.txt
...
up /etc/openvpn/update-resolv-conf
down /etc/openvpn/update-resolv-conf
}

sudo vim /etc/default/openvpn
AUTOSTART="CG_XX"  (the name of the file WITHOUT the file extension ‘.conf’)

head /etc/openvpn/CG_XX.conf

sudo ufw allow in to 192.168.1.0/24
sudo ufw allow out to 192.168.1.0/24
sudo ufw default deny outgoing
sudo ufw default deny incoming
sudo ufw allow out to 107.152.104.216 port 1194 proto udp
sudo ufw allow out on tun0 from any to any
sudo ufw allow in on tun0 from any to any
sudo ufw enable

sudo chmod 400 /etc/openvpn/CG_XX.conf
sudo chmod 400 /etc/openvpn/user.txt

sudo systemctl start openvpn
sudo systemctl enable openvpn
```

[back](../)
