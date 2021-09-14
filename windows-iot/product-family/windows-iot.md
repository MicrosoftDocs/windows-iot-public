---
title: Overview of Windows 10 IoT
author: rsameser
ms.author: riameser
ms.date: 3/16/2021
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: See an overview of Windows 10 IoT and what you can do with it.
keywords: Windows 10 IoT Enterprise, Windows 10 IoT Core, Windows Sever IoT 2019, editions
---

# An overview of Windows 10 IoT

## What is Windows 10 IoT?
Windows 10 IoT is a member of the Windows 10 family that brings enterprise-class power, security, and manageability to the Internet of Things.  It leverages Windows' embedded experience, ecosystem and cloud connectivity, allowing organizations to create their Internet of Things with secure devices that can be quickly provisioned, easily managed, and seamlessly connected to an overall cloud strategy.  

## Windows 10 IoT Editions
Windows 10 IoT comes in **three** editions.
1. [Windows 10 IoT Enterprise](../iot-enterprise/Getting_Started.md) is a full version of Windows 10 with specialized features to create dedicated devices locked down to a specific set of applications and peripherals.
2. [Windows Server IoT 2019](../server/windows-server.md) is a full version of Windows Server 2019 that delivers enterprise manageability and security to IoT solutions.
3. [Windows 10 IoT Core](https://docs.microsoft.com/windows/iot-core/windows-iot-core) is the smallest member of the Windows 10 operating system family. While only running a single app, it still has the manageability and security expected from Windows 10.  

## Fixed purpose devices
Windows is well known as the operating system for laptops and desktops that have been used by consumers and businesses worldwide for decades. Windows also powers many ATM machines, point-of-sale terminals, industrial automation systems, thin clients, medical devices, digital signage, kiosks, and other fixed purpose devices. Windows IoT allows you to build these fixed purpose devices with specific allowances and restrictions in the license agreement.

>[!TIP]
>
> See your licensing agreement for complete guidance on all Windows 10 IoT Enterprise usage scenarios. If you are an end-user customer, your OEM should have provided you with the terms in an agreement. If you are an OEM, you can direct questions to your distributor regarding your specific licensing agreement.

A fixed purpose device differs from a general-purpose device in the following ways:
* The device is locked down to a single application or fixed set of applications through the Assigned Access or Shell Launcher features.
* The device experience is often immediate when the customer powers-on. This is achieved by configuring the device image to skip the normal Windows out-of-box experiences.
* Keyboards, USB ports, and device policies can be locked down to constrain the device to be used only in its fixed purpose.
* The IoT Device OEM licenses the device to the user with the software attached to the device as a complete product and passes through specific Windows terms in their own IoT OEM agreements.
* The OEM provides the customer support for their complete product, including the functions performed by the operating system.
