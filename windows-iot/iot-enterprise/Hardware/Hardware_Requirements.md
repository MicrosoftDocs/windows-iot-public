---
title: Hardware Requirements
titleSuffix: Windows IoT Enterprise
author: TerryWarwick
ms.author: twarwick
ms.date: 02/12/2024
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Learn about what Hardware is Required for Windows IoT Enterprise.
keywords: IoT Enterprise, Hardware, Windows IoT
---

# Minimum Hardware Requirements for Windows IoT Enterprise

> [!WARNING]
> THIS IS AN IN-PROGRESS ROUGH DRAFT. The wording and feature list may change before publishing.

# [Windows 11 IoT Enterprise LTSC 2024](#tab/LTSC2024)

| Components        | Recommended                       | Minimum¹</br>IoT&nbsp;Enterprise&nbsp;LTSC |
| ----------------- |:---------------------------------:|:------------------------------------------:|
| Processor²        | 1&nbsp;GHz,&nbsp;2 Cores          | 1&nbsp;GHz,&nbsp;2&nbsp;Cores              |
| System Memory     |  4 GB                             |  2 GB                                      |
| Storage Size      | 64 GB                             | 16 GB                                      |
| Storage Type      | Solid-State&nbsp;Drive&nbsp;(SSD) |  Hard&nbsp;Disk&nbsp;Drive&nbsp;(HDD)</br> Hybrid&nbsp;Hard&nbsp;Drive&nbsp;(SSHD) </br> Flash&nbsp;(eMMC,&nbsp;SD,&nbsp;USB)  |
| System Firmware   | UEFI                              | BIOS                                       |
| TPM               | TPM 2.0                           | Optional                                   |
| Secure Boot       | Enabled                           | Optional                                   |
| DirectX           | DirectX 12                        | DirectX 10 / None                          |
| Display           | 9" diagonal</br>720p HD           | Custome Size / Optional                    |

¹ Applies to Windows 11 IoT Enterprise LTSC 2024 (build XXXXX)
² For more information, see [Windows IoT Enterprise Supported Processors](Processor_Requirements.md)

# [Windows 11 IoT Enterprise, version 24H2 or later](#tab/win1124h2)

| Components        | Recommended               | Minimum¹</br>IoT&nbsp;Enterprise |
| ----------------- |:-------------------------:|:--------------------------------:|
| Processor²         | 1&nbsp;GHz,&nbsp;2 Cores  | 1&nbsp;GHz,&nbsp;2&nbsp;Cores   |
| System Memory     |  4 GB                     |  4 GB                            |
| Storage Size      | 64 GB                     | 64 GB                            |
| Storage Type      | Solid-State&nbsp;Drive&nbsp;(SSD)   | Hard&nbsp;Disk&nbsp;Drive&nbsp;(HDD)</br> Hybrid&nbsp;Hard&nbsp;Drive&nbsp;(SSHD) </br> Flash&nbsp;(eMMC,&nbsp;SD,&nbsp;USB)  |
| System Firmware   | UEFI                      | BIOS                             |
| TPM               | TPM 2.0                   | Optional                         |
| Secure Boot       | Enabled                   | Optional                         |
| DirectX           | DirectX 12                | DirectX 10 / None                |
| Display           | 9" diagonal</br>720p HD   | Custome Size / Optional          |

¹ Applies to Windows 11 IoT Enterprise, Version 24H2 (build XXXXX) and later.
² For more information, see [Windows IoT Enterprise Supported Processors](Processor_Requirements.md)

# [Windows 11 IoT Enterprise, versions 21H2, 22H2, 23H2](#tab/win1121H2to23H2)

| Components        | Recommended                         | Minimum</br>IoT&nbsp;Enterprise  |
| ----------------- |:-----------------------------------:|:--------------------------------:|
| Processor²        | 1&nbsp;GHz,&nbsp;2 Cores            | 1&nbsp;GHz,&nbsp;2&nbsp;Cores    |
| System Memory     |  4 GB                               |  4 GB                            |
| Storage Size      | 64 GB                               | 64 GB                            |
| Storage Type      | Solid-State&nbsp;Drive&nbsp;(SSD)   | Hard&nbsp;Disk&nbsp;Drive&nbsp;(HDD)</br> Hybrid&nbsp;Hard&nbsp;Drive&nbsp;(SSHD) </br> Flash&nbsp;(eMMC,&nbsp;SD,&nbsp;USB)  |
| System Firmware   | UEFI                                | UEFI                             |
| TPM               | TPM 2.0                             | TPM 2.0                          |
| Secure Boot       | Enabled                             | Optional                         |
| DirectX           | DirectX 12                          | DirectX 12                       |
| Display           | 9" diagonal</br>720p HD             | Custome Size / Optional          |

² For more information, see [Windows IoT Enterprise Supported Processors](Processor_Requirements.md)

# [Windows 10 IoT Enterprise (All versions)](#tab/win10)

| Topic         | Recommended                    | Minimum</br>64-bit&nbsp;IoT&nbsp;Enterprise | Minimum</br>32-bit&nbsp;IoT&nbsp;Enterprise |
|:--------------|:------------------------------:|:-------------------------------------------:|:------------------------------:|
| Processor²    | 1&nbsp;GHz&nbsp;or&nbsp;faster | 1&nbsp;GHz&nbsp;or&nbsp;faster              | 1&nbsp;GHz&nbsp;or&nbsp;faster |
| System Memory | x64: 2 GB                      | 2 GB                                        | 1 GB                           |
| Storage Size  | 20 GB                          | 20 GB                                       | 16 GB                          |
| TPM           | TPM 2.0                        | Optional                                    | Optional                       |
| Display       | 7" diagonal</br>800x600 SVGA   | Optional                                    | Optional                       |
| Graphics      | DirectX 9 or later             | Optional                                    | Optional                       |
| Networking    | Ethernet or Wi-Fi              | Optional                                    | Optional                       |

² For more information, see [Windows IoT Enterprise Supported Processors](Processor_Requirements.md)

For more information, see [Windows 10 Minimum Hardware Requirements](https://download.microsoft.com/download/c/1/5/c150e1ca-4a55-4a7e-94c5-bfc8c2e785c5/Windows%2010%20Minimum%20Hardware%20Requirements.pdf)

The use of a TPM for Windows 10 IoT Enterprise devices is determined based on the usage and security requirements of each device.  

For more information, see...

- [TPM Requirements](/windows-hardware/design/minimum/minimum-hardware-requirements-overview#37-trusted-platform-module-tpm)
- [Trusted Platform Module Technology Overview](/windows/security/information-protection/tpm/trusted-platform-module-overview)
- [TPM Recommendations](/windows/security/information-protection/tpm/tpm-recommendations)

---

## Other Resources

* [Windows Minimum Hardware Requirements](/windows-hardware/design/minimum/minimum-hardware-requirements-overview)
* [Windows Processor Requirements](/windows-hardware/design/minimum/windows-processor-requirements)
* [Hardware Component Guidelines](/windows-hardware/design/component-guidelines/components)
