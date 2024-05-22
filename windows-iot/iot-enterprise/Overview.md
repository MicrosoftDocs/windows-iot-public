---
title: What is Windows IoT Enterprise?
author: TerryWarwick
ms.author: twarwick
ms.date: 05/22/2024
ms.topic: overview
ms.service: windows-iot
ms.subservice: iot
description: Windows IoT Enterprise is a full version of Windows Enterprise. Is intended for fixed purpose devices and provides a 10-year support lifecycle.
keywords: IoT Enterprise, binary, fixed purpose devices, LTSC, Silicon
#customer intent: I want to understand what Windows IoT Enterprise is and its benefits for building fixed purpose devices.
---

# What is Windows IoT Enterprise?

Windows IoT Enterprise is a full version of Windows Enterprise that delivers enterprise manageability and security to IoT solutions. Windows IoT Enterprise shares all the benefits of the worldwide Windows ecosystem. It is a binary equivalent to Windows Enterprise, so you can use the same familiar development and management tools as client PCs and laptops. 

However, when it comes to *licensing and distribution*, the desktop version and IoT versions differ as the Windows IoT Enterprise product line is intended for *fixed purpose devices*. Windows IoT Enterprise offers both *General Availability Channel (GAC)* and *Long-Term Servicing Channel (LTSC)* options, LTSC provides a *10-year support lifecycle* for fixed purpose devices where changes in functionality aren't desirable.

- **Fixed Purpose Devices** - Windows is well known as the operating system for laptops and desktops that have been used by consumers and businesses worldwide for decades. Windows also powers many ATM machines, point-of-sale terminals, industrial automation systems, thin clients, medical devices, digital signage, kiosks, and other fixed purpose devices. Windows IoT Enterprise allows you to build these fixed purpose devices with specific allowances and restrictions in the license agreement.

## Why Do Customers Choose Windows IoT Enterprise?

There are three main reasons why customers choose to develop with Windows IoT Enterprise:

1. **Productive** - Leverage existing knowledge to build and manage Windows IoT Enterprise devices with powerful tools and technologies to quickly unlock data and drive digital transformation.
1. **Trusted** - Windows IoT Enterprise helps you build IoT solutions that you can trust, keeping your devices, data, and identities secure and giving you peace of mind.
3. **Smart** - Windows IoT Enterprise helps you connect your devices to each other, your network, and the cloud, so you can use data to drive real business insight and create new business opportunities

> [!TIP]
>
> If you are building any kind of **OEM style appliance**, such as a point-of-sale or retail device, industrial automation equipment, digital signage, medical equipment or any appliance with a screen, Windows IoT Enterprise is the solution for you.
>
> See how our [customers](https://www.microsoft.com/WindowsForBusiness/windows-iot) are using Windows IoT Enterprise to accomplish their business goals.

## Windows IoT Enterprise LTSC

Windows IoT Enterprise LTSC is designed for fixed purpose devices and use cases where functionality and features remain constant for the life of the device.  These devices are typically found in industries including, but not limited to, banking, healthcare, hospitality, manufacturing and retail. Devices that require regulatory certification and devices that perform a critical business function can't accept feature updates for years at a time.  

We designed Windows IoT Enterprise LTSC with these use cases in mind. We support each Windows IoT Enterprise LTSC release for 10 years, and that features and functionality don't change over the course of that 10-year lifecycle.

Windows IoT Enterprise LTSC releases approximately every three years, and each release contains all the new capabilities and support included in Windows feature updates that have been released since the previous LTSC release.  LTSC releases are named with a specific year, such as Windows 11 IoT Enterprise LTSC 2024.

Windows IoT Enterprise LTSC releases receive 10 years of servicing and support. Upgrading from one version of Windows IoT Enterprise LTSC to the next version requires a new license.

> [!NOTE]
> Microsoft does not publish feature updates through Windows Update for devices running Windows IoT Enterprise LTSC.

### Considerations when to use LTSC

The LTSC is designed for devices and use cases where features and functionality don't change. It provides 10-years of security servicing to a static feature set. As part of this offering you should consider:

| Area | Description |
| --- | --- |
| **Silicon support** | Windows IoT Enterprise LTSC is supported for security, reliability, and compatibility on the latest silicon available at the time of release.  Previous silicon generations may still in support by the Silicon Vendor (SV) or Original Equipment Manufacturer (OEM). </br></br>When you utilize the LTSC, you must factor hardware into your decision, making sure you have a long-term supply of components for the expected life of your devices. If the hardware your device is using needs to be replaced in five years, do you have a replacement supply to support the version you're running?</br></br>For more information, see [Windows IoT Enterprise processor list](/windows/iot/iot-enterprise/hardware/hardware_requirements#processor) |
| **API support** | Windows IoT Enterprise LTSC is designed to support the latest application APIs and driver interfaces available at the time of release.  These interfaces don't change during the life-cycle of the LTSC. Access to updated interfaces requires updating to a successor release that contains the updated interfaces. |
| **Security** | Windows IoT Enterprise LTSC, with the latest cumulative update distributed monthly installed, provides the most secure environment for the most demanding industrial devices. |
| **Stability** | Windows IoT Enterprise LTSC, with the latest cumulative update distributed monthly installed, has the latest performance and stability improvements. |
| **Hardware choice** | New devices target and ship with the latest Windows release to light up new hardware capabilities and improvements. |

## Next step

[How to Start Prototyping with Windows IoT Enterprise](./Hardware/Prototype.md)