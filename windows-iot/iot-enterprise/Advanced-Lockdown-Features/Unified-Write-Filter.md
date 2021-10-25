---
title: Unified Write Filter
author: rsameser
ms.author: riameser
ms.date: 10/05/2021
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about the Unified Write Filter Features of Windows IoT Enterprise.
keywords: Lockdown, Unified Write Filter
---
# Unified Write Filter
The [Unified Write Filter (UWF)](/windows-hardware/customize/enterprise/unified-write-filter#turn-on-and-configure-uwf) is a Windows IoT Enterprise feature that helps to protect your drives by intercepting and redirecting any writes to the drive (app installations, settings changes, saved data) to a virtual overlay. The virtual overlay is a temporary location that is usually cleared during a reboot or when a guest user logs off.

This is a useful feature because it provides a clean experience for thin clients and workspaces that have frequent guests, like school, library or hotel computers. This way, guests can work, change settings, and install software, and after the device reboots, the next guest receives a clean experience. This also increases reliability for kiosks, IoT-embedded devices, or other devices where new apps are not expected to be frequently added. It can be used to help reduce wear on solid-state drives and other write-sensitive media.

## Install the Unified Write Filter
The Unified Write Filter (UWF) is an optional Windows feature. So in order to use UWF, you'll first need to install the feature.

* [Turn on UWF on a running PC](/windows-hardware/customize/enterprise/uwf-turnonuwf#turn-on-uwf-on-a-running-pc)
* [Install UWF on a customized Windows Image](/windows-hardware/customize/enterprise/uwf-turnonuwf#install-uwf-on-a-customized-windows-image)
* [Install the UWF feature by using Windows Configuration Designer](/windows-hardware/customize/enterprise/uwf-turnonuwf#install-the-uwf-feature-by-using-windows-configuration-designer)
* [Install the UWF feature by using Windows Management Instrumentation (WMI)](/windows-hardware/customize/enterprise/uwf-turnonuwf#install-the-uwf-feature-by-using-windows-management-instrumentation-wmi)

Next, you'll enable (and optionally configure) the feature.

The first time you enable UWF on your device, UWF makes the following changes to your system to improve the performance of UWF:
* Paging files are disabled.
* System restore is disabled.
* SuperFetch is disabled.
* File indexing service is turned off.
* Fast boot is disabled.
* Defragmentation service is turned off.
* BCD setting **bootstatuspolicy** is set to **ignoreallfailures**.

After UWF is enabled, you can select a drive to protect and start using UWF.

> [!TIP]
>
> You can install UWF for running PCs and devices, prepare it for customized Windows images, or manage it remotely using CSP or WMI.

## New Capabilities - 21H2
With [Windows 10 IoT Enterprise, version 21H2](/windows/iot/product-family/what's-new-in-windows-10-iot-enterprise-21h2), a new set of capabilities have been introduced to the Unified Write Filter.

1. [UWF Swapfile Created on Any Volume](/windows-hardware/customize/enterprise/uwf-wes7-ewf-to-win10-uwf)
    * Allows booting from devices suseptible to wear from writings (e.g. SSD)
    * Redirects Disk overlay to other media


2. [Read Only Mode (ROM) Mode](/windows-hardware/customize/enterprise/uwf-wes7-ewf-to-win10-uwf#read-only-media-mode)  
    * Allows elimination to physical devices
    * Official successor to WES7 Enhanced Write Filter


3. [Full Volume Commit in ROM Mode](/windows-hardware/customize/enterprise/uwf-wes7-ewf-to-win10-uwf#full-volume-commit-in-read-only-media-mode)
    * Ability to commit entire state of UWF protected volumes to physical disk at once.

## Additional Resources
* [Enable UWF](/windows-hardware/customize/enterprise/uwf-turnonuwf)
* [Unified Write Filter](/windows-hardware/customize/enterprise/unified-write-filter)
* [Unified Write Filter WMI Provider Reference](/windows-hardware/customize/enterprise/uwf-wmi-provider-reference)
* [UWF Command-line tool](/windows-hardware/customize/enterprise/uwfmgrexe)
* [Service UWF-protected devices](/windows-hardware/customize/enterprise/service-uwf-protected-devices)
