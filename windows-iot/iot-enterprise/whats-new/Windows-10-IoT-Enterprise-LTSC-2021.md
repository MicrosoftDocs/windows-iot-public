---
title: What's new in Windows 10 IoT Enterprise LTSC 2021
description: New features in Windows 10 IoT Enterprise LTSC 2021.
ms.service: windows-iot
author: TerryWarwick
ms.author: twarwick
ms.topic: whats-new
ms.subservice: iot
ms.date: 05/22/2024
---

# What's new in Windows 10 IoT Enterprise LTSC 2021

## Overview

This article lists new and updated features that are of interest to device makers and IT Pros working with Windows 10 IoT Enterprise LTSC 2021, compared to Windows 10 IoT Enterprise LTSC 2019. Windows 10 IoT Enterprise LTSC will continue to offer a 10-year support lifecycle.

This article lists new and updated features and content that is of interest to IT Pros for Windows 10 Enterprise LTSC 2021, compared to Windows 10 Enterprise LTSC 2019 (LTSB). For a brief description of the LTSC servicing channel and associated support, see [Windows IoT Enterprise LTSC](Windows-IoT-Enterprise-LTSC.md).

> [!NOTE]
> Features in Windows 10 Enterprise LTSC 2021 are equivalent to Windows 10, version 21H2.
> The LTSC release is [intended for special use devices](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/LTSC-What-is-it-and-when-should-it-be-used/ba-p/293181). Support for LTSC by apps and tools that are designed for the General Availability Channel release of Windows 10 might be limited.

Windows 10 Enterprise LTSC 2021 builds on Windows 10 Enterprise LTSC 2019, adding premium features such as advanced protection against modern security threats and comprehensive device management, app management, and control capabilities.

## Lifecycle

Windows 10 IoT Enterprise LTSC 2021 follows the [Fixed Lifecycle Policy](/lifecycle/policies/fixed).

| Version | Build  | Availability | End of Servicing |
| --- | --- | --- | --- |
| Windows&nbsp;10&nbsp;IoT&nbsp;Enterprise,&nbsp;version&nbsp;2021 | 19044 | 2021-11-16 | 2032-01-13 |

For more information, see [Windows 10 IoT Enterprise LTSC 2021 support lifecycle](/lifecycle/products/windows-10-iot-enterprise-ltsc-2021).

## Availability

