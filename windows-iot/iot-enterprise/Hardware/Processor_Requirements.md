---
title: Windows IoT Enterprise Processor Requirements
author: TerryWarwick
ms.author: twarwick
ms.date: 07/05/2023
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Learn about Processor Requirements for Windows IoT Enterprise.
keywords: IoT Enterprise, Hardware, Windows IoT
---

# Processor Requirements for Windows IoT Enterprise

> [!WARNING]
> THIS IS AN IN-PROGRESS ROUGH DRAFT. The wording and feature list may change before publishing.

This specification defines the minimum hardware requirements for Windows IoT Enterprise. Microsoft will build and test the Windows IoT Enterprise OS against the requirements described in this specification.

## Overview

This specification defines the minimum hardware requirements necessary to:

* Boot and run Windows IoT Enterprise.
* Update and service Windows IoT Enterprise.

The goal of this specification is to enable OEMs, ODMs, SoC vendors, and other component vendors to make early design decisions for devices and computers that run Windows IoT Enterprise.

This specification doesn't provide compatibility and certification requirements for devices and computers that run Windows IoT Enterprise or implementation guidance for exceptional user experiences.

> [!NOTE]
> Beginning with Windows 10, version 2004, all new Windows 10 systems will be required to use 64-bit builds and Microsoft will no longer release 32-bit builds for OEM distribution. This does not impact 32-bit customer systems that are manufactured with earlier versions of Windows 10; Microsoft remains committed to providing feature and security updates on these devices, including continued 32-bit media availability in non-OEM channels to support various upgrade installation scenarios.

## Processor Requirements

Devices that run Windows IoT Enterprise must meet these [system requirements](./System_Requirements.md).

> [!TIP]
>
> Information on support is available at [Microsoft Support Policy](https://support.microsoft.com/lifecycle) and [Microsoft Lifecycle FAQ](https://support.microsoft.com/help/18581).
>
> For specific hardware support, please refer to your Original Equipment Manufacturer (OEM) provider.

### Windows IoT Enterprise Processor Lists

The processors listed here represent the latest processor generations and models that are supported for the listed Windows IoT Enterprise Edition.

For more information, visit [Windows Processor Requirements](/windows-hardware/design/minimum/windows-processor-requirements)

### Windows IoT Enterprise LTSC

| Version | AMD | Intel | Qualcomm | NXP |
| --------------- | --- | ----- | -------- | --- |
| Windows&nbsp;11&nbsp;IoT&nbsp;Enterprise&nbsp;LTSC&nbsp;2024 | [Supported AMD Processors](supported/Win11_LTSC_2024_AMD_Processors.md) | [Supported Intel Processors](supported/Win11_LTSC_2024_Intel_Processors.md) | [Supported Qualcomm Processors](supported/Win11_LTSC_2024_Qualcomm_Processors.md) | [Supported NXP Processors](supported/Win11_LTSC_2024_NXP_Processors.md)|
| Windows&nbsp;10&nbsp;IoT&nbsp;Enterprise&nbsp;LTSC&nbsp;2021 | [Supported AMD Processors](/windows-hardware/design/minimum/supported/windows-10-LTSC-2021-supported-amd-processors) | [Supported Intel Processors](/windows-hardware/design/minimum/supported/windows-10-LTSC-2021-supported-intel-processors) | N/A | [Supported NXP Processors](supported\21H2_LTSC_NXP_Processors.md) |
| Windows&nbsp;10&nbsp;IoT&nbsp;Enterprise&nbsp;LTSC&nbsp;1809 | [Supported AMD Processors](/windows-hardware/design/minimum/supported/windows-10-ltsc-1809-supported-amd-processors) | [Supported Intel Processors](/windows-hardware/design/minimum/supported/windows-10-LTSC-1809-supported-intel-processors) | N/A | N/A |
| Windows&nbsp;10&nbsp;IoT&nbsp;Enterprise&nbsp;LTSB&nbsp;1607 | [Supported AMD Processors](/windows-hardware/design/minimum/supported/windows-10-ltsb-1607-supported-amd-processors) | [Supported Intel Processors](/windows-hardware/design/minimum/supported/windows-10-ltsb-1607-supported-intel-processors) | N/A | N/A |

### Windows 11 IoT Enterprise

| Version | AMD | Intel | Qualcomm | NXP |
| --------------- | --- | ----- | -------- | --- |
| Windows&nbsp;11&nbsp;IoT&nbsp;Enterprise,&nbsp;version&nbsp;22H2 | [Supported AMD Processors](/windows-hardware/design/minimum/supported/windows-11-22h2-supported-amd-processors) | [Supported Intel Processors](/windows-hardware/design/minimum/supported/windows-11-22h2-supported-intel-processors) | [Supported Qualcomm Processors](/windows-hardware/design/minimum/supported/windows-11-22h2-supported-qualcomm-processors) | N/A |
| Windows&nbsp;11&nbsp;IoT&nbsp;Enterprise,&nbsp;version&nbsp;21H2| [Supported AMD Processors](/windows-hardware/design/minimum/supported/windows-11-supported-amd-processors) | [Supported Intel Processors](/windows-hardware/design/minimum/supported/windows-11-supported-intel-processors) | [Supported Qualcomm Processors](/windows-hardware/design/minimum/supported/windows-11-supported-qualcomm-processors) | N/A |

### Windows 10 IoT Enterprise

| Version | AMD | Intel | Qualcomm | NXP |
| --------------- | --- | ----- | -------- | --- |
| Windows&nbsp;10&nbsp;IoT&nbsp;Enterprise,&nbsp;version&nbsp;22H2 | [Supported AMD Processors](/windows-hardware/design/minimum/supported/windows-10-22H2-supported-amd-processors) | [Supported Intel Processors](/windows-hardware/design/minimum/supported/windows-10-22H2-supported-intel-processors) | [Supported Qualcomm Processors](/windows-hardware/design/minimum/supported/windows-10-22H2-supported-qualcomm-processors) | [Supported NXP Processors](supported/22H2_NXP_Processors.md) |
| Windows&nbsp;10&nbsp;IoT&nbsp;Enterprise,&nbsp;version&nbsp;21H2 | [Supported AMD Processors](/windows-hardware/design/minimum/supported/windows-10-21H2-supported-amd-processors) | [Supported Intel Processors](/windows-hardware/design/minimum/supported/windows-10-21H2-supported-intel-processors) | [Supported Qualcomm Processors](/windows-hardware/design/minimum/supported/windows-10-21H2-supported-qualcomm-processors) | [Supported NXP Processors](supported/21H2_NXP_Processors.md) |
| Windows&nbsp;10&nbsp;IoT&nbsp;Enterprise,&nbsp;version&nbsp;21H1 | [Supported AMD Processors](/windows-hardware/design/minimum/supported/windows-10-21H1-supported-amd-processors) | [Supported Intel Processors](/windows-hardware/design/minimum/supported/windows-10-21H1-supported-intel-processors) | [Supported Qualcomm Processors](/windows-hardware/design/minimum/supported/windows-10-21H1-supported-qualcomm-processors) | N/A |
| Windows&nbsp;10&nbsp;IoT&nbsp;Enterprise,&nbsp;version&nbsp;20H2 | [Supported AMD Processors](/windows-hardware/design/minimum/supported/windows-10-20H2-supported-amd-processors) | [Supported Intel Processors](/windows-hardware/design/minimum/supported/windows-10-20H2-supported-intel-processors) | [Supported Qualcomm Processors](/windows-hardware/design/minimum/supported/windows-10-20H2-supported-qualcomm-processors) | N/A |

## Other Resources

* [Windows Minimum Hardware Requirements](/windows-hardware/design/minimum/minimum-hardware-requirements-overview)
* [Windows Processor Requirements](/windows-hardware/design/minimum/windows-processor-requirements)
* [Hardware Component Guidelines](/windows-hardware/design/component-guidelines/components)
