---
layout: post
title: Building a Raspberry Pi Typewriter (Part 1)
data: 2020-12-25 11:20:00
author: Patrick R. Callahan
image:
---

## Core Parts

1. Pi Zero WH
2. Micro SD card 32gb


### Optional

1. Bluetooth Keyboard (Separate battery supply saves power for pi)
2. Mouse during installation

## Steps

1. Flash Raspberry Pi OS Lite to SD card
2. Physical Set Up for Prototype:

a. pi zero w/ flashed SD card
b. micro HDMI in pi zero
c. HDMI in micro HDMI converter
d. micro USB to USB converter
e. Keyboard
f. power (via micro USB)

3. Log on
a. user: pi
b. password: raspberry

(If necessary at this point: Configure display: "sudo raspi-config" and reboot--log in again)

4. Localisation Options

5. Configure SSID (https://www.raspberrypi.org/documentation/configuration/wireless/wireless-cli.md)

6. reboot

7. sudo apt install flatpak
7a. https://flatpak.org/setup/Raspberry%20Pi%20OS/
8. sudo reboot
9. flatpak install flathub org.gottcode.FocusWriter (https://flathub.org/apps/details/org.gottcode.FocusWriter)

Download FocusWriter

## Hot Keys
