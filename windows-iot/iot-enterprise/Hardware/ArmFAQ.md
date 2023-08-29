---
title: Arm64 Guidance
author: sydbruck
ms.author: sybruckm
ms.date: 08/29/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Windows IoT on Arm64
keywords: IoT Enterprise, Hardware, Windows IoT, Arm64, NXP
---

# Getting Started with Windows IoT Enterprise for Arm64
This article will help you leverage the strength of Windows on low power, low cost devices with Windows IoT Enterprise for Arm64.

## What is Windows IoT Enterprise on Arm?
Windows IoT Enterprise on Arm is simply Windows IoT Enterprise built for Arm64 devices. Windows IoT Enterprise on Arm64 is the same OS as it is on X86 and X64-based devices, with IoT features available to help you build secure, powerful devices across any architecture. Since the OS is the same, the capabilities and the documentation are the same as well. Refer to the standard Windows IoT Enterprise documentation for Arm64 guidance. 

## Getting Started
Follow our Quick Start guide to learn how to get Windows 10 IoT Enterprise running on NXP's Evaluation Kits. This is the quickest way to get familiar with Windows IoT Enterprise on Arm64.

## Frequently Asked Questions

### Which hardware is supported?
You can get started with the NXP Evaluation Kits (EVK), or choose a board from one of our partners.

