--
title: Arm64 Guidance
author: sydbruck
ms.author: sybruckm
ms.date: 10/19/2022
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Windows IoT on Arm64
keywords: IoT Enterprise, Hardware, Windows IoT, Arm64, NXP
---

# Getting Started with Windows IoT Enterprise for Arm64
This article will help you leverage the strength of Windows on low power, low cost devices with Windows IoT Enterprise for Arm64.

## What is Windows IoT Enterprise on Arm?
Windows IoT Enterprise on Arm is simply Windows IoT Enterprise built for Arm64 devices. Windows IoT Enterprise on Arm64 is the same OS as it is on X86 and X64-based devices, with IoT features available to help you build secure, powerful devices across any architecture. Since the OS is the same, the capabilities and the documentation are the same as well. Please refer to the standard Windows IoT Enterprise documentation for Arm64 guidance. The only noted differences are captured below in the list of exceptions.

## NXP i.MX8 Family

### Exceptions
#### Emulation
On Arm-based devices, only X86 (32-bit) applications can be emulated on Windows IoT Enterprise.

#### Graphics Runtime
Currently, only D3D11, [feature level 9.3](https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-devices-downlevel-intro) is supported on the NXP i.MX8 family.

#### Hyper-V
[Hyper-V](https://learn.microsoft.com/en-us/virtualization/hyper-v-on-windows/about/) is not supported on the NXP i.MX8 family.

#### Windows 11
Windows 11 is not supported on the NXP i.MX8 family.

### Frequently Asked Questions

#### Which hardware can I use?
You can get started with the NXP EVK boards, or choose a board from one of our partners below.

* NXP EVKs: [i.MX 8M EVK](https://www.nxp.com/design/development-boards/i-mx-evaluation-and-development-boards/evaluation-kit-for-the-i-mx-8m-applications-processor:MCIMX8M-EVK), [i.MX 8M Plus EVK](https://www.nxp.com/design/development-boards/i-mx-evaluation-and-development-boards/evaluation-kit-for-the-i-mx-8m-plus-applications-processor:8MPLUSLPD4-EVK), [i.MX 8M Mini EVK](https://www.nxp.com/design/development-boards/i-mx-evaluation-and-development-boards/evaluation-kit-for-the-i-mx-8m-mini-applications-processor:8MMINILPD4-EVK), [i.MX 8M Nano EVK](https://www.nxp.com/design/development-boards/i-mx-evaluation-and-development-boards/evaluation-kit-for-the-i-mx-8m-nano-applications-processor:8MNANOD4-EVK)
* Avnet: [MSC SM2S IMX8PLUS](https://embedded.avnet.com/product/msc-sm2s-imx8plus/), [MSC SM2S-IMX8M](https://embedded.avnet.com/product/msc-sm2s-imx8m/)
* Advantech: [RSB-3720](https://www.advantech.com/en/products/single_board_computer/rsb-3720/mod_d2f1b0bc-650b-449a-8ef7-b65ce4f69949), [ROM-5720](https://www.advantech.com/en/products/computer-on-module/rom-5720/mod_4fbfe9fa-f5b2-4ba8-940e-e47585ad0fef), [ROM-5722](https://www.advantech.com/en/products/computer-on-module/rom-5722/mod_11aa0c77-868e-4014-8151-ac7a7a1c5c1b)
* ASUS: [IMX8P IM A](https://www.asus.com/us/site/IOT/#!/products/single-board-computer/IMX8P-IM-A), [PE100A](https://iot.asus.com/products/intelligent-edge-computer/PE100A/)
* SECO: [Trizeps VIII Plus](https://edge.seco.com/usa/trizeps-viii-plus.html), [Trizeps VIII](https://edge.seco.com/usa/trizeps-viii.html), [Trizeps VIII Mini](https://edge.seco.com/usa/trizeps-viii-mini.html)
* Reycom: [RIA 8M](https://www.reycom.swiss/en/oem-hardware/the-ria-8m/)

#### Where can I find details about the BSP?

You can download the BSP from NXP at [aka.ms/NXPIoT](https://aka.ms/nxpiot)
