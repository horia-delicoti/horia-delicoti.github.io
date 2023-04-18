---
title: "Increase Swap on a Raspberry Pi"
date: 2023-04-15T12:08:00+03:00
draft: false

tags: [raspberry-pi]
categories: []
ontawesome: true
linkToMarkdown: true
rssFullText: false
---

## Introduction

The swap file is used to increase the system’s total accessible memory beyond its hardware capabilities.

This means that when all of the Raspberry Pi’s RAM is exhausted, it can start using the swap file as memory instead.

The addition of more virtual memory allows the system to deal with more memory intensive tasks without running into out of memory errors or having to shut down other additional packages.

However, the downside to this is that accessing the swap file is a significantly slower process that can create slowdowns.

The reason for this is that the swap file exists on your actual disk, which has significantly lower read and write speeds then your RAM.

Another caveat of a large swap file is that you need that space to be free on your SD Card. You can’t set a swap file on your Raspberry Pi larger than your available free space.

### You will need

* A Raspberry-Pi setup ([starter kit][rpi_starter_kit] is a great way to start)
* A [Micro SD Card][sd_card]
* Ethernet cable or Wi-Fi
* [Power Supply][power]

### Increase the Swap File on a Raspberry Pi

Before we can increase our Raspberry Pi’s swap file, we must first temporarily stop it.
The swap file cannot be in use while we increase it.
To stop the operating system from using the current swap file, run the following command.

```sh
sudo dphys-swapfile swapoff
```

Next, we need to modify the swap file configuration file.

```sh
sudo vim /etc/dphys-swapfile
```

Within this config file, find the following line of text.

```sh
CONF_SWAPSIZE=100
```

To increase or decrease the swap file, all you need to do is modify the numerical value you find here.
This number is the size of the swap in megabytes.

```sh
CONF_SWAPSIZE=1024
```

Whatever size you set, you must have that space available on your SD card.
We can now re-initialize the Raspberry Pi’s swap file by running the command below.

```sh
sudo dphys-swapfile setup
```

With the swap now recreated to the newly defined size, we can now turn the swap back on.

```sh
sudo dphys-swapfile swapon
```

To reload all programs with access to the new memory pool, then restart your device.

```sh
sudo reboot
```

## References

* [Raspberry Pi Swap File][rpi_swap_file]

[rpi_starter_kit]: https://thepihut.com/products/raspberry-pi-starter-kit
[sd_card]: https://www.tomshardware.com/best-picks/raspberry-pi-microsd-cards
[power]: https://thepihut.com/blogs/raspberry-pi-tutorials/how-do-i-power-my-raspberry-pi
[rpi_swap_file]: https://pimylifeup.com/raspberry-pi-swap-file/
