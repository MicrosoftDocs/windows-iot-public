---
title: Hardware Requirements
titleSuffix: Windows IoT Enterprise
author: TerryWarwick
ms.author: twarwick
ms.date: 02/06/2024
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Learn about what Hardware is Required for Windows IoT Enterprise.
keywords: IoT Enterprise, Hardware, Windows IoT
---

# Minimum Hardware Requirements for Windows IoT Enterprise

This specification defines the minimum hardware requirements for Windows IoT Enterprise. Microsoft will build and test the Windows IoT Enterprise OS against the requirements described in this specification.

## Overview

This specification defines the minimum hardware requirements necessary to:

* Boot and run Windows IoT Enterprise.
* Update and service Windows IoT Enterprise.

The goal of this specification is to enable OEMs, ODMs, SoC vendors, and other component vendors to make early design decisions for devices and computers that run Windows IoT Enterprise.

This specification doesn't provide compatibility and certification requirements for devices and computers that run Windows IoT Enterprise or implementation guidance for exceptional user experiences.

## Hardware Requirements

Recommended [hardware requirements](/windows-hardware/design/minimum/minimum-hardware-requirements-overview).

| Components        | Recommended               | Minimum¹</br>IoT&nbsp;Enterprise | Minimum¹</br>IoT&nbsp;Enterprise&nbsp;LTSC |
| ----------------- |:-------------------------:|:-------------------------------:|:-----------------------------------------:|
| Processor²         | 1&nbsp;GHz,&nbsp;2 Cores  | 1&nbsp;GHz,&nbsp;2&nbsp;Cores   | 1&nbsp;GHz,&nbsp;2&nbsp;Cores             |
| System Memory     |  4 GB                     |  4 GB                           |  2 GB                                     |
| Storage Size      | 64 GB                     | 64 GB                           | 16 GB                                     |
| Storage Type      | Solid-State&nbsp;Drive&nbsp;(SSD)   | Hard&nbsp;Disk&nbsp;Drive&nbsp;(HDD)</br> Hybrid&nbsp;Hard&nbsp;Drive&nbsp;(SSHD) </br> Flash&nbsp;(eMMC,&nbsp;SD,&nbsp;USB)  |  Hard&nbsp;Disk&nbsp;Drive&nbsp;(HDD)</br> Hybrid&nbsp;Hard&nbsp;Drive&nbsp;(SSHD) </br> Flash&nbsp;(eMMC,&nbsp;SD,&nbsp;USB)  |
| System Firmware   | UEFI                      | BIOS                            | BIOS                                      |
| TPM               | TPM 2.0                   | Optional                        | Optional                                  |
| Secure Boot       | Enabled                   | Optional                        | Optional                                  |
| DirectX           | DirectX 12                | DirectX 10 / None               | DirectX 10 / None                         |
| Display           | 9" diagonal</br>720p HD   | Custome Size / Optional         | Custom Size / Optional                    |

¹ Applies to Windows 11 IoT Enterprise LTSC 2024 and Windows 11 IoT Enterprise, Version 24H2 (build XXXXX) and later.
² For more information, see [Windows IoT Enterprise Supported Processors](Processor_Requirements.md)

## Hardware Component Guidelines

| Topic | Description |
| ----- | ----------- |
| Memory | Devices that run Windows IoT Enterprise must meet the following [RAM requirements](/windows-hardware/design/minimum/minimum-hardware-requirements-overview#32-memory). |
| Storage | Devices that run Windows IoT Enterprise must include a storage device that meets the following [size requirements](/windows-hardware/design/minimum/minimum-hardware-requirements-overview#331-storage-device-size).  To achieve the minimum storage requirements, review how to [Optimize a Windows IoT Enterprise image](../Optimize/overview.md). |
| Display | Display size requirements don't apply to Windows IoT Enterprise. |
| Graphics | Devices that run Windows IoT Enterprise **and** require hardware accelerated graphics, must include a GPU that supports DirectX 9 or later. |
| Networking | It's recommended that devices that run Windows IoT Enterprise include at least one network connectivity option, such as Wi-Fi or an Ethernet adapter. |
| Trusted Platform Module (TPM) | While TPM requirements are highly encouraged for Windows 10 IoT Enterprise, it isn't required. The use of a TPM for Windows 10 IoT Enterprise devices is determined based on the usage and security requirements of each device.  For more information, see [TPM Requirements](/windows-hardware/design/minimum/minimum-hardware-requirements-overview#37-trusted-platform-module-tpm), [Trusted Platform Module Technology Overview](/windows/security/information-protection/tpm/trusted-platform-module-overview), and [TPM Recommendations](/windows/security/information-protection/tpm/tpm-recommendations) |

## Other Resources

* [Windows Minimum Hardware Requirements](/windows-hardware/design/minimum/minimum-hardware-requirements-overview)
* [Windows Processor Requirements](/windows-hardware/design/minimum/windows-processor-requirements)
* [Hardware Component Guidelines](/windows-hardware/design/component-guidelines/components)
