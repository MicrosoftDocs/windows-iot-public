---
title: ARM64 Overview
author: anthonychen
ms.author: anthonychen
ms.date: 6/7/2024
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Windows IoT Enterprise on ARM64 Overview
keywords: IoT Enterprise, Hardware, Windows IoT, Arm64, NXP
---

# What is Windows IoT Enterprise on Arm?

Windows IoT Enterprise on Arm is simply Windows IoT Enterprise that is built for and runs on ARM64 processors. It has the same features and capabilities of Windows IoT Enterprise for x64-based processors, enabling you to build secure and powerful devices across any processor architecture.

## Windows IoT Enterprise on Arm vs. x86/x64

Windows IoT Enterprise on Arm is designed to be familiar for device builders and developers used to working with x86/x64. Most of the documentation for Windows IoT Enterprise applies to both ARM64 and x86/x64, with differences called out directly in each feature's documentation page. A few general points to consider are mentioned below. 

### Applications

Windows IoT Enterprise on Arm can run both **native** ARM64 applications and **emulated** x86/x64 applications.

**Native** ARM64 applications are applications that are compiled and built specifically for the ARM64 architecture. Native Arm64 applications provide the best performance, responsiveness, and power consumption.

**Emulated** applications are x86/x64 applications that are run as-is without modification on Windows IoT Enterprise on Arm using inbox emulation technology. x86/x64 application emulation provides a fast way for device builders to port existing x86/x64 designs to ARM64. Windows 10 IoT Enterprise on Arm supports emulating x86 applications, whereas Windows 11 IoT Enterprise on Arm supports emulating both x86 and x64 applications.

Learn more about Arm application development in the [Windows IoT Enterprise on Arm application development documentation](../Development/App_dev.md) or the [Windows on Arm application development documentation](/windows/arm/overview). 

### Device Drivers

Device drivers must be built natively for ARM64 to run on Windows IoT Enterprise on Arm. ARM64 drivers for many commonly used devices are provided by Microsoft in Windows, the processor vendor, or the board manufacturer in a board's Board Support Package (BSP). In addition, many device vendors provide drivers for their devices through either Windows Update or through 3rd-party support channels. For a device without an available driver, you need to work with the device vendor to get one or write one yourself. 

Learn more about writing and deploying drivers the [Windows IoT Enterprise device driver documentation](../OS-Features/Device-Drivers.md).

## ARM64 Processor Support

Windows IoT Enterprise on Arm supports various NXP and Qualcomm processors, catering to different device needs and performance requirements. 

NXP processors provide the lowest power and lowest cost options for building Windows IoT Enterprise devices, making them excellent for device categories like thin clients, kiosks, gateways, and human machine interfaces (HMIs).

Qualcomm processors provide excellent performance while maintaining the low power benefits of ARM64 processors and are excellent for use cases that require high quality visualizations or machine learning/AI.

For the specific processors models supported for each Windows IoT Enterprise OS version, refer to the [Windows IoT Enterprise Processor Lists](../Hardware/Processor_Requirements.md#windows-iot-enterprise-processor-lists).

## ARM64 Hardware Platforms

Each ARM64 hardware platform in the following table is built with an ARM64 Processor that supports Windows IoT Enterprise and has a Board Support Package (BSP) that supports Windows IoT Enterprise. Visit the hardware platform's product page to learn more about its capabilities and ordering information.

|Processor|Platform|Form Factor|
|-|---------|-------|
|Qualcomm QCS6490|[Thundercomm RB3 Gen 2](https://www.thundercomm.com/product/qualcomm-rb3-gen-2/) (in preview)|Development Kit|
|NXP i.MX 8M Plus|[NXP i.MX 8M Plus EVK](https://www.nxp.com/design/development-boards/i-mx-evaluation-and-development-boards/evaluation-kit-for-the-i-mx-8m-plus-applications-processor:8MPLUSLPD4-EVK)|Development Kit|
|NXP i.MX 8M Plus|[Avnet MSC SM2S IMX8PLUS](https://embedded.avnet.com/product/msc-sm2s-imx8plus/)|System on Module|
|NXP i.MX 8M Plus|[Advantech ROM-5722](https://www.advantech.com/en/products/computer-on-module/rom-5722/mod_11aa0c77-868e-4014-8151-ac7a7a1c5c1b)|System on Module|
|NXP i.MX 8M Plus|[SECO Trizeps VIII Plus](https://edge.seco.com/usa/trizeps-viii-plus.html)|System on Module|
|NXP i.MX 8M Plus|[Advantech EPC-R3720](https://www.advantech.com/en/products/880a61e5-3fed-41f3-bf53-8be2410c0f19/epc-r3720/mod_fde326be-b36e-4044-ba9a-28c4c49a25c6)|Embedded PC|
|NXP i.MX 8M Plus|[Advantech RSB-3720](https://www.advantech.com/en/products/single_board_computer/rsb-3720/mod_d2f1b0bc-650b-449a-8ef7-b65ce4f69949)|Single Board Computer|
|NXP i.MX 93|[NXP i.MX 93 EVK](https://www.nxp.com/products/processors-and-microcontrollers/arm-processors/i-mx-applications-processors/i-mx-9-processors/i-mx-93-applications-processor-family-arm-cortex-a55-ml-acceleration-power-efficient-mpu:i.MX93)|Development Kit|
|NXP i.MX 8M Mini|[NXP i.MX 8M Mini EVK](https://www.nxp.com/design/development-boards/i-mx-evaluation-and-development-boards/evaluation-kit-for-the-i-mx-8m-mini-applications-processor:8MMINILPD4-EVK)|Development Kit|
|NXP i.MX 8M Mini|[SECO Trizeps VIII Mini](https://edge.seco.com/usa/trizeps-viii-mini.html)|System on Module|
|NXP i.MX 8X|[NXP i.MX 8X EVK](https://www.nxp.com/products/processors-and-microcontrollers/arm-processors/i-mx-applications-processors/i-mx-8-applications-processors/i-mx-8x-family-arm-cortex-a35-3d-graphics-4k-video-dsp-error-correcting-code-on-ddr:i.MX8X)|Development Kit|
|NXP i.MX 8M|[NXP i.MX 8M EVK](https://www.nxp.com/design/development-boards/i-mx-evaluation-and-development-boards/evaluation-kit-for-the-i-mx-8m-applications-processor:MCIMX8M-EVK)|Development Kit|
|NXP i.MX 8M|[MSC SM2S-IMX8M](https://embedded.avnet.com/product/msc-sm2s-imx8m/)    |System on Module|
|NXP i.MX 8M|[Advantech ROM-5720](https://www.advantech.com/en/products/computer-on-module/rom-5720/mod_4fbfe9fa-f5b2-4ba8-940e-e47585ad0fef)|System on Module|
|NXP i.MX 8M|[SECO Trizeps VIII](https://edge.seco.com/usa/trizeps-viii.html)|System on Module|
|NXP i.MX 8M Nano|[NXP i.MX 8M Nano EVK](https://www.nxp.com/design/development-boards/i-mx-evaluation-and-development-boards/evaluation-kit-for-the-i-mx-8m-nano-applications-processor:8MNANOD4-EVK)|Development Kit|

## Getting Started

For the quickest way to get familiar with Windows IoT Enterprise on ARM64, see our [Tutorial: Setup an NXP i.MX EVK](../Tutorials/Win10-NXP-iMX.md).