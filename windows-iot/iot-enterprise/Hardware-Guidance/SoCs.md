---
title: SoCs and Custom Boards for Windows 10 IoT Enterprise
author: rsameser
ms.author: riameser
ms.date: 1/31/2021
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about SoCs and Custom Boards requirements for Windows 10 IoT Enterprise.
keywords: IoT Enterprise, Hardware, SoCs, Custom Boards, development devices, boards, SOC, SOM, system on chips, Windows IoT
---
# SoCs and Custom Boards

## Microsoft-enabled SoCs

Microsoft works alongside Intel, Qualcomm, and AMD to verify support for Windows 10 IoT Enterprise on several vendors' system on a chip (SoCs). These SoCs are used in hundreds of different devices that you can use to prototype and commercialize your idea. The SoC you choose to adopt will depend on considerations such as performance requirements, power profile, cost, physical connectivity options, long-term support, and operating conditions.

You'll also need to decide whether you want to use an off-the-shelf board or device, build a custom device using a system on a module (SoM) plus a custom carrier board, or build a complete custom board. Cost and the degree of customization are the key factors in this decision, with both generally increasing as you customize further.

## Boards
If an off-the-shelf device is in a form factor that includes the connectivity options that work for your scenarios, that will often be the most cost- and time-effective choice.  

For most people, developing a complete custom board would make sense when the product is expected to be sold in volumes greater than hundreds, or even thousands, of millions of units. For smaller volumes, using a SoM and designing a custom carrier board, instead of designing a completely new board, can significantly reduce your cost and time-to-market, as well as streamlining software development and integration.

Each of the platforms has unique features that need attention during implementation, please review the following SoC provider's websites for more details.  

* [Intel](https://www.intel.com/content/www/us/en/internet-of-things/overview.html)
* [AMD](https://www.amd.com/en/products/embedded)
* [Qualcomm](https://www.qualcomm.com/products/snapdragon-850-mobile-compute-platform)
* [VIA Technologies](https://www.viatech.com/en/products/boards/embedded-boards/)

## Additional Resources
* [Windows 10 IoT Enterprise Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/desktop/iot-ent-overview)
* [Windows Processor Requirements](https://docs.microsoft.com/windows-hardware/design/minimum/windows-processor-requirements)
