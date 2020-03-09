---
layout: default
title: SoilSCAPE Setup
---

# SoilSCAPE Network Setup Instructions
*author: Rajan K Paul*

## Introduction
> These instructions are for setting up a network in the lab as I have not yet had a chance to setup a soilscape network in the field.
> Instructions should be the same, just swapping the 12V power supply for a 12V lead acid car-battery. Written for LCv4 and RippleV3.

## Overview
1. **Hardware Check**
	* Local Coordinator
	* End Device
2. **Flashing Firmware**
	* Local Coordinator
	* End Device
	* XBee Modem
	* Raspberry Pi
3. **Powering Network**
	* Local Coordinator
	* End Device

## Hardware Check

### Local Coordinator

#### Local Coordinator Power Board
* Use the power supply tester to make sure the LCPB is properly functioning before connecting it to the LCLB.

#### Local Coordinator Logic Board
* Check the jumpers on the LCLB to make sure it is in the desired bootmode.

### End Device
* Check the jumpers on the ED to make sure the LEDs are on.

## Flashing Firmware

### Local Coordinator
* Using Atmel Studio software
* write firmware from file -> program
* compare firmware with file -> verify
* save firmware to file -> read

#### Local Coordinator Logic Board
* Programming the Atmel1280 requires that the power supply is connected

##### Schedule Controller
* Connect header to C16
* Select device "Atmel1280" -> Read Signature
* Set FUSES -> OxFF (Extended); OxDA (High); OxFF(Low)

##### LCED
* Connect header to C19
* Select device "Atmel1280" -> Read Signature
* Set FUSES -> OxFD (Extended); OxDA (High); OxFF(Low)

#### Local Coordinator Power Board
* Use programming board with AA batteries

##### Watchdog Timer
* Select device "ATtiny85" -> Read Signature
* Set FUSES -> OxFF (Extended); OxDF (High); Ox62(Low)

### End Device

#### Watchdog Timer
* Use programming board with AA batteries
* Select device "ATtiny85" -> Read Signature
* Set FUSES -> OxFF (Extended); OxDF (High); Ox62(Low)

#### MCU
* Programming the Atmel1280 requires that the battery is connected
* Connect header to 
* Select device "Atmel1280" -> Read Signature
* Set FUSES -> OxFF (Extended); OxDA (High); OxFF(Low)

### XBee Modem

#### Configure Settings
* Using Digi XCTU software
* Add -> usb serial (defaults) -> finish
* Downgrade firmware to 3009
* Click here to download legacy)
* Uncheck force module
* for LC change the channel
* for ED change the channel and EDID(My Source Address)
* Profile -> Apply -> .xml file

### Raspberry Pi

#### Flash microSD Card
* Use win32disk imager to flash .img file onto the microSD card

#### Configure Settings
* Use extFS if on lab computer, else mount ext4 partition using linux OS
* files can be found in /home/pi/LC4/
* Change 10-digit ID number in /config/lc_id.txt
* if using wifi dongle instead of modem run followeing command:
```console
pi@LC4:~$ sudo systemctl restart wpa_supplicant.service
```

## Powering Network
* before powering the hardware, make sure everything is connected in the proper orientation

### Local Coordinator
* connect XBee modem to LCLB and connect antenna to modem
* connect raspberry pi to bottom connector on LCLB
* connect ribbon cable between LCLB and LCPB
* connect 12V power supply or battery to LCPB CN4 using 2EDGK connector

### End Device
* connect batteries, taking care to make sure positive is on the outside and negative is on the inside

## Glossary
LCLB - Local Coordinator Logic Board  
LCPB - Local Coordinator Power Board
