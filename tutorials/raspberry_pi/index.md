---
layout: default
title: Raspberry Pi
---

# Raspberry Pi

> The OG SBC.
> 
> I honestly think everyone should own one.

## Preparation
*   Use Win32DiskImager or Raspberry Pi Imager to flash your desired Raspbian image onto a microSD card
*   Remount the microSD card and add an empty file named *ssh* to the boot partition
*   If using wifi, add the following *wpa_supplicant.conf* file to the boot partition:

```
country=us
update_config=1
ctrl_interface=/var/run/wpa_supplicant

network={
 scan_ssid=1
 ssid="MyNetworkSSID"
 psk="Pa55w0rd1234"
}
```

## Initial Setup
*   Insert the flashed microSD card into the rpi, and power it on
*   Look for the rpi's IP Address using a tool like Wireless Network Watcher on Windows or *arp-scan* on cli
*   ssh into the pi using default username=pi, password=raspberry
*   immediately run *passwd* command to change default password to something more secure
*   run the following commands:
```bash
sudo apt update
sudo apt dist-upgrade -y
sudo apt autoremove
```

## New User
*   In order to creater a new user, run the following command and replace *&lt;username&gt;* with your actual desired username. It will ask you to enter a new password:
```bash
sudo adduser --gecos "" <username>
```
*   Run the following command to add your new user to the same groups as pi, except for the pi group. You must once again replace *&lt;username&gt;* with your desired username:
```bash
for GROUP in adm dialout cdrom sudo audio video plugdev games users input netdev spi i2c gpio; do sudo adduser <username> $GROUP; done
```
*   Use the following commands to switch to your new user and disable logging in directly to the pi user:
```bash
sudo su <username>
sudo passwd --lock pi
```

## Extra Security
*   Something

## Blahblah
*   Something

[back](../)
