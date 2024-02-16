---
title: Minimum System Requirements
titleSuffix: Windows IoT Enterprise
author: TerryWarwick
ms.author: twarwick
ms.date: 02/15/2024
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Learn about the minimum system requirements for Windows IoT Enterprise.
keywords: IoT Enterprise, Hardware, Windows IoT
---

# Minimum System Requirements for Windows IoT Enterprise

> [!WARNING]
> THIS IS AN IN-PROGRESS ROUGH DRAFT. The wording and feature list may change before publishing.

**Recommended Minimum Requirements**

Enter details about recommended requirements here

**Optional Minimum Requirements**

Enter details about minimum requirements here

# [Windows 11 LTSC](#tab/Windows11LTSC)
Applies to:  
⛔ Windows 11 IoT Enterprise  
✅ Windows 11 IoT Enterprise LTSC  

| </br></br>Component    | </br>RECOMMENDED</br>Minimum</br>Requirements   | OPTIONAL </br> Minimum </br>Requirements  |
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

# [Windows 11 (Non-LTSC)](#tab/Windows11)

Applies to:  
✅ Windows 11 IoT Enterprise  
⛔ Windows 11 IoT Enterprise LTSC  

| </br></br>Component    | </br>RECOMMENDED</br>Minimum</br>Requirements   | 21H2,&nbsp;22H2,&nbsp;23H2 </br> OPTIONAL </br> Minimum </br>Requirements  | 24H2 or Later </br> OPTIONAL </br> Minimum </br> Requirements  |
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

# [Windows 10](#tab/Windows10)

Applies to:  
✅ Windows 10 IoT Enterprise  
✅ Windows 10 IoT Enterprise LTSC

| </br></br></br>Component  | </br>RECOMMENDED</br>Minimum</br>Requirements | 64&#x2011;bit</br>OPTIONAL</br>Minimum</br>Requirements | 32&#x2011;bit</br>OPTIONAL</br>Minimum</br>Requirements |
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

- [How Windows uses the Trusted Platform Module (TPM)](/windows/security/hardware-security/tpm/how-windows-uses-the-tpm)
- [TPM Requirements](/windows-hardware/design/minimum/minimum-hardware-requirements-overview#37-trusted-platform-module-tpm)
- [Trusted Platform Module Technology Overview](/windows/security/information-protection/tpm/trusted-platform-module-overview)
- [TPM Recommendations](/windows/security/information-protection/tpm/tpm-recommendations)

## Other Resources

- [Windows Minimum Hardware Requirements](/windows-hardware/design/minimum/minimum-hardware-requirements-overview)
- [Windows Processor Requirements](/windows-hardware/design/minimum/windows-processor-requirements)
- [Hardware Component Guidelines](/windows-hardware/design/component-guidelines/components)
