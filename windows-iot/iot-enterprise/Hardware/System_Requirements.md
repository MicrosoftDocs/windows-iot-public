---
title: Minimum System Requirements
titleSuffix: Windows IoT Enterprise
author: TerryWarwick
ms.author: twarwick
ms.date: 05/22/2024
ms.topic: reference
ms.service: windows-iot
ms.subservice: iot
description: Learn about the minimum system requirements for Windows IoT Enterprise.
keywords: IoT Enterprise, Hardware, Windows IoT
---

# Minimum System Requirements for Windows IoT Enterprise

## Overview

This specification defines the minimum hardware requirements necessary to:

* Boot and run Windows IoT Enterprise.
* Update and service Windows IoT Enterprise.

The goal of this specification is to enable OEMs, ODMs, SoC vendors, and other component vendors to make early design decisions for devices and computers that run Windows IoT Enterprise.

This specification doesn't provide compatibility and certification requirements for devices and computers that run Windows IoT Enterprise or implementation guidance for exceptional user experiences.

### Preferred Minimum Requirements

The Windows IoT Enterprise preferred minimum requirements match the requirements for consumer general purpose devices where optimal performance and compatibility are required. Windows IoT Enterprise based devices have some flexibility from this system requirements bar for specialized devices. You must carefully consider deviating from this bar when producing specialized devices where software can be added to the device by the end customer. As an example, not offering a TPM can affect software that the end user would require, whereas using different storage devices typically only affect read and write performance. To enable Microsoft Security best practices out of the box, please refer to [Edge Secured-core minimum requirements](/azure/certification/program-requirements-edge-secured-core?pivots=platform-windows).

### Optional Minimum Requirements

The Windows IoT Enterprise optional minimum requirements are provided for device makers to use when building a specialized device, which provides a curated "appliance like" experience. Some of these optional minimum requirements, such as a lower storage requirement, require extra monitoring and management throughout the lifecycle of the device to prevent storage from being fully consumed due to servicing or data file growth. It's important to fully validate the chosen configurations meet the needs of the specialized device for its lifetime before distribution.

<!--markdownlint-disable-next-line -->
# [Windows 11 LTSC](#tab/Windows11LTSC)

Applies to:  
✅ Windows 11 IoT Enterprise LTSC

> [!NOTE]
> Windows 11 IoT Enterprise LTSC 2024 is coming later this year.

| </br>Component    | PREFERRED</br>Minimum&nbsp;Requirements   | OPTIONAL </br> Minimum&nbsp;Requirements  |
| ---------------------- |:---------------------------------:|:---------------------------------:|
| Processor¹             | 1&nbsp;GHz,&nbsp;2 Cores          | 1&nbsp;GHz,&nbsp;2&nbsp;Cores     |
| System&nbsp;Memory     |  4 GB                             |  2 GB                             |
| Storage&nbsp;Size      | 64 GB                             | 16 GB                             |
| Storage&nbsp;Type      | Solid&#x2011;State&nbsp;Drive&nbsp;(SSD) | Solid&#x2011;State&nbsp;Drive&nbsp;(SSD) </br> Hard&nbsp;Disk&nbsp;Drive&nbsp;(HDD)</br> Hybrid&nbsp;Hard&nbsp;Drive&nbsp;(SSHD) </br> Flash&nbsp;(eMMC,&nbsp;SD,&nbsp;USB)  |
| System&nbsp;Firmware   | UEFI                              | BIOS                              |
| TPM                    | TPM 2.0                           | Optional                          |
| Secure Boot            | Enabled                           | Optional                          |
| DirectX                | DirectX 12                        | DirectX 10 / None                 |
| Display                | 9" diagonal</br>720p HD           | Custom Size / Optional            |

<!--markdownlint-disable-next-line -->
# [Windows 11 (Non-LTSC)](#tab/Windows11)

Applies to:  
✅ Windows 11 IoT Enterprise  

> [!NOTE]
> Windows 11 IoT Enterprise, version 24H2 is coming later this year.

