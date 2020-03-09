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
1. **Pre-Flash Hardware Check**
	* Local Coordinator
	* End Device
2. **Flashing Firmware**
	* Local Coordinator
	* End Device
	* XBee Modem
	* Raspberry Pi
1. **Post-Flash Hardware Check**
	* Local Coordinator
	* End Device
	* XBee Modem
	* Raspberry Pi
3. **Powering Network**
	* Local Coordinator
	* End Device

## Checking Hardware

### Local Coordinator

* #### Local Coordinator Power Board
* Use the power supply tester to make sure the LCPB is properly functioning before connecting it to the LCLB.

#### Local Coordinator Logic Board
* Check the jumpers on the LCLB to make sure it is in the desired bootmode.

### End Device
* Check the jumpers on the ED to make sure the LEDs are on.

## Flashing Firmware

### Local Coordinator

#### Local Coordinator Logic Board

##### Schedule Controller

##### LCED

#### Local Corrdinator Power Board

##### Watchdog Timer

### End Device

#### Watchdog Timer

#### MCU

### XBee Modem

#### Configure Settings

#### Flash Firmware

### Raspberry Pi

#### Flash microSD Card

#### Configure Settings

## Powering Network

### Local Coordinator


### End Device


## Glossary
LCLB
LCPB
