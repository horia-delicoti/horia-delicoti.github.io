---
title: "How to install an OS on an SSD with the Raspberry Pi Imager"
date: 2023-04-07T12:08:00+03:00
draft: false

tags: [raspberry-pi]
categories: []
ontawesome: true
linkToMarkdown: true
rssFullText: false
---

## Introduction

I'll walk you through setting up your Raspberry Pi 4 to boot from an USB connected SSD. We'll start by flashing the SD card, then copy the card to the drive, move on to setting up the Pi and finish off by removing the SD card and allowing the Pi to boot from the SSD.

### You will need

* A Raspberry-Pi setup ([starter kit][rpi_starter_kit] is a great way to start)
* A [2.5" SSD][2_5_ssd] (SATA connection)
* A [USB to SATA Cable][sata_to_usb]

### Install Rasbperry Pi OS

* Install Raspberry Pi OS using [Raspberry Pi Imager][rpi_software]
* Enable SSH

## Getting started

Copy SSH key:

```sh
ssh-copy-id -i ~/.ssh/mykey user@host
```

Once you have Raspberry Pi OS installed you'll want to make sure it's all up to date

```sh
sudo apt-get update
sudo apt full-upgrade
sudo rpi-update
sudo reboot
```

Once you got back to your RPI Desktop:

* plug in your SSD
* Copy the content of SD card to SSD by using SD Card Copier

Make sure you have the latest bootloder by running

```sh
sudo rpi-eeprom-update -d -a
```

Configure bootloader to boot from USB

```sh
sudo raspi-config
```

Select:

* Advanced Option -> Bootloder version -> Select first option -> Select No to reset boot ROM to defaults
* Advanced Option -> Boot Order -> Select USB Boot
* System Options -> Boot / Auto Login -> Console

Shutdown your Raspberry Pi, remove the SD Card and boot your device

## Card speed test using the dd command

To find out the SD card write speed performance, we are creating 100MB of free storage space and five blocks of 20MB each

```sh
dd if=/dev/zero of=./speedTestFile bs=20M count=5 oflag=direct
```

To find out the read speed information of your SD card, issue the following command in the terminal:

```sh
dd if=./speedTestFile of=/dev/zero bs=20M count=5 oflag=dsync
```

## References

* [How To Boot A Raspberry Pi 4 From An SSD][boot_rpi4_youtube]
* [How to Test Speed of Raspberry Pi SD Card][card_speed_test]
* [How to Disable Desktop GUI on Raspberry Pi][disable_gui]

[rpi_starter_kit]: https://thepihut.com/products/raspberry-pi-starter-kit
[2_5_ssd]: https://thepihut.com/products/wd-green-240gb-2-5-ssd
[sata_to_usb]: https://thepihut.com/products/ssd-to-usb-3-0-cable-for-raspberry-pi
[rpi_software]: https://www.raspberrypi.com/software/
[boot_rpi4_youtube]: https://www.youtube.com/watch?v=a8nzkLryGmM
[card_speed_test]: https://linuxhint.com/raspberry-pi-sd-card-speed-test/
[disable_gui]: https://linuxhint.com/disable-gui-raspberry-pi/
