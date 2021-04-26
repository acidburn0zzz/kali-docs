---
title: Raspberry Pi Zero W
description:
icon:
type: post
weight:
author: ["steev",]
---

The [Raspberry Pi Zero W](https://www.raspberrypi.org/products/raspberry-pi-zero-w/) has a single core 1GHz, with 512MB of RAM. Kali Linux fits on an external microSD card.

By default, the Kali Linux Raspberry Pi Zero W image contains the **kali-linux-default** metapackage similar to other ARM images. If you wish to install extra tools please refer to our [tools site](https://tools.kali.org/kali-metapackages).

{{% notice info %}}
The Raspberry Pi images use [Re4son](https://twitter.com/re4sonkernel)'s kernel, which includes the drivers for external Wi-Fi cards, TFT displays, and the [nexmon](https://github.com/seemoo-lab/nexmon) firmware for the built-in wireless card on the Raspberry Pi 3 and 4. You will not need to download it and install it, and doing so will likely be a downgrade over the current installed kernel.
{{% /notice %}}

## Kali on Raspberry Pi Zero W - User Instructions

If you're unfamiliar with the details of [downloading and validating a Kali Linux image](/docs/introduction/download-official-kali-linux-images/), or for [using that image to create a bootable device](/docs/usb/live-usb-install-with-windows/), it's strongly recommended that you refer to the more detailed procedures described in the specific articles on those subjects.

To install a pre-built image of the standard build of Kali Linux on your Raspberry Pi Zero W, follow these instructions:

1. Get a fast microSD card with at least 16GB capacity. Class 10 cards are highly recommended.
2. Download _and validate_ the `Kali Raspberry Pi Zero/Zero W` image from the [downloads](https://www.offensive-security.com/kali-linux-arm-images/) area. The process for validating an image is described in more detail in the article on [Downloading Kali Linux](/docs/introduction/download-official-kali-linux-images/).
3. Use the **dd** utility to image this file to your microSD card (same process as [making a Kali USB](/docs/usb/live-usb-install-with-windows/).

In our example, we assume the storage device is located at **_/dev/sdb_**. Do _not_ simply copy these value, **change this to the correct drive path**.

{{% notice info %}}
This process will wipe out your SD card. If you choose the wrong storage device, you may wipe out your computers hard disk.
{{% /notice %}}

```console
$ xzcat kali-linux-$version-rpi0w-nexmon.img.xz | sudo dd of=/dev/sdb bs=4M status=progress
```

This process can take a while, depending on your PC, your microSD card's speed, and the size of the Kali Linux image.

Once the _dd_ operation is complete, boot up the Raspberry Pi Zero W with the microSD plugged in.

You should be able to [log in to Kali](/docs/introduction/default-credentials/).

## Kali on Raspberry Pi Zero W - Image Customization

If you want to customize the Kali Raspberry Pi Zero W image, including changes to the [packages](https://www.kali.org/docs/general-use/metapackages/) being installed, changing the desktop environment, increasing or decreasing the image file size or generally being adventurous, check out the [kali-arm-build-scripts](https://gitlab.com/kalilinux/build-scripts/kali-arm) repository on GitLab, and follow the _README.md_ file's instructions. The script to use is **rpi0w-nexmon.sh**