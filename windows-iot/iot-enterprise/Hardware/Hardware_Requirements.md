---
title: Windows IoT Enterprise Hardware Requirements
author: TerryWarwick
ms.author: twarwick
ms.date: 11/22/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about Hardware Requirements for Windows IoT Enterprise.
keywords: IoT Enterprise, Hardware, Windows IoT
---

# Minimum Hardware Requirements for Windows IoT Enterprise

This specification defines the minimum hardware requirements for Windows IoT Enterprise. 

## Overview

This specification defines the minimum hardware requirements necessary to:

* Boot and run Windows IoT Enterprise.
* Update and service Windows IoT Enterprise.

The goal of this specification is to enable OEMs, ODMs, SoC vendors, and other component vendors to make early design decisions for devices and computers that run Windows IoT Enterprise.

This specification doesn't provide compatibility and certification requirements for devices and computers that run Windows IoT Enterprise or implementation guidance for exceptional user experiences.

## Hardware Requirements

| Topic | Description |
| ----- | ----------- |
| Memory | Devices that run Windows IoT Enterprise must meet the following [RAM requirements](/windows-hardware/design/minimum/minimum-hardware-requirements-overview#32-memory). |
| Storage | Devices that run Windows IoT Enterprise must include a storage device that meets the following [size requirements](/windows-hardware/design/minimum/minimum-hardware-requirements-overview#331-storage-device-size).  To achieve the minimum storage requirements, review how to [Optimize a Windows IoT Enterprise image](../Optimize/iot-ent-optimize-images.md). |
| Display | Display size requirements don't apply to Windows IoT Enterprise. |
| Graphics | Devices that run Windows IoT Enterprise **and** require hardware accelerated graphics, must include a GPU that supports DirectX 9 or later. |
| Networking | It's recommended that devices that run Windows IoT Enterprise include at least one network connectivity option, such as Wi-Fi or an Ethernet adapter. |
| Trusted Platform Module (TPM) | While TPM requirements are highly encouraged for Windows 10 IoT Enterprise, it isn't required. The use of a TPM for Windows 10 IoT Enterprise devices is determined based on the usage and security requirements of each device.  For more information, see [TPM Requirements](/windows-hardware/design/minimum/minimum-hardware-requirements-overview#37-trusted-platform-module-tpm), [Trusted Platform Module Technology Overview](/windows/security/information-protection/tpm/trusted-platform-module-overview), and [TPM Recommendations](/windows/security/information-protection/tpm/tpm-recommendations) |

Recommended [hardware requirements](/windows-hardware/design/minimum/minimum-hardware-requirements-overview).

| Components | Recommended | Minimum |
| ---------- | ----------- | ------- |
| Processor  | 1 GHz, 2 Cores</br>[Supported Processors](Processor_Requirements.md) | 1 GHz, 2 Cores |
| System Memory | 4 GB | 2 GB |
| Storage | 64 GB | |
| System Firmware | UEFI | |
| TPM | TPM 2.0 | Optional |
| UEFI Secure Boot | Enabled | Optional |
| Display | | |
| Camera | | |

## Other Resources

* [Windows Minimum Hardware Requirements](/windows-hardware/design/minimum/minimum-hardware-requirements-overview)
* [Windows Processor Requirements](/windows-hardware/design/minimum/windows-processor-requirements)
* [Hardware Component Guidelines](/windows-hardware/design/component-guidelines/components)
