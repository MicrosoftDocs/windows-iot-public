---
title: Getting Started with Windows IoT Enterprise
author: rsameser
ms.author: riameser
ms.date: 9/8/2022
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about what Windows IoT Enterprise is and what you can do with it.
keywords: IoT Enterprise, binary, fixed purpose devices, LTSC, Silicon
---

# Getting Started with Windows IoT Enterprise
This article will give you an overview of the product and guide you through how to get started with Windows IoT Enterprise.

## What is Windows IoT Enterprise?
Windows IoT Enterprise is a full version of Windows Enterprise that delivers enterprise manageability and security to IoT solutions. Windows IoT Enterprise shares all the benefits of the worldwide Windows ecosystem. It is a binary equivalent to Windows Enterprise, so you can use the same familiar development and management tools as client PCs and laptops. However, when it comes to *licensing and distribution*, the desktop version and IoT versions differ. Today there are two releases of Windows IoT Enterprise: [Windows 10 IoT Enterprise](/windows/iot/product-family/what's-new-in-windows-10-iot-enterprise-21h2) and [Windows 11 IoT Enterprise](/windows/iot/product-family/what's-new-in-windows-11-iot-enterprise).


> [!NOTE]
>
> Windows 10 IoT Enterprise offers *both* Long Term Servicing Channel (LTSC) and General Availability Channel (GAC) options, and OEMs can choose the one they need for their devices. At this time Windows 11 IoT Enterprise is only available as an [annual release](/lifecycle/faq/windows#windows-11). For more information on how to reach out to a [Windows IoT Distributor](https://aka.ms/IoTDistributorList) or how to purchase a license, review [Licensing & Usage](./Commercialization/Licensing.md).


## Why Do Customer Choose Windows IoT Enterprise?
There are three main reasons why customers choose to develop with Windows IoT Enterprise:

1. **Productive** - Leverage existing knowledge to build and manage Windows IoT Enterprise devices with powerful tools and technologies to quickly unlock data and drive digital transformation.
2. **Trusted** - Windows IoT Enterprise helps you build IoT solutions that you can trust, keeping your devices, data, and identities secure and giving you peace of mind.
3. **Smart** - Windows IoT Enterprise helps you connect your devices to each other, your network, and the cloud, so you can use data to drive real business insight and create new business opportunities

> [!TIP]
>
> If you are building any kind of **OEM style appliance**, such as a point-of-sale or retail device, industrial automation equipment, digital signage, medical equipment or any appliance with a screen, Windows IoT Enterprise is the solution for you.
>
> See how our [customers](https://www.microsoft.com/WindowsForBusiness/windows-iot) are using Windows IoT Enterprise to accomplish their business goals.


## Documentation Overview
This documentation set will cover the technical breakdown of what's included when you choose to use Windows IoT Enterprise.


### Hardware Guidance
This section provides insight into the hardware needed to run Windows IoT Enterprise as your device's OS.

Articles include:
* [Hardware Requirements](./Hardware-Guidance/Hardware_Requirements.md)
* [Selecting SoCs and Custom Boards](./Hardware-Guidance/SoCs.md)

### Quickstarts
This section provides quick tutorials on how to get started with Windows IoT Enterprise.

Articles include:
* [How to Start Prototyping](./Hardware-Guidance/Prototype.md)  

### Kiosk Mode
This section walks users through the features and functionalities of Kiosk Mode and how to enable those features on Windows IoT Enterprise.

Articles include:
* [Kiosk Mode Overview](./Kiosk-Mode/Kiosk-Mode.md)
* [Assigned access single-app kiosk mode](./Kiosk-Mode/Single-App-Kiosk.md)
* [Assigned access multi-app kiosk mode](./Kiosk-Mode/Multi-App-Kiosk.md)
* [Configure Shell Launcher](./Kiosk-Mode/Shell-Launcher.md)
* [Browser Support](./Kiosk-Mode/Browser-Support.md)
* [Manage the Edge Swipe Policy](./Advanced-Lockdown-Features/Edge-Swipe-Policy.md)

### Advanced Lockdown Features
This section highlights how to create a lock-down environment with Windows IoT Enterprise OS features.

Articles include:
* [Application Control](./Advanced-Lockdown-Features/Application-Control.md)
* [Put in Place Device Safeguards](./Advanced-Lockdown-Features/Device-Safeguards.md)
* [Use a Keyboard Filter](./Advanced-Lockdown-Features/Keyboard-Filter.md)
* [Explore the Unified Write Filter](./Advanced-Lockdown-Features/Unified-Write-Filter.md)
* [Enable Hibernate Once, Resume Many (HORM)](./Advanced-Lockdown-Features/HORM.md)


### Branding Features
This section reviews how to create a custom user-experience that highlights your brand.
Articles include:
* [Enable Custom Logon](./Branding-Features/Custom-Logon.md)
* [Manage Microsoft Store Access](./Branding-Features/Microsoft-Store-Access.md)
* [Control Page Visibility](./Branding-Features/Page-Visibility.md)
* [Configure Layout Control](./Branding-Features/Layout-Control.md)
* [Enable Unbranded Boot](./Branding-Features/Unbranded-Boot.md)
* [Manage Update Screen UI and Notifications](./Branding-Features/Update-Notification.md)


### Device Management
Learn more about the device management solutions you can take advantage of with Windows IoT Enterprise.

Articles include:
* [Device Management Overview](./Device-Management/Device-Management-Overview.md)
* [Manage OS Updates](./OS-Features/Updates.md)
* [Manage App Updates](./Device-Management/App-Updates.md)
* [Reset & Recovery](./Device-Management/Reset-and-Recovery.md)


### IoT Device Features
This section gives an overview of many of the built-in functionalities of Windows IoT Enterprise devices.

Articles include:
* [Windows IoT Security](./OS-Features/Security.md)
* [Enable Embedded Mode](./OS-Features/Embedded-Mode.md)
* [Configure Device Drivers](./OS-Features/Device-Drivers.md)
* [Bus Providers](./OS-Features/Bus-Providers.md)
* [Manage Network Service Controls](./OS-Features/Network-Controls.md)
* [Enable On-Screen Keyboard](./OS-Features/On-Screen-Keyboard.md)
* [Privacy Features](./OS-Features/Privacy.md)
* [Accessibility Features](./OS-Features/Accessibility.md)

### Device Optimization
This section provides insight into how OEMs can optimize their devices for manufacturing and production.

Articles include:
* [Guidelines for Device Optimization](./optimize-your-device/overview.md)
* [Reduce Disk Footprint](./optimize-your-device/Reduce-Disk-Footprint.md)
* [Services Guide](./optimize-your-device/services.md)


### Commercialization
Learn how to commercialize your Windows IoT Enterprise devices.

Articles include:
* [Explore Licensing Options](./Commercialization/Licensing.md)
* [Windows IoT Enterprise Manufacturing Guide](./Commercialization/Manufacturing-Guide.md)


### Soft Real-Time
Learn how to use Soft Real-Time capabilities with your Windows IoT Enterprise devices.

* [Overview](/windows/iot/iot-enterprise/soft-real-time/soft-real-time)
* [Device Configuration](/windows/iot/iot-enterprise/soft-real-time/soft-real-time-device)
* [Application Development](/windows/iot/iot-enterprise/soft-real-time/soft-real-time-application)


### Additional Resources
These resources provide additional information and support to our customers and partners.

Articles include:
* [Azure IoT Edge for Linux on Windows](./Azure-IoT-Edge-For-Linux-On-Windows.md)
* [Downloads](./Downloads.md)
* [Features by Release](./Features.md)
* [Frequently Asked Questions](./FAQ.md)
* [Contact Us](./Contact-Us.md)
