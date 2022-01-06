---
title: Hardware Requirements
author: rsameser
ms.author: riameser
ms.date: 10/05/2021
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
Devices that run Windows IoT Enterprise must meet these [processor requirements](/windows-hardware/design/minimum/minimum-hardware-requirements-overview#31-processor). Check out the [processor matrix](/windows-hardware/design/minimum/windows-processor-requirements#windows-iot-enterprise--embedded-processors) to review the latest processor generations and models that are supported. Previous generations of processors and models (indicated by "Up through"), remain supported in addition to the listed processors and models.

> [!TIP]
>
> Information on support is available at [Microsoft Support Policy](https://support.microsoft.com/lifecycle) and [Microsoft Lifecycle FAQ](https://support.microsoft.com/help/18581).
>
> For specific hardware support, please refer to your Original Equipment Manufacturer (OEM) provider.

### Windows 11 IoT Enterprise Processor Lists
* [Intel](/windows-hardware/design/minimum/supported/windows-11-supported-intel-processors)
* [Qualcomm](/windows-hardware/design/minimum/supported/windows-11-supported-qualcomm-processors)
* [AMD](/windows-hardware/design/minimum/supported/windows-11-supported-amd-processors)


## Memory
Devices that run Windows IoT Enterprise must meet the following [RAM requirements](/windows-hardware/design/minimum/minimum-hardware-requirements-overview#32-memory).

## Storage
### Storage device size
Devices that run Windows IoT Enterprise must include a storage device that meets the following [size requirements](/windows-hardware/design/minimum/minimum-hardware-requirements-overview#331-storage-device-size).

> ![TIP]
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
* [Windows Processor Requirements](/windows-hardware/design/minimum/windows-processor-requirements)
* [Hardware Component Guidelines](/windows-hardware/design/component-guidelines/components)
