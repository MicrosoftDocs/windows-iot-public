---
title: Hardware Requirements
author: twarwick
ms.author: twarwick
ms.date: 1/15/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about what Hardware is Required for Windows IoT Enterprise.
keywords: IoT Enterprise, Hardware, Windows IoT
---

# Minimum Hardware Requirements for Windows IoT Enterprise
This specification defines the minimum hardware requirements for Windows IoT Enterprise. Microsoft will build and test the Windows IoT Enterprise OS against the requirements described in this specification.

## Overview
This specification defines the minimum hardware requirements necessary to:
* Boot and run Windows IoT Enterprise.
* Update and service Windows IoT Enterprise.

The goal of this specification is to enable OEMs, ODMs, SoC vendors, and other component vendors to make early design decisions for devices and computers that will run Windows IoT Enterprise.

This specification does not provide compatibility and certification requirements for devices and computers that run Windows IoT Enterprise or implementation guidance for exceptional user experiences.

> [!NOTE]
> Beginning with Windows 10, version 2004, all new Windows 10 systems will be required to use 64-bit builds and Microsoft will no longer release 32-bit builds for OEM distribution. This does not impact 32-bit customer systems that are manufactured with earlier versions of Windows 10; Microsoft remains committed to providing feature and security updates on these devices, including continued 32-bit media availability in non-OEM channels to support various upgrade installation scenarios.

## Processor
Devices that run Windows IoT Enterprise must meet these [hardware requirements](/windows-hardware/design/minimum/minimum-hardware-requirements-overview).

> [!TIP]
>
> Information on support is available at [Microsoft Support Policy](https://support.microsoft.com/lifecycle) and [Microsoft Lifecycle FAQ](https://support.microsoft.com/help/18581).
>
> For specific hardware support, please refer to your Original Equipment Manufacturer (OEM) provider.

### Windows IoT Enterprise Processor Lists

The processors listed in the tables below, represent the latest processor generations and models which are supported for the listed Windows IoT Enterprise Edition.

For more information, visit [Windows Processor Requirements](/windows-hardware/design/minimum/windows-processor-requirements)

<table>
    <tr>
        <th>Windows Edition</th>
        <th>AMD Processors</th>
		<th>Intel Processors</th>
        <th>Qualcomm Processors</th>
        <th>NXP Processors</th>
    </tr>
	<tr>
		<td>Windows 10 IoT Enterprise LTSB 1607</td>
		<td><a href="/windows-hardware/design/minimum/supported/windows-10-1607-supported-amd-processors"> Supported AMD Processors </a></td>
		<td><a href="/windows-hardware/design/minimum/supported/windows-10-1607-supported-intel-processors"> Supported Intel Processors </a></td>
		<td>N/A</td>
    <td>N/A</td>
	</tr>
	<tr>
		<td>Windows 10 IoT Enterprise LTSC 1809</td>
		<td><a href="/windows-hardware/design/minimum/supported/windows-10-1809-supported-amd-processors"> Supported AMD Processors </a></td>        
		<td><a href="/windows-hardware/design/minimum/supported/windows-10-LTSC-1809-supported-intel-processors"> Supported Intel Processors </a></td>
    <td>N/A</td>		
    <td>N/A</td>
	</tr>
	<tr>
		<td>Windows 10 IoT Enterprise 20H2</td>
		<td><a href="/windows-hardware/design/minimum/supported/windows-10-20H2-supported-amd-processors"> Supported AMD Processors </a></td>
		<td><a href="/windows-hardware/design/minimum/supported/windows-10-20H2-supported-intel-processors"> Supported Intel Processors </a></td>
    <td><a href="/windows-hardware/design/minimum/supported/windows-10-20H2-supported-qualcomm-processors"> Supported Qualcomm Processors </a></td>
    <td>N/A</td>
	</tr>
	<tr>
		<td>Windows 10 IoT Enterprise 21H1</td>
		<td><a href="/windows-hardware/design/minimum/supported/windows-10-21H1-supported-amd-processors"> Supported AMD Processors </a></td>
		<td><a href="/windows-hardware/design/minimum/supported/windows-10-21H1-supported-intel-processors"> Supported Intel Processors </a></td>
		<td><a href="/windows-hardware/design/minimum/supported/windows-10-21H1-supported-qualcomm-processors"> Supported Qualcomm Processors </a></td>
    <td>N/A</td>
	</tr>
    <tr>
		<td>Windows 10 IoT Enterprise 21H2</td>
		<td><a href="/windows-hardware/design/minimum/supported/windows-10-21H2-supported-amd-processors"> Supported AMD Processors </a></td>
		<td><a href="/windows-hardware/design/minimum/supported/windows-10-21H2-supported-intel-processors"> Supported Intel Processors </a></td>
		<td><a href="/windows-hardware/design/minimum/supported/windows-10-21H2-supported-qualcomm-processors"> Supported Qualcomm Processors </a></td>
    <td><a href="supported/21H2_NXP_Processors.md"> Supported NXP Processors </a></td>
	</tr>
    <tr>
		<td>Windows 10 IoT Enterprise LTSC 2021</td>
		<td><a href="/windows-hardware/design/minimum/supported/windows-10-LTSC-2021-supported-amd-processors"> Supported AMD Processors </a></td>
		<td><a href="/windows-hardware/design/minimum/supported/windows-10-LTSC-2021-supported-intel-processors"> Supported Intel Processors </a></td>
		<td>N/A</td>
    <td><a href="supported\21H2_LTSC_NXP_Processors.md"> Supported NXP Processors </a></td>
	</tr>
    <tr>
        <td>Windows 11 IoT Enterprise</td>
        <td><a href="/windows-hardware/design/minimum/supported/windows-11-supported-amd-processors"> Supported AMD Processors </a></td>
        <td><a href="/windows-hardware/design/minimum/supported/windows-11-supported-intel-processors"> Supported Intel Processors </a></td>
        <td><a href="/windows-hardware/design/minimum/supported/windows-11-supported-qualcomm-processors"> Supported Qualcomm Processors </a></td>
        <td>N/A</td>
    </tr>
</table>           

## Memory
Devices that run Windows IoT Enterprise must meet the following [RAM requirements](/windows-hardware/design/minimum/minimum-hardware-requirements-overview#32-memory).

## Storage
### Storage device size
Devices that run Windows IoT Enterprise must include a storage device that meets the following [size requirements](/windows-hardware/design/minimum/minimum-hardware-requirements-overview#331-storage-device-size).

> [!TIP]
>
> To achieve the minimum storage requirements, review how to [optimize a Windows IoT Enterprise image](/windows-hardware/manufacture/desktop/iot-ent-optimize-images).

## Display and graphics
### Resolution, bit depth, and size
Display size requirements do not apply to Windows IoT Enterprise.

### Graphics
Devices that run Windows IoT Enterprise **and** require hardware accelerated graphics, must include a GPU that supports DirectX 9 or later.

### Networking
It is recommended that devices that run Windows IoT Enterprise include at least one network connectivity option, such as Wi-Fi or an Ethernet adapter.

## Trusted Platform Module (TPM)
> [!NOTE]
>
> While TPM requirements are highly encouraged for Windows 10 IoT Enterprise, it is not required. The use of a TPM for Windows 10 IoT Enterprise devices is determined based on the usage and security requirements of each device.

* [TPM Requirements](/windows-hardware/design/minimum/minimum-hardware-requirements-overview#37-trusted-platform-module-tpm)
* [Trusted Platform Module Technology Overview](/windows/security/information-protection/tpm/trusted-platform-module-overview)
* [TPM Recommendations](/windows/security/information-protection/tpm/tpm-recommendations)

## Additional Resources
* [Shared Minimum Hardware Requirements for Windows OS](/windows-hardware/design/minimum/minimum-hardware-requirements-overview#section-60---shared-minimum-hardware-requirements-for-components)
* [Minimum Hardware Requirements](/windows-hardware/design/minimum/minimum-hardware-requirements-overview)
* [Windows Processor Requirements](/Processor_Requirements.md)
* [Hardware Component Guidelines](/windows-hardware/design/component-guidelines/components)
