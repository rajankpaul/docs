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
*   Remount the microSD card and add a file named **ssh** to the boot partition 

## Initial Setup
*   Insert the flashed microSD card into the rpi, and power it on
*   Look for the rpi's IP Address using a tool like Wireless Network Watcher on Winows or arp-scan on cli
*   ssh into the pi using default username=pi, password=raspberry
*   immediately run 'passwd' command to change default password to something more secure
*   run the following commands:
```bash
sudo apt update
sudo apt dist-upgrade -y
sudo apt autoremove
```

## New User
*   Something

## Extra Security
*   Something

## Blahblah
*   Something

[back](../)
