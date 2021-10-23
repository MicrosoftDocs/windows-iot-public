---
title: What's new in Windows 10 IoT Enterprise, Version 21H2?
author: rsameser
ms.author: riameser
ms.date: 10/26/2021
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about what's new in Windows 10 IoT Enterprise 2021
keywords: Windows IoT Enterprise, Windows 10, Windows 10 IoT, Windows 10 IoT Enterprise, LTSC, SAC, Windows 11
---

# What's new in Windows 10 IoT Enterprise, version 21H2?

This article will walk you through the latest updates for Windows 10 IoT Enterprise 21H2 and what device builders and OEMs should know about this latest offering.


## What is Windows 10 IoT Enterprise 21H2?
Windows 10 IoT Enterprise is the latest operating system offering for embedded and IoT devices. With every new release, we continue to deliver on our promise of bringing enterprise-class power, security, and manageability to the Internet of Things in addition to adding new features and capabilities, some of which are highlighted below.

This release will be available in two editions:
* Semi-Annual Channel (SAC): [Windows 10 IoT Enterprise 21H2](/lifecycle/products/windows-10-iot-enterprise)
* Long-Term Servicing Channel (LTSC): [Windows 10 IoT Enterprise LTSC 2021](/lifecycle/products/windows-10-iot-ltsc-2021)

Please contact your [Windows IoT distributor](https://aka.ms/IoTDistributorList) for more information.


## New Features and Capabilities

### Microsoft Edge Browser Support
Windows 10 IoT Enterprise, version 21H2 comes with built-in Microsoft Edge Browser support.

### Customizable Windows Update UX
With this latest release, we are enabling you to manage your Windows update experience with genericized update message strings and screen accent colors.

### Soft Real-Time
Windows 10 soft real-time is a new feature with Windows 10 IoT Enterprise, version 21H2 that allows device makers to introduce soft real-time capabilities on their devices. Check out the following documentation to learn more: Soft-Real Time Overview, Device Configuration and Application Development.

### Unified Write Filter (UWF) Updates
With Windows 10 IoT Enterprise, version 21H2, there have been many improvements to Unified Write Filter.

1. Allowing UWF Swapfile (DISK Overlay) to be created and used on any volume
2. Read Only Media Mode
3. Full Volume Commit in Read-Only Media mode

To learn more about how to implement these new features, review [Enhanced Unified Write Filter Features](/windows-hardware/customize/enterprise/uwf-wes7-ewf-to-win10-uwf)

### Windows Subsystem for Linux (WSL)
Starting with Windows IoT Enterprise LTSC 2021, Windows Subsystem for Linux (WSL) will be available in-box. In Windows 10 IoT Enterprise, version 21H2 (SAC), WSL will be available as a store download. [Check with Terry on this one]

### GPU Compute Support
With Windows 10 IoT Enterprise, version 21H2 there is additional GPU compute support in the Windows Subsystem for Linux (WSL) and Azure IoT Edge for Linux on Windows (EFLOW) deployments for machine learning and other compute intensive workflows.

### Adding WPA3 H2E standards support

In this new release, there will be WPA3 H2E standards support for enhanced Wi-Fi security. Worry less about security when connecting devices to wireless networks—public or personal. WPA3 represents a industry standard in in Wi-Fi security.

Introduced with Windows 11, it now comes available to Windows 10 IoT Enterprise, version 21H2 to offer increased protection against web traffic spying, session hijacking attacks, and brute-force password cracking. With WPA3 H2E standars in effect, web traffic will be encrypted when connected to open networks.

**Minimum requirements**: In order for your device to take advantage of this feature, you will need a router that supports WPA3 and a wireless network adapter that supports WPA3.

To learn more, view [Faster and more secure Wi-Fi in Windows](https://support.microsoft.com/windows/faster-and-more-secure-wi-fi-in-windows-26177a28-38ed-1a8e-7eca-66f24dc63f09)


## What's the difference between Windows 10 IoT Enterprise, version 21H2 and Windows 11 IoT Enterprise?

Please review the following table to understand the differences between these operation system versions.

| Scenario | Windows 10 IoT Enterprise, Version 21H2 | Windows 11 IoT Enterprise |
|----------|-----------------------------------------|---------------------------|
| Servicing | 2 Options: SAC, 10-Year LTSC | Annual Release |
| Multi-App Assigned Access | Available | Coming soon in a future release |
| Browser Support | Microsoft Edge included in-box and supported until OS EOL | Microsoft Edge included in-box |
| Customizable Windows Update UX | X | X |
| Soft Real-Time | X | X |
| Unified Write Filter (UWF) Updates | X | X |
| Windows Subsystem for Linux (WSL) | Available in-box | Available with GUI [(WSGLg)](/windows/iot/product-family/what's-new-in-windows-11-iot-enterprise#windows-subsystem-for-linux-gui)|
| GPU Compute Support | X | X |
| WPA3 H2E Support | X | X |
| Wifi 6E | - | X |
| USB 4.0 | - | X |
| Removable Packages Feature | Available Q1 of 2022 | Will not be available |
