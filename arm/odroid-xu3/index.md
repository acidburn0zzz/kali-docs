---
title: ODROID-XU3
description:
icon:
type: post
weight:
author: ["steev",]
---

The [ODROID-XU3](https://www.hardkernel.com/main/products/prdt_info.php?g_code=g140448267127) is an octacore development board. Boasting 4 A15 cores and 4 A7 cores and 4GB of RAM, the ODROID-XU3 is a fast ARM device. Kali Linux fits on an external microSD card or on an eMMC module.

By default, the Kali Linux ODROID-XU3 image contains the **kali-linux-default** metapackage similar to other ARM images. If you wish to install extra tools please refer to our [tools site](https://tools.kali.org/kali-metapackages).

## Kali on the ODROID-XU3 microSD card - User Instructions

If you're unfamiliar with the details of [downloading and validating a Kali Linux image](/docs/introduction/download-official-kali-linux-images/), or for [using that image to create a bootable device](/docs/usb/live-usb-install-with-windows/), it's strongly recommended that you refer to the more detailed procedures described in the specific articles on those subjects.

To install a pre-built image of the standard build of Kali Linux on your ODROID-XU3, follow these instructions:

1. Get a fast microSD or eMMC card with at least 16GB capacity. Class 10 cards are highly recommended.
2. Download _and validate_ the `Kali ODROID-XU3` image from the [downloads](https://www.offensive-security.com/kali-linux-arm-images/) area. The process for validating an image is described in more detail in the article on [Downloading Kali Linux](/docs/introduction/download-official-kali-linux-images/).
3. Use the **dd** utility to image this file to your microSD card (same process as [making a Kali USB](/docs/usb/live-usb-install-with-windows/).

In our example, we assume the storage device is located at **_/dev/sdb_**. Do _not_ simply copy these value, **change this to the correct drive path**.

{{% notice info %}}
This process will wipe out your SD card. If you choose the wrong storage device, you may wipe out your computers hard disk.
{{% /notice %}}

```console
$ xzcat kali-linux-$version-odroidxu3.img.xz | sudo dd of=/dev/sdb bs=4M status=progress
```

This process can take a while, depending on your PC, your microSD/eMMC card's speed, and the size of the Kali Linux image.

Once the _dd_ operation is complete, boot up the ODROID-XU3 with the microSD/eMMC plugged in.

You should be able to [log in to Kali](/docs/introduction/default-credentials/).

## Kali on the ODROID-XU3 eMMC - User Instructions

If you want to install Kali on your ODROID-XU3's eMMC, there are 2 different ways to do so.

If you have the [USB Adapter for eMMC Module](https://pine64.com/product/usb-adapter-for-emmc-module/?v=0446c16e2e66) then you can simply follow the same steps as you would for the microSD card.

If you do not have the USB Adapter for eMMC Module, you can use a bootable microSD card to write the Kali image to eMMC. The instructions are similar to the microSD card, and as with above, we need to make sure that we have the correct device. The easiest way to tell which device you want to use, is look in /dev at the `mmcblkX` devices. The device that has a `boot0` and `boot1` is the eMMC. For example, if `/dev/mmcblk1boot0` exists it would mean that we want to use `/dev/mmcblk1` as our device. One important difference is that we **do** need to include the number of the device, unlike above when using `sdb`.

{{% notice info %}}
This process will wipe out your eMMC. If you choose the wrong storage device, you may wipe out your microSD card.
{{% /notice %}}

```console
$ xzcat kali-linux-$version-odroidxu3.img.xz | sudo dd of=/dev/mmcblk1 bs=4M status=progress
```

This process can take a while, depending on your PC, your microSD/eMMC card's speed, and the size of the Kali Linux image.

Once the _dd_ operation is complete, boot up the ODROID-XU3 with the microSD/eMMC plugged in.

You should be able to [log in to Kali](/docs/introduction/default-credentials/).

## Kali on ODROID-XU3 - Image Customization

If you want to customize the Kali ODROID-XU3 image, including changes to the [packages](https://www.kali.org/docs/general-use/metapackages/) being installed, changing the desktop environment, increasing or decreasing the image file size or generally being adventurous, check out the [kali-arm-build-scripts](https://gitlab.com/kalilinux/build-scripts/kali-arm) repository on GitLab, and follow the _README.md_ file's instructions. The script to use is **odroid-xu3.sh**