---
title: Arm64 Guidance
author: sydbruck
ms.author: sybruckm
ms.date: 10/09/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Windows IoT on Arm64
keywords: IoT Enterprise, Hardware, Windows IoT, Arm64, NXP
---

# Getting Started with Windows IoT Enterprise for Arm64

This article helps you use the strength of Windows on low power, low cost devices with Windows IoT Enterprise for Arm64.

## What is Windows IoT Enterprise on Arm?

Windows IoT Enterprise on Arm is simply Windows IoT Enterprise built for Arm64 devices. Windows IoT Enterprise on Arm64 is the same OS as it is on X64-based devices, with IoT features available to help you build secure, powerful devices across any architecture. Since the OS is the same, the capabilities and the documentation are the same as well. Refer to the standard Windows IoT Enterprise documentation for Arm64 guidance.

## Getting Started

For the quickest way to get familiar with Windows IoT Enterprise on Arm64, see our [Tutorial: Setup an NXP i,MX EVK](../Tutorials/Win10-NXP-iMX.md)

## Frequently Asked Questions

### Which hardware is supported?

You can get started with the NXP Evaluation Kits (EVK), or choose a board from one of our partners.

|Manufacturer|Hardware  |
|-|---------|
|NXP|[i.MX 8M EVK](https://www.nxp.com/design/development-boards/i-mx-evaluation-and-development-boards/evaluation-kit-for-the-i-mx-8m-applications-processor:MCIMX8M-EVK)<br> [i.MX 8M Plus EVK](https://www.nxp.com/design/development-boards/i-mx-evaluation-and-development-boards/evaluation-kit-for-the-i-mx-8m-plus-applications-processor:8MPLUSLPD4-EVK)<br>[i.MX 8M Mini EVK](https://www.nxp.com/design/development-boards/i-mx-evaluation-and-development-boards/evaluation-kit-for-the-i-mx-8m-mini-applications-processor:8MMINILPD4-EVK)<br> [i.MX 8M Nano EVK](https://www.nxp.com/design/development-boards/i-mx-evaluation-and-development-boards/evaluation-kit-for-the-i-mx-8m-nano-applications-processor:8MNANOD4-EVK)<br> [i.MX 8X EVK](https://www.nxp.com/products/processors-and-microcontrollers/arm-processors/i-mx-applications-processors/i-mx-8-applications-processors/i-mx-8x-family-arm-cortex-a35-3d-graphics-4k-video-dsp-error-correcting-code-on-ddr:i.MX8X)<br> [i.MX 93 EVK](https://www.nxp.com/products/processors-and-microcontrollers/arm-processors/i-mx-applications-processors/i-mx-9-processors/i-mx-93-applications-processor-family-arm-cortex-a55-ml-acceleration-power-efficient-mpu:i.MX93)|
|Avnet|[MSC SM2S IMX8PLUS](https://embedded.avnet.com/product/msc-sm2s-imx8plus/)<br> [MSC SM2S-IMX8M](https://embedded.avnet.com/product/msc-sm2s-imx8m/)    |
|Advantech|[RSB-3720](https://www.advantech.com/en/products/single_board_computer/rsb-3720/mod_d2f1b0bc-650b-449a-8ef7-b65ce4f69949)<br> [ROM-5720](https://www.advantech.com/en/products/computer-on-module/rom-5720/mod_4fbfe9fa-f5b2-4ba8-940e-e47585ad0fef)<br> [ROM-5722](https://www.advantech.com/en/products/computer-on-module/rom-5722/mod_11aa0c77-868e-4014-8151-ac7a7a1c5c1b)     |
|SECO|[Trizeps VIII Plus](https://edge.seco.com/usa/trizeps-viii-plus.html)<br> [Trizeps VIII](https://edge.seco.com/usa/trizeps-viii.html)<br> [Trizeps VIII Mini](https://edge.seco.com/usa/trizeps-viii-mini.html)     |
|ASUS|[IMX8P IM A](https://www.asus.com/us/site/IOT/#!/products/single-board-computer/IMX8P-IM-A)<br> [PE100A](https://iot.asus.com/products/intelligent-edge-computer/PE100A/)     |
|Reycom|[RIA 8M](https://www.reycom.swiss/oem-hardware/ria-8m/)<br> [RIA 8M](https://www.reycom.swiss/oem-hardware/ria-8mplus/)|

### Where can I download Windows?

For more information on the various ways to get a Windows license, see our [licensing page](../Commercialization/Licensing.md).

### Which Windows IoT Enterprise version should I use?

Both LTSC and GAC editions of Windows IoT Enterprise are available for NXP devices. You can find more information on the [Hardware Requirements](Hardware_Requirements.md) page.

|SoC  |Windows 10 IoT Enterprise  |Windows 11 IoT Enterprise  |
|---------|---------|---------|
|i.MX 8M      |    build 19044 or later     |    Not Supported    |
|i.MX 8M Mini |    build 19044 or later     |    Not Supported    |
|i.MX 8M Nano |    build 19044 or later     |    Not Supported    |
|i.MX 8M Plus |    build 19044 or later     |    Not Supported    |
|i.MX 8X      |    build 19044 or later     |    Not Supported    |
|i.MX 93      |    build 19044 or later     |    Coming Soon      |

### Can I run applications that aren't native to Arm64?

On Arm64 devices, Windows IoT Enterprise allows emulation of x86 applications. For more information, see [How x86 emulation works on Arm](/windows/arm/apps-on-arm-x86-emulation).

### Can I use Hyper-V on my Arm64 device?

Hyper-V is only supported on boards that support Windows 11 IoT Enterprise. For more information, see [Which Windows IoT Enterprise version should I use?](#which-windows-iot-enterprise-version-should-i-use).

### Can I use Windows IoT Enterprise on Qualcomm hardware?

Yes, you can see the list of supported Qualcomm processors on the [Windows 11 processor requirements](/windows-hardware/design/minimum/supported/windows-11-22h2-supported-qualcomm-processors) page.

Additionally, the Qualcomm QCS6490 and QCS5430 are supported as part of [Qualcomm's IoT hardware longevity program](https://www.qualcomm.com/products/product-longevity-program), guaranteeing both hardware and OS support with Windows IoT Enterprise on Qualcomm.