| </br></br>Component    | </br>PREFERRED</br>Minimum&nbsp;Requirements   | 21H2,&nbsp;22H2,&nbsp;23H2 </br> OPTIONAL </br> Minimum&nbsp;Requirements  | 24H2 or Later </br> OPTIONAL </br> Minimum&nbsp;Requirements  |
| ---------------------- |:-----------------------------:|:---------------------------------:|:---------------------------------:|
| Processor¹             | 1&nbsp;GHz,&nbsp;2 Cores      | 1&nbsp;GHz,&nbsp;2&nbsp;Cores     | 1&nbsp;GHz,&nbsp;2&nbsp;Cores     |
| System&nbsp;Memory     |  4 GB                         |  4 GB                             |  4 GB                             |
| Storage&nbsp;Size      | 64 GB                         | 64 GB                             | 64 GB                             |
| Storage&nbsp;Type      | Solid&#x2011;State&nbsp;Drive&nbsp;(SSD) | Solid&#x2011;State&nbsp;Drive&nbsp;(SSD) </br> Hard&nbsp;Disk&nbsp;Drive&nbsp;(HDD)</br> Hybrid&nbsp;Hard&nbsp;Drive&nbsp;(SSHD) </br> Flash&nbsp;(eMMC,&nbsp;SD,&nbsp;USB)  | Solid&#x2011;State&nbsp;Drive&nbsp;(SSD) </br> Hard&nbsp;Disk&nbsp;Drive&nbsp;(HDD)</br> Hybrid&nbsp;Hard&nbsp;Drive&nbsp;(SSHD) </br> Flash&nbsp;(eMMC,&nbsp;SD,&nbsp;USB)  |
| System&nbsp;Firmware   | UEFI                          | UEFI                              | BIOS                              |
| TPM                    | TPM 2.0                       |TPM 2.0                            | Optional                          |
| Secure Boot            | Enabled                       | Optional                          | Optional                          |
| DirectX                | DirectX 12                    | DirectX 12                        | DirectX 10 / None                 |
| Display                | 9" diagonal</br>720p HD       | Custom Size / Optional            | Custom Size / Optional            |

<!--markdownlint-disable-next-line -->
# [Windows 10](#tab/Windows10)

Applies to:  
✅ Windows 10 IoT Enterprise  
✅ Windows 10 IoT Enterprise LTSC

| </br></br></br>Component  | </br>PREFERRED</br>Minimum&nbsp;Requirements | 64&#x2011;bit</br>OPTIONAL</br>Minimum&nbsp;Requirements | 32&#x2011;bit</br>OPTIONAL</br>Minimum&nbsp;Requirements |
|:-------------------|:------------------------------:|:-------------------------------------------:|:------------------------------:|
| Processor¹         | 1&nbsp;GHz&nbsp;or&nbsp;faster | 1&nbsp;GHz&nbsp;or&nbsp;faster              | 1&nbsp;GHz&nbsp;or&nbsp;faster |
| System&nbsp;Memory | x64: 2 GB                      | 2 GB                                        | 1 GB                           |
| Storage&nbsp;Size  | 20 GB                          | 20 GB                                       | 16 GB                          |
| TPM                | TPM 2.0                        | Optional                                    | Optional                       |
| Display            | 7" diagonal</br>800x600 SVGA   | Optional                                    | Optional                       |
| Graphics           | DirectX 9 or later             | Optional                                    | Optional                       |
| Networking         | Ethernet or Wi-Fi              | Optional                                    | Optional                       |

For more information, see [Windows 10 Minimum Hardware Requirements](https://download.microsoft.com/download/c/1/5/c150e1ca-4a55-4a7e-94c5-bfc8c2e785c5/Windows%2010%20Minimum%20Hardware%20Requirements.pdf).

---

¹ For more information, see [Windows IoT Enterprise Supported Processors](Processor_Requirements.md).

The use of a TPM for Windows 10 IoT Enterprise devices is determined based on the usage and security requirements of each device.  

For more information, see...

* [How Windows uses the Trusted Platform Module (TPM)](/windows/security/hardware-security/tpm/how-windows-uses-the-tpm)
* [TPM Requirements](/windows-hardware/design/minimum/minimum-hardware-requirements-overview#37-trusted-platform-module-tpm)
* [Trusted Platform Module Technology Overview](/windows/security/information-protection/tpm/trusted-platform-module-overview)
* [TPM Recommendations](/windows/security/information-protection/tpm/tpm-recommendations)

## Related content

* [Windows Minimum Hardware Requirements](/windows-hardware/design/minimum/minimum-hardware-requirements-overview)
* [Windows Processor Requirements](/windows-hardware/design/minimum/windows-processor-requirements)
* [Hardware Component Guidelines](/windows-hardware/design/component-guidelines/components)
