---
title: Building Arm Images
author: anthonychen
ms.author: anthonychen
ms.date: 6/7/2024
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Building Windows IoT on ARM64 Images
keywords: IoT Enterprise, Hardware, Windows IoT, Arm64, NXP
---

To get started evaluating Windows IoT Enterprise on an Arm64 SoC, you will need three things:

1. A hardware platform with a supported ARM64 processor

2. A Windows IoT Board Support Package (BSP) for the hardware platform

3. An ARM64 build of a Windows IoT Enterprise OS

### 1. ARM64 Hardware Platforms

### 2. Board Support Package (BSP)
A Board Support Package (BSP) is made up of all platform-specific components needed for Windows IoT Enterprise to run on a particular hardware platform. For Windows IoT Enterprise, this includes bootloaders, the UEFI environment, the ACPI tables that describes the platform's hardware to Windows, and the Windows drivers for the platform.

You can get the BSP for Evaluation Kits and Development Kits from the Processor Vendor (e.g. Qualcomm or NXP). For all other form factors, you can get the BSP from the platform manufacturer.

### 3. Windows IoT Enterprise OS for ARM64