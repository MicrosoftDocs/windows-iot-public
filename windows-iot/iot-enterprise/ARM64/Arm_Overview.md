---
title: Arm Overview
author: anthonychen
ms.author: anthonychen
ms.date: 6/7/2024
ms.topic: overview
ms.service: windows-iot
ms.subservice: iot
description: Windows IoT Enterprise on Arm Overview
keywords: IoT Enterprise, Hardware, Windows IoT, Arm64, NXP
---

# What is Windows IoT Enterprise on Arm?

Windows IoT Enterprise on Arm is simply Windows IoT Enterprise that is built for and runs on 64-bit Arm (Arm64) processors. It has the same features and capabilities of Windows IoT Enterprise for x64-based processors, enabling you to build secure and powerful devices across any processor architecture.

## Windows IoT Enterprise on Arm vs. x86/x64

Windows IoT Enterprise on Arm is designed to be familiar for device builders and developers used to working with x86/x64. Most of the documentation for Windows IoT Enterprise applies to both Arm64 and x86/x64, with differences called out directly in each feature's documentation page. A few general points to consider are mentioned below.

### Applications

Windows IoT Enterprise on Arm can run **native** Arm64 applications and **emulated** x86/x64 applications.

**Native** Arm64 applications are applications that are compiled and built specifically for the Arm64 architecture. Native Arm64 applications provide the best performance, responsiveness, and power consumption.

**Emulated** applications are x86/x64 applications that are run as-is without modification on Windows IoT Enterprise on Arm using inbox emulation technology. x86/x64 application emulation provides a fast way for device builders to port existing x86/x64 designs to Arm64. Windows 10 IoT Enterprise on Arm supports emulating x86 applications, whereas Windows 11 IoT Enterprise on Arm supports emulating both x86 and x64 applications.

Learn more about Arm application development in the [Windows IoT Enterprise on Arm application development documentation](../Development/App_dev.md) or the [Windows on Arm application development documentation](/windows/arm/overview).

### Device Drivers

Device drivers must be built natively for Arm64 to run on Windows IoT Enterprise on Arm. Arm64 drivers for many commonly used devices are provided in Windows or in a board's Board Support Package (BSP). In addition, many device vendors provide drivers for their devices through Windows Update or 3rd-party support channels. For a device without an available driver, you need to work with the device vendor to get one or write one yourself.

Learn more about writing and deploying drivers the [Windows IoT Enterprise device driver documentation](../OS-Features/Device-Drivers.md).

## Arm64 Processor Support

Windows IoT Enterprise on Arm supports various NXP and Qualcomm processors, catering to different device needs and performance requirements.

[NXP processors](./NXP.md) provide the lowest power and lowest cost options for building Windows IoT Enterprise devices, making them excellent for device categories like thin clients, kiosks, gateways, and human machine interfaces (HMIs).

Qualcomm processors provide excellent performance while maintaining the low power benefits of Arm64 processors and are excellent for use cases that require high quality visualizations or machine learning/AI.

For the specific processors models supported for each Windows IoT Enterprise OS version, refer to the [Windows IoT Enterprise Processor Lists](../Hardware/Processor_Requirements.md#windows-iot-enterprise-processor-lists).

## Arm64 Hardware Platforms and Boards

To get started building Windows IoT Enterprise on Arm devices, select an [Arm64 hardware platform or board](../Hardware/Platforms_and_Boards.md). Each listed Arm64 hardware platform and board has a Board Support Package (BSP) that supports Windows IoT Enterprise. Visit the hardware manufacturer's product page to learn more about its capabilities and ordering information.

## Getting Started

For the quickest way to get familiar with Windows IoT Enterprise on Arm64, see our [Tutorial: Setup an NXP i.MX EVK](../Tutorials/Win10-NXP-iMX.md).
