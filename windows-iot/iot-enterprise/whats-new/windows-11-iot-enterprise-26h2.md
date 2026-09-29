---
title: What's new in Windows 11 IoT Enterprise, version 26H2?
titleSuffix: Windows IoT Enterprise
description: Learn about new and updated features that are of interest to device makers and IT pros working with Windows 11 IoT Enterprise, version 26H2.
author: v-fvalentyna
ms.author: v-fvalentyna
ms.date: 09/29/2026
ms.topic: concept-article
ms.service: windows-iot
ms.subservice: iot
keywords: Windows IoT Enterprise, Windows 11, Windows 11 IoT, Windows 11 IoT Enterprise
appliesto: "✅ Windows 11"
---

# What's new in Windows 11 IoT Enterprise, version 26H2

## Overview

Windows 11 IoT Enterprise, version 26H2 is a feature update for Windows 11 IoT Enterprise. This version includes all updates to Windows 11 IoT Enterprise, versions 25H2 and 24H2, plus some new and updated features. This article lists the new and updated features that are valuable for IoT scenarios.

### Servicing lifecycle

Windows 11 IoT Enterprise follows the [Modern Lifecycle Policy](/lifecycle/policies/modern).

| Release Version | Build | Start Date | End&nbsp;of&nbsp;Servicing |
|---------|---------|--------------|----------------------------|
| Windows&nbsp;11&nbsp;IoT&nbsp;Enterprise,&nbsp;version&nbsp;26H2 | 26300 | 2026&#8209;09&#8209;29 | 2029&#8209;10&#8209;09 |

For more information, see [Windows 11 IoT Enterprise support lifecycle](/lifecycle/products/windows-11-iot-enterprise).

### New devices

Original Equipment Manufacturers (OEMs) can preinstall Windows 11 IoT Enterprise, version 26H2 on devices.

- To purchase devices with Windows IoT Enterprise preinstalled, contact your preferred OEM.

