---
title: BeagleBone Black
description:
icon:
type: post
weight:
author: ["steev",]
---

The [BeagleBone Black](http://beagleboard.org/BLACK) is a low-cost, community-supported ARM-based development platform aimed at developers and hobbyists. The BeagleBone Black runs a 1GHz Cortex-A8 CPU and includes hardware-based floating point and 3D acceleration; while much lower-powered than a desktop or laptop system, its affordability makes it an excellent option for a tiny Linux system.

The BeagleBone Black provides a microSD card slot for mass storage and if that device is bootable, will use it in preference to the board's "burned-in" Angstrom or Debian operating system.

By default, the Kali Linux BeagleBone Black image contains the **kali-linux-default** metapackage similar to other ARM images. If you wish to install extra tools please refer to our [tools site](https://tools.kali.org/kali-metapackages).

## Kali Linux on BeagleBone Black - Pre-built Version

If you're unfamiliar with the details of [downloading and validating a Kali Linux image](/docs/introduction/download-official-kali-linux-images/), or for [using that image to create a bootable device](/docs/usb/live-usb-install-with-windows/), it's strongly recommended that you refer to the more detailed procedures described in the specific articles on those subjects.

To install a pre-built image of the standard build of Kali Linux on your BeagleBone Black, follow these instructions:

1. Get a fast microSD card with at least 16GB capacity. Class 10 cards are highly recommended.
2. Download _and validate_ the `Kali Linux BeagleBone Black` image from the [downloads](https://www.offensive-security.com/kali-linux-arm-images/) area. The process for validating an image is described in more detail in the article on [Downloading Kali Linux](/docs/introduction/download-official-kali-linux-images/).
3. Use the **dd** utility to image this file to your microSD card (same process as [making a Kali USB](/docs/usb/live-usb-install-with-windows/).

In our example, we assume the storage device is located at **_/dev/sdb_**. Do _not_ simply copy these value, **change this to the correct drive path**.

{{% notice info %}}
This command will wipe out any existing data on your microSD card. If you specify the _wrong device path_, you could wipe out your computer's hard disk!
{{% /notice %}}

```console
$ xzcat kali-linux-$version-bbb.img.xz | sudo dd of=/dev/sdb bs=4M status=progress
```

This process can take a while, depending on your PC, your microSD card's speed, and the size of the Kali Linux image.

Once the _dd_ operation is complete, insert the microSD card into the BeagleBone Black and power it on.

You should be able to [log in to Kali](/docs/introduction/default-credentials/).

## Kali Linux on BeagleBone Black - Image Customization

If you want to customize the Kali BeagleBone Black image, including changes to the [packages](https://www.kali.org/docs/general-use/metapackages/) being installed, changing the desktop environment, increasing or decreasing the image file size or generally being adventurous, check out the [kali-arm-build-scripts](https://gitlab.com/kalilinux/build-scripts/kali-arm) repository on GitLab, and follow the _README.md_ file's instructions. The script to use is **bbb.sh**