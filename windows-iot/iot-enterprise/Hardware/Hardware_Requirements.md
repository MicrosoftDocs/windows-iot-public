---
title: Windows IoT Enterprise Hardware Requirements
author: TerryWarwick
ms.author: twarwick
ms.date: 04/28/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about Hardware Requirements for Windows IoT Enterprise.
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
