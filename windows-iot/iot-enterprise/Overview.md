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

<!--
### Fixed purpose devices

Windows is well known as the operating system for laptops and desktops that have been used by consumers and businesses worldwide for decades. Windows also powers many ATM machines, point-of-sale terminals, industrial automation systems, thin clients, medical devices, digital signage, kiosks, and other fixed purpose devices. Windows IoT Enterprise allows you to build these fixed purpose devices with specific allowances and restrictions in the license agreement.  

> [!TIP]
> See your licensing agreement for complete guidance on all Windows IoT Enterprise usage scenarios. If you are an end-user customer, your OEM should have provided you with the terms in an agreement. If you are an OEM, you can direct questions to your distributor regarding your specific licensing agreement.  

A fixed purpose device differs from a general-purpose device in the following ways:  

* The device is locked down to a single application or fixed set of applications through the Assigned Access or Shell Launcher features.  
* The device experience is often immediate when the customer powers-on. This is achieved by configuring the device image to skip the normal Windows out-of-box experiences.
* Keyboards, USB ports, and device policies can be locked down to constrain the device to be used only in its fixed purpose.  
* The IoT Device OEM licenses the device to the user with the software attached to the device as a complete product and passes through specific Windows terms in their own IoT OEM agreements.
* The OEM provides the customer support for their complete product, including the functions performed by the operating system.

> [!NOTE]
>
> There are currently **two** release channels for Windows 10 IoT Enterprise:
> * The General Availability Channel receives feature updates twice per year and provides support for **18-30 months**.
> * The Long Term Servicing Channel, which is designed to be used only for specialized devices (which typically don't run Office) such as those that control medical equipment or ATM machines, receives new feature releases every two to three years and provides support for **10 years**.
>
> There is currently **one** annual release channel for Windows 11 IoT Enterprise. For more information, see [Windows 11 servicing](/lifecycle/faq/windows#windows-11) and [Windows for IoT Product Lifecycle](/lifecycle/products/?terms=Windows%20IoT%20Enterprise).

## General Availability Channel

In the general availability servicing channel, feature updates are available as soon as Microsoft releases them. This servicing model is ideal for pilot deployments and testing of Windows 10 feature updates and for users such as developers who need to work with the latest features immediately. Once the latest release has gone through pilot deployment and testing, you're able to choose the timing at which it goes into broad deployment.

Review [General Availability Channel](/windows/deployment/update/waas-overview#servicing) for more information.

## Long-term Servicing Channel (LTSC)

Specialized systems, such as PCs that control medical equipment, point-of-sale systems, and ATMs, often require a longer servicing option because of their purpose. These devices typically perform a single important task and don’t need feature updates as frequently as other devices in the organization. For these fixed-purpose devices, we recommend the long-term servicing channel, since it’s more important that these devices be kept as stable and secure as possible than that they be up to date with UI changes. The LTSC servicing model prevents Windows 10 IoT Enterprise LTSC devices from receiving the usual feature updates and provides only quality updates to ensure that device security stays up to date. With this in mind, quality updates are still immediately available to Windows 10 IoT Enterprise LTSC clients, but customers can choose to defer them by using a servicing tool.

Review [Long-term Servicing Channel](/windows/deployment/update/waas-overview#long-term-servicing-channel) for more information.

### LTSC Model

Microsoft makes available a new [Windows 10 IoT Enterprise LTSC release](/lifecycle/products/?terms=Windows%2010%20IoT%20Enterprise) approximately every three years. Each Windows 10 IoT Enterprise LTSC release is its own SKU and contains all the new capabilities and support updates included in the Windows 10 IoT Enterprise features updates since the previous LTSC release. To access these feature updates, a new Windows 10 IoT Enterprise LTSC SKU license must be purchased. For example, to get access to the new security, deployment, and management updates and features released since the launch of Windows 10 IoT Enterprise 2016 LTSC, a license for Windows 10 IoT Enterprise 2019 LTSC must be purchased, and an update applied to the device. Due to the long life of the LTSC releases and the benefit of remaining on a specific release for 10 years, an upgrade fee is charged for customers moving from one LTSC release to another.

Review the [Fixed Lifecycle Policy](/lifecycle/policies/fixed) for more information.
-->