* NXP EVKs: [i.MX 8M EVK](https://www.nxp.com/design/development-boards/i-mx-evaluation-and-development-boards/evaluation-kit-for-the-i-mx-8m-applications-processor:MCIMX8M-EVK), [i.MX 8M Plus EVK](https://www.nxp.com/design/development-boards/i-mx-evaluation-and-development-boards/evaluation-kit-for-the-i-mx-8m-plus-applications-processor:8MPLUSLPD4-EVK), [i.MX 8M Mini EVK](https://www.nxp.com/design/development-boards/i-mx-evaluation-and-development-boards/evaluation-kit-for-the-i-mx-8m-mini-applications-processor:8MMINILPD4-EVK), [i.MX 8M Nano EVK](https://www.nxp.com/design/development-boards/i-mx-evaluation-and-development-boards/evaluation-kit-for-the-i-mx-8m-nano-applications-processor:8MNANOD4-EVK), [i.MX 8X EVK](https://www.nxp.com/products/processors-and-microcontrollers/arm-processors/i-mx-applications-processors/i-mx-8-applications-processors/i-mx-8x-family-arm-cortex-a35-3d-graphics-4k-video-dsp-error-correcting-code-on-ddr:i.MX8X), [i.MX 93 EVK](https://www.nxp.com/products/processors-and-microcontrollers/arm-processors/i-mx-applications-processors/i-mx-9-processors/i-mx-93-applications-processor-family-arm-cortex-a55-ml-acceleration-power-efficient-mpu:i.MX93)
* Avnet: [MSC SM2S IMX8PLUS](https://embedded.avnet.com/product/msc-sm2s-imx8plus/), [MSC SM2S-IMX8M](https://embedded.avnet.com/product/msc-sm2s-imx8m/)
* Advantech: [RSB-3720](https://www.advantech.com/en/products/single_board_computer/rsb-3720/mod_d2f1b0bc-650b-449a-8ef7-b65ce4f69949), [ROM-5720](https://www.advantech.com/en/products/computer-on-module/rom-5720/mod_4fbfe9fa-f5b2-4ba8-940e-e47585ad0fef), [ROM-5722](https://www.advantech.com/en/products/computer-on-module/rom-5722/mod_11aa0c77-868e-4014-8151-ac7a7a1c5c1b)
* ASUS: [IMX8P IM A](https://www.asus.com/us/site/IOT/#!/products/single-board-computer/IMX8P-IM-A), [PE100A](https://iot.asus.com/products/intelligent-edge-computer/PE100A/)
* SECO: [Trizeps VIII Plus](https://edge.seco.com/usa/trizeps-viii-plus.html), [Trizeps VIII](https://edge.seco.com/usa/trizeps-viii.html), [Trizeps VIII Mini](https://edge.seco.com/usa/trizeps-viii-mini.html)
* Reycom: [RIA 8M](https://www.reycom.swiss/en/oem-hardware/the-ria-8m/)

### I've chosen my hardware, where can I find the BSP?


|Manufacturer|Hardware  |BSP |
|-|---------|---------|
|NXP|[i.MX 8M EVK](https://www.nxp.com/design/development-boards/i-mx-evaluation-and-development-boards/evaluation-kit-for-the-i-mx-8m-applications-processor:MCIMX8M-EVK), [i.MX 8M Plus EVK](https://www.nxp.com/design/development-boards/i-mx-evaluation-and-development-boards/evaluation-kit-for-the-i-mx-8m-plus-applications-processor:8MPLUSLPD4-EVK), [i.MX 8M Mini EVK](https://www.nxp.com/design/development-boards/i-mx-evaluation-and-development-boards/evaluation-kit-for-the-i-mx-8m-mini-applications-processor:8MMINILPD4-EVK), [i.MX 8M Nano EVK](https://www.nxp.com/design/development-boards/i-mx-evaluation-and-development-boards/evaluation-kit-for-the-i-mx-8m-nano-applications-processor:8MNANOD4-EVK), [i.MX 8X EVK](https://www.nxp.com/products/processors-and-microcontrollers/arm-processors/i-mx-applications-processors/i-mx-8-applications-processors/i-mx-8x-family-arm-cortex-a35-3d-graphics-4k-video-dsp-error-correcting-code-on-ddr:i.MX8X), [i.MX 93 EVK](https://www.nxp.com/products/processors-and-microcontrollers/arm-processors/i-mx-applications-processors/i-mx-9-processors/i-mx-93-applications-processor-family-arm-cortex-a55-ml-acceleration-power-efficient-mpu:i.MX93)|[NXP BSP](https://aka.ms/nxpiot)   |
|Avnet|[MSC SM2S IMX8PLUS](https://embedded.avnet.com/product/msc-sm2s-imx8plus/), [MSC SM2S-IMX8M](https://embedded.avnet.com/product/msc-sm2s-imx8m/)    |         |
|Advantech|[RSB-3720](https://www.advantech.com/en/products/single_board_computer/rsb-3720/mod_d2f1b0bc-650b-449a-8ef7-b65ce4f69949), [ROM-5720](https://www.advantech.com/en/products/computer-on-module/rom-5720/mod_4fbfe9fa-f5b2-4ba8-940e-e47585ad0fef), [ROM-5722](https://www.advantech.com/en/products/computer-on-module/rom-5722/mod_11aa0c77-868e-4014-8151-ac7a7a1c5c1b)     |         |
|SECO|[Trizeps VIII Plus](https://edge.seco.com/usa/trizeps-viii-plus.html), [Trizeps VIII](https://edge.seco.com/usa/trizeps-viii.html), [Trizeps VIII Mini](https://edge.seco.com/usa/trizeps-viii-mini.html)     |         |
|ASUS|[IMX8P IM A](https://www.asus.com/us/site/IOT/#!/products/single-board-computer/IMX8P-IM-A), [PE100A](https://iot.asus.com/products/intelligent-edge-computer/PE100A/)     |         |

### Where can I download Windows?

For more information on the various ways to get a Windows license, see our [licensing page](../Commercialization/Licensing.md).

### Which Windows IoT Enterprise version should I use?

|SoC  |Windows 10 IoT Enterprise  |Windows 11 IoT Enterprise  |
|---------|---------|---------|
|i.MX 8M     |    Supported from 22H2     |    Not Supported     |
|i.MX 8M Mini|    Supported from 22H2     |    Not Supported     |
|i.MX 8M Nano|    Supported from 22H2     |    Not Supported     |
|i.MX 8M Plus|    Supported from 22H2     |    Not Supported     |
|i.MX 8 X    |    Supported from 22H2     |    Not Supported     |
|i.MX 93     |    Supported from 22H2     |    Coming Soon     |

### Can I run applications that are not native to Arm64?
On Arm64 devices, Windows IoT Enterprise allows or emulation of x86 applications. 

### Can I use Hyper-V on my Arm64 device?
Hyper-V is only supported on boards that support Windows 11 IoT Enterprise. See [above](#which-windows-iot-enterprise-version-should-i-use) for details.