- For information about OEM preinstallation of Windows IoT Enterprise on new devices for sale, see [OEM Licensing](../Commercialization/Licensing.md#oem-licensing).

### Upgrade

Windows 11 IoT Enterprise, version 26H2 is available as an upgrade to devices running Windows 11 IoT Enterprise (non-LTSC) via Windows Update, Windows Autopatch, and the Microsoft 365 admin center. Note that downloads in the Microsoft 365 admin center and similar channel can be delayed. The upgrade becomes available via Windows Server Update Services (WSUS) on October 13, 2026, with the October security update. For more information, see [How to get the Windows 11 2026 Update](https://aka.ms/how-to-get-26H2) and [An IT pro’s guide to Windows 11, version 26H2](https://aka.ms/26H2-for-IT-pros).

To learn more about the status of the update rollout, known issues, and new information, see [Windows release health](/windows/release-health/).

> [!NOTE]
> When upgrading from Windows 10 IoT Enterprise version 22H2 via Windows Update, the device must first update to Windows 11 IoT Enterprise version 23H2, 22H2, or 21H2. Direct upgrades to versions 26H2, 25H2, or 24H2 aren't supported.

## Features added to Windows 11 since version 25H2

### Security

| Feature | Description |
| ------- | ----------- |
| **Administrator protection** | Administrator protection enables administrative tasks by using just-in-time privileges rather than free-floating administrator rights. It introduces profile separation to help harden Windows against elevation-of-privilege attacks. The feature is off by default. You can enable it by using Microsoft Intune or Group Policy. |
| **Native Sysmon integration** | System Monitor (Sysmon) is now built into Windows. It captures system events you can use for threat detection and supports custom configuration files to filter which events to monitor. Captured events appear in Windows Event Log, allowing security tools and other applications to consume them. Built-in Sysmon is off by default. Enable it to use it. |
| **Post-quantum crypto APIs (ML-KEM / ML-DSA)** | Windows adds API support for the NIST post-quantum cryptography algorithms ML-KEM and ML-DSA in accordance with FIPS 203 and FIPS 204. You can use these algorithms for key exchange, signing, and decryption through Cryptography, Next Generation Crypto (CNG), and .NET. |
| **Standalone ML-KEM for TLS** | ML-KEM is supported as a standalone algorithm for TLS key exchange, enabling quantum-resistant secure connections for connected IoT endpoints. |
| **Locked batch files during execution** | Administrators and Application Control for Business policy authors get extra control over how Windows processes batch files and Command Prompt scripts. You can administratively enable a more secure processing mode that prevents batch files from changing during execution, hardening automation and provisioning scripts on kiosk and embedded devices. |
| **Smart App Control toggle without reinstall** | You can turn Smart App Control (SAC) on or off without requiring a clean installation of Windows. When turned on, Smart App Control helps block untrusted or potentially harmful apps. |

## Management

| Feature | Description |
| ------- | ----------- |
| **Windows settings backup and restore** | Windows settings backup is now enabled by default for eligible commercial devices, helping organizations preserve supported Windows settings and Microsoft Store app lists for recovery and device-replacement scenarios. The first sign-in restore experience supports Microsoft Entra hybrid joined devices, Cloud PCs, and multi-user environments, restoring user settings and the Store app list automatically at first sign-in. Existing administrator-configured policies continue to be honored. |
| **Policy-based removal of preinstalled apps** | With policy-based removal of preinstalled Microsoft apps, you can specify additional MSIX or APPX packaged apps for removal by using their app package family names through Group Policy. This approach streamlines device images and prevents unwanted apps from reappearing. |
| **Enterprise State Roaming via Windows settings backup and restore** | You can now manage Enterprise State Roaming through Windows settings backup policies, alongside the first sign-in restore experience for Microsoft Entra hybrid joined devices, Cloud PCs, and multi-user environments. | 
| **Fewer restarts / combined servicing** | Windows Update reduces the number of restarts required to keep devices up to date. It now installs eligible updates together with the monthly security update when possible, giving admins a single, predictable servicing window. Individual updates remain available under **Settings** > **Windows Update** > **Available updates**. Expedited or critical updates might still install separately. |
| **RSAT support on Arm64** | Remote Server Administration Tools now run on Arm64 devices, extending management tooling to Arm-based IoT and edge hardware. |

## Deployment and recovery

| Feature | Description |
| ------- | ----------- |
| **Quick machine recovery enhancements** | Quick machine recovery can perform a one-time scan for remediation when both quick machine recovery and **Automatically check for solutions** are turned on. If a solution isn't immediately available, it directs users to other recovery options. For domain-joined or enterprise-managed devices, the feature remains off unless you enable it. |
| **Point-in-time restore for Windows** | Point-in-time restore provides a recovery option that can roll back a PC (including apps, settings, and personal files) to a recent automatic restore point. This feature helps reduce downtime and simplify troubleshooting when issues occur on fixed-function devices. |
| **Windows Autopilot device preparation - device association** | Device association for Windows Autopilot device preparation helps organizations identify trusted devices before enrollment. It enables device-targeted policies, automatic corporate device enrollment, and more setup customization during the out-of-box experience (OOBE). |
| **Custom user folder name during setup** | Set a custom user-profile folder name during Windows Setup, giving OEMs and integrators cleaner, standardized device images. |

## Kiosk and camera

| Feature | Description |
| ------- | ----------- |
| **Simplified Edge configuration in multi-app kiosk** | Streamlined setup of Microsoft Edge within multi-app kiosk mode. Directly relevant to retail, signage, and self-service scenarios. |
| **Multi-App Camera and Basic Camera GPO management** | Multi-App Camera allows multiple applications to access the camera stream at the same time. Basic Camera mode provides simplified camera functionality you can use for troubleshooting or improving stability. Configure both Multi-App Camera and Basic Camera modes through Group Policy. |
| **Camera pan and tilt controls** | Pan and tilt controls in **Settings** for supported cameras. Useful for interactive kiosks and monitoring endpoints. |

## Printing

| Feature | Description |
| ------- | ----------- |
| **Protected Print Mode indicator** | Visible indicator for Protected Print Mode, supporting the modern, more secure Windows printing stack in POS and retail deployments. |
| **Windows Ready Print - default IPP installation** | Windows Ready Print installs printers by using the standard IPP class driver by default, reducing the driver footprint on managed devices. |

### Developer and command line

| Feature | Description |
| ------- | ----------- |
| **Edit - built-in command-line text editor** | A new built-in terminal text editor (`edit`) for quick, local file editing during provisioning and troubleshooting. It's open-source on GitHub. |

### Accessibility

| Feature | Description |
| ------- | ----------- |
| **Magnifier screen reader announcements** | Magnifier provides clearer and more consistent announcements when used with a screen reader. |
| **Magnifier protected content support** | Magnifier can magnify permitted protected content. |
| **Screen tint** | Apply a full-screen color tint to help reduce eye strain and improve readability. |
| **Direct Magnifier zoom control** | Users can enter a specific zoom percentage and adjust zoom increments directly from the Magnifier window. |

### Narrator

| Feature | Description |
| ------- | ----------- |
| **Braille Viewer** | Narrator includes Braille Viewer, which displays on-screen text and its Braille equivalent on a refreshable Braille display. |
| **Custom control announcements** | Users have more control over which details about on-screen controls are announced and the order in which they're announced. |

### Touchpad

| Feature | Description |
| ------- | ----------- |
| **Scroll and zoom speed controls** | Adjust touchpad scrolling and zoom speed from Settings for a more comfortable input experience. |
| **Accelerated scrolling** | Touchpad acceleration enables faster scrolling through long content. |

### Voice Access

| Feature | Description |
| ------- | ----------- |
| **Natural language commands** | Voice access supports natural language commands on supported Copilot+ PCs. There's now more flexibility to use filler words and synonyms instead of predefined commands. |
| **Simplified onboarding** | A simplified onboarding experience makes it easier to get started with Voice access. | 
| **Additional language support** | Voice access adds French, German, Spanish, and Korean language support. |
| **Voice isolation** | Voice isolation helps reduce interference from other speakers and background noise for more reliable voice control. |

### Voice typing

| Feature | Description |
| ------- | ----------- |
| **Wait before acting** | A new setting lets voice typing wait before acting on dictated input, improving accuracy in noisy or hands-busy environments. |

### Passkeys

| Feature | Description |
| --------- | --------- |
| **Plugin credential manager integration** | Windows supports plugin credential managers for passkeys. After installing a credential manager application that supports integration, users can use existing passkeys stored in the credential manager or save new passkeys to it. |
| **Security key PIN setup** | Windows supports setting up a PIN for security keys during authentication when required. | 

### Windows Hello

| Feature | Description |
| --------- | --------- |
| **ESS support for external fingerprint readers** | Windows Hello Enhanced Sign-in Security (ESS) supports compatible peripheral fingerprint sensors. This support extends ESS beyond devices with built-in fingerprint sensors to desktops and other Windows 11 PCs, including Copilot+ PCs. |


## Features removed in Windows 11 IoT, version 26H2

The following changes might affect existing IoT device configurations, drivers, or automation. Review them before upgrading.

| Feature | Description |
| --------- | --------- |
| **Windows Management Instrumentation command-line (WMIC) utility** | The Windows Management Instrumentation Command-line (WMIC) utility is removed from Windows 11, version 24H2 and later, and is no longer available as a Feature on Demand (FoD). WMI itself remains supported. Migrate scripts to PowerShell CIM cmdlets. |
| **Default trust for cross-signed drivers removed** | Windows changes how the kernel trusts third-party drivers: default trust for cross-signed drivers is removed. Drivers from the Windows Hardware Compatibility Program (WHCP) and an allow list of trusted legacy drivers remain allowed. Windows audits driver compatibility for at least 100 hours and three restarts before enabling enforcement. Audit device drivers before upgrading. |
| **MSHTA inline script execution blocked** | Inline scripts passed directly to MSHTA.exe no longer execute due to security hardening. Review any provisioning or automation that relies on MSHTA. |

> [!NOTE]
> Consult the complete list of [deprecated features](/windows/whats-new/deprecated-features) and [removed features](/windows/whats-new/removed-features) in Windows.

## Related content

- [How to get the Windows 11 2026 Update](https://aka.ms/how-to-get-26H2) | Windows Experience Blog
- [An IT pro's guide to Windows 11, version 26H2](https://aka.ms/26H2-for-IT-pros) | Windows IT Pro Blog
- [Get ready for Windows 11, version 26H2](https://techcommunity.microsoft.com/blog/windows-itpro-blog/get-ready-for-windows-11-version-26h2/4529367) | Windows IT Pro Blog
- [What's new in Windows 11, version 26H2](/windows/whats-new/whats-new-windows-11-version-26h2)
- [Windows 11 requirements](/windows/whats-new/windows-11-requirements)
- [Windows release health](/windows/release-health/)
- [Windows 11 release information](/windows/release-health/windows11-release-information)