Windows 10 IoT Enterprise LTSC 2021 is available for Windows IoT Enterprise device makers through an authorized [Windows IoT Distributor](https://aka.ms/IoTDistributorList) for building new devices.  This release requires a new license.

## What's New

Windows 10 IoT Enterprise LTSC 2021 release includes the cumulative enhancements provided by the following semi-annual / annual releases since Windows 10 IoT Enterprise LTSC 2019:

- [Windows 10 IoT Enterprise, version 21H2](Windows-10-IoT-Enterprise-21H2.md)
- [Windows 10 IoT Enterprise, version 21H1](Windows-10-IoT-Enterprise-21H1.md)
- Windows 10 IoT Enterprise, version 20H2
- Windows 10 IoT Enterprise, version 2004
- Windows 10 IoT Enterprise, version 1909
- Windows 10 IoT Enterprise, version 1903

### Applications

| Feature | Description |
| ------- | ----------- |
| **Microsoft Edge** | Microsoft Edge Browser is now included in-box as the default browser. Microsoft Edge kiosk mode offers two lockdown experiences of the browser so organizations can create, manage, and provide the best experience for their customers. The *Digital/Interactive Signage experience* displays a specific site in full-screen mode. The *Public-Browsing experience* runs a limited multi-tab version of Microsoft Edge. Both experiences are running a Microsoft Edge InPrivate session, which protects user data. For more information, see [Configure Microsoft Edge kiosk mode](/deployedge/microsoft-edge-configure-kiosk-mode). |
| **Soft Real-Time** | Introducing [Soft-Real Time](/windows/iot/iot-enterprise/soft-real-time/soft-real-time), a new feature exclusive to Windows IoT Enterprise allows device makers to introduce soft real-time capabilities on their devices. |

### Deployment

| Feature | Description |
| ------- | ----------- |
| **Removable Packages** | Introducing [Removable Packages](../Optimize/Removable-Packages.md), a new feature exclusive to Windows IoT Enterprise LTSC allows a device administrator to reduce the operating system storage footprint. |
| **SetupDiag** | SetupDiag is a command-line tool that can help diagnose why a Windows 10 update failed. SetupDiag works by searching Windows Setup log files. When log files are being searched, SetupDiag uses a set of rules to match known issues. In the current version of SetupDiag there are 53 rules contained in the rules.xml file, which is extracted when SetupDiag is run. The rules.xml file will be updated as new versions of SetupDiag are made available. For more information, see [SetupDiag](/windows/deployment/upgrade/setupdiag).|
| **Reserved Storage** | Reserved storage sets aside disk space to be used by updates, apps, temporary files, and system caches. It improves the day-to-day function of your PC by ensuring critical OS functions always have access to disk space. On Windows 10 IoT Enterprise LTSC 2021, reserved storage is disabled by default, and can be configured using [DISM Reserved Storage Command-line](/windows-hardware/manufacture/desktop/dism-storage-reserve). For more information, see [Reserved storage](https://techcommunity.microsoft.com/t5/Storage-at-Microsoft/Windows-10-and-reserved-storage/ba-p/428327). |
| **Windows Assessment and Deployment Toolkit (ADK)** | A new [Windows ADK](/windows-hardware/get-started/adk-install) is available for Windows 11 that also supports Windows 10 IoT Enterprise LTSC 2021. |

### Identity and privacy

| Feature | Description |
| ------- | ----------- |
| **Credential Guard** | [Credential Guard](/windows/security/identity-protection/credential-guard/credential-guard) is now available for ARM64 devices, for extra protection against credential theft for ARM64 devices. |
| **Microphone privacy settings** | [Microphone privacy settings](https://support.microsoft.com/windows/windows-camera-microphone-and-privacy-a83257bc-e990-d54a-d212-b5e41beba857): A microphone icon appears in the notification area letting you see which apps are using your microphone. |

### Management

| Feature | Description |
| ------- | ----------- |
| **Microsoft Intune** | [Update rings](/mem/intune/protect/windows-10-update-rings) policy on Windows 10 IoT Enterprise LTSC 2021 is a collection of settings that configures when quality updates get installed. A new remote action to [collect diagnostics](/mem/intune/remote-actions/collect-diagnostics) from managed devices without interrupting or waiting for the device operator. Intune has also added capabilities to [Role-based access control](/mem/intune/fundamentals/role-based-access-control) (RBAC) that can be used to further define profile settings for the [Enrollment Status Page (ESP)](/mem/intune/enrollment/windows-enrollment-status). For more information, see [What's new in Microsoft Intune](/mem/intune/fundamentals/whats-new). |
| **MDM Policy** | Mobile Device Management (MDM) policy is extended with new [Local Users and Groups settings](/windows/client-management/mdm/policy-csp-localusersandgroups) that match the options available for devices managed through Group Policy. For more information about what's new in MDM, see [What's new in mobile device enrollment and management](/windows/client-management/mdm/new-in-windows-mdm-enrollment-management)|
| **WMI Group Policy Service** | Windows Management Instrumentation (WMI) Group Policy Service (GPSVC) has a performance improvement in the propagation of changes made by an Active Direcory (AD) administrator to user or computer group memberships. to support remote work scenarios. |
| **Key-rolling and Key-rotation** | This release includes two new features called key-rolling and key-rotation enables secure rolling of recovery passwords on MDM-managed Microsoft Entra ID devices on demand from Microsoft Intune/MDM tools or when a recovery password is used to unlock the BitLocker protected drive. This feature will help prevent accidental recovery password disclosure as part of manual BitLocker drive unlock by users. For more information, see [Using BitLocker recovery keys with Microsoft Endpoint Manager - Microsoft Intune](https://techcommunity.microsoft.com/t5/intune-customer-success/using-bitlocker-recovery-keys-with-microsoft-endpoint-manager/ba-p/2255517) |

### Networking

| Feature | Description |
| ------- | ----------- |
| **Wi-Fi 6** | Wi-Fi 6 gives you better wireless coverage and performance with added security. |
| **WPA3** | WPA3 provides improved Wi-Fi security by using the latest standard.|

### Security

| Feature | Description |
| ------- | ----------- |
| **Windows&nbsp;Defender System&nbsp;Guard** | Windows Defender System Guard Secure Launch protects bootup with a technology known as the Dynamic Root of Trust for Measurement (DRTM). With DRTM, the system initially follows the normal UEFI Secure Boot process. However, before launching, the system enters a hardware-controlled trusted state that forces the CPU(s) down a hardware-secured code path. If a malware rootkit/bootkit has bypassed UEFI Secure Boot and resides in memory, DRTM will prevent it from accessing secrets and critical code protected by the virtualization-based security environment. Firmware Attack Surface Reduction technology can be used instead of DRTM on supporting devices such as Microsoft Surface. For more information, see [How a hardware-based root of trust helps protect Windows](/windows/security/hardware-security/how-hardware-based-root-of-trust-helps-protect-windows). |
| **Windows&nbsp;Defender Security&nbsp;Center** | Improvements now include Protection history, including detailed and easier to understand information about threats and available actions, Controlled Folder Access blocks are now in the Protection history, Windows Defender Offline Scanning tool actions, and any pending recommendations. For more information, see [Windows Defender Security Center](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center). |
| **Windows&nbsp;Defender Firewall** | Windows Defender Firewall reduces the attack surface, helps enforce integrity and confidentiality of data, complements non-Microsoft network security solutions.  In this release, Windows Defender Firewall is also easier to analyze and debug using an in-box cross-component network diagnostic tool for Windows.  Additionally, event logs have been enhanced to ensure an audit can identify the specific filter that was responsible for any given event. For more information, see [Windows Defender Firewall](/windows/security/operating-system-security/network-security/windows-firewall/) |
| **Microsoft&nbsp;Defender for&nbsp;Endpoint** |Enhancements including [attack surface area reduction](/windows/security/threat-protection/windows-defender-atp/overview-attack-surface-reduction), [tamper-proofing](/microsoft-365/security/defender-endpoint/prevent-changes-to-security-settings-with-tamper-protection), and [next generation protection](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-in-windows-10) against ransomware, credential misuse, and attacks transmitted through removable storage. Additional improvements in the areas of advanced machine learning, emergency outbreak protection, certified ISO 27001 compliance, geolocation support and non-ASCII file paths. </br> *Note: The [DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware) parameter is deprecated in this release.* |
| **Microsoft&nbsp;Defender Application&nbsp;Guard** | Performance improvements associated with memory utilization, copying files as well as opening a file using a Universal Naming Convention (UNC) path or Server Message Block (SMB) share. For more information, see [Microsoft Defender Application Guard](/windows/security/threat-protection/windows-defender-application-guard/wd-app-guard-overview) |
| **Windows&nbsp;Defender Application&nbsp;Control** |  Suport for [multiple simultaneous code integrity policies](/windows/security/threat-protection/windows-defender-application-control/deploy-multiple-windows-defender-application-control-policies) for one device, [path-based policy and file rules](/windows/security/threat-protection/windows-defender-application-control/create-path-based-rules), and [COM Object Registration](/windows/security/threat-protection/windows-defender-application-control/allow-com-object-registration-in-windows-defender-application-control-policy). |
| **Application Isolation** | Isolated desktop environment where you can run untrusted software without the fear of lasting impact to your device. For more information, see [Windows Sandbox](/windows/security/application-security/application-isolation/windows-sandbox/windows-sandbox-overview). |

### Storage

| Feature | Description |
| ------- | ----------- |
| **Removable Packages** | Introducing [Removable Packages](../Optimize/Removable-Packages.md), a new feature exclusive to Windows IoT Enterprise LTSC allows a device administrator to reduce the operating system storage footprint. |
| **Reserved Storage** | Reserved storage sets aside disk space to be used by updates, apps, temporary files, and system caches. It improves the day-to-day function of your PC by ensuring critical OS functions always have access to disk space. On Windows 10 IoT Enterprise LTSC 2021, reserved storage is disabled by default, and can be configured using [DISM Reserved Storage Command-line](/windows-hardware/manufacture/desktop/dism-storage-reserve). For more information, see [Reserved storage](https://techcommunity.microsoft.com/t5/Storage-at-Microsoft/Windows-10-and-reserved-storage/ba-p/428327). |
| Unified Write Filter (UWF) | [Unified Write Filter](../customize/Unified-Write-Filter.md) improvements include [UWF Swapfile Created on Any Volume](../customize/uwf-wes7-ewf-to-win10-uwf.md), [Read Only Mode (ROM) Mode](../customize/uwf-wes7-ewf-to-win10-uwf.md#read-only-media-mode) and [Full Volume Commit in ROM Mode](../customize/uwf-wes7-ewf-to-win10-uwf.md#full-volume-commit-in-read-only-media-mode) |

### Windows Update

| Feature | Description |
| ------- | ----------- |
| **Manage Update Experience** | Introducing, generic, unbranded update message strings without reference to "Windows", "computer", or "PC" and configurable background color of the update screen from the traditional blue to whichever color best matches your branding requirements.  For more information, see [Manage Update Experience](/windows/iot/iot-enterprise/customize/update-notification). |

## Related content

- [What's new in Windows 10 Enterprise LTSC 2021](/windows/whats-new/ltsc/whats-new-windows-10-2021)
