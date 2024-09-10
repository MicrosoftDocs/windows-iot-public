---
title: What's new in Windows 11 IoT Enterprise, version 24H2?
titleSuffix: Windows IoT Enterprise
description: Learn about new and updated features that are of interest to device makers and IT Pros working with Windows 11 IoT Enterprise, version 24H2.
author: TerryWarwick
ms.author: twarwick
ms.date: 07/25/2024
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
keywords: Windows IoT Enterprise, Windows 11, Windows 11 IoT, Windows 11 IoT Enterprise
---

# What's new in Windows 11 IoT Enterprise, version 24H2

Windows 11 IoT Enterprise, version 24H2 is a feature update for Windows 11 IoT Enterprise. Windows 11 IoT Enterprise, version 24H2 includes all updates to Windows 11 IoT Enterprise, version 23H2 plus some new and updated features. This article lists the new and updated features valuable for IoT scenarios.

Windows 11 IoT Enterprise follows the [Modern Lifecycle Policy](/lifecycle/policies/modern).

| Release Version | Build | Start Date | End&nbsp;of&nbsp;Servicing |
|---------|---------|--------------|----------------------------|
| Windows&nbsp;11&nbsp;IoT&nbsp;Enterprise,&nbsp;version&nbsp;24H2 | 26100 | 2024&#8209;10&#8209;01 | 2027&#8209;10&#8209;12 |

For more information, see [Windows 11 IoT Enterprise support lifecycle](/lifecycle/products/windows-11-iot-enterprise).

## Availability

Windows 11 IoT Enterprise, version 24H2 is available through Windows Update, Windows Server Update Services (including Configuration Manager), the OEM Software Order Center, as well as [volume licensing](https://www.microsoft.com/licensing/terms/productoffering/WindowsDesktopOperatingSystem/all).

To learn more about the status of the update rollout, known issues, and new information, see [Windows release health](/windows/release-health/).

## What's new

| Feature | Description |
| ------- | ----------- |
| **Checkpoint cumulative updates** </br> [24H2] | Windows quality updates are provided as cumulative updates throughout the life cycle of a Windows release.  Checkpoint cumulative updates introduce periodic baselines that reduce the size of future cumulative updates making the distribution of monthly quality updates more efficient.  For more information, see [https://aka.ms/CheckpointCumulativeUpdates](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/introducing-windows-11-checkpoint-cumulative-updates/ba-p/4182552). |
| **Local Security Authority (LSA) protection enablement on upgrade** </br> [24H2] | On upgrade to 24H2,  an audit occurs for incompatibilities with LSA protection for a period of time. If incompatibilities aren't detected, LSA protection is automatically enabled. For more information, see [LSA protection](/windows-server/security/credentials-protection-and-management/configuring-additional-lsa-protection). |
| **Windows Local Admin Password Solution (LAPS)** </br> [24H2] | Windows Local Administrator Password Solution (Windows LAPS) is a Windows feature that automatically manages and backs up the password of a local administrator account on your Microsoft Entra joined or Windows Server Active Directory-joined devices. Windows LAPS is the successor for the now deprecated legacy Microsoft LAPS product. For more information, see [What is Windows LAPS?](/windows-server/identity/laps/laps-overview)|
| **Windows protected print mode** </br> [24H2] | Windows protected print mode (WPP) enables a modern print stack which is designed to work exclusively with [Mopria certified printers](https://mopria.org/certified-products). For more information, see [What is Windows protected print mode (WPP)](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/a-new-modern-and-secure-print-experience-from-windows/ba-p/4002645) and [Windows Insider WPP announcement](https://blogs.windows.com/windows-insider/2023/12/13/announcing-windows-11-insider-preview-build-26016-canary-channel/). |
| **Wi-Fi 7 consumer access points** </br> [24H2] | Support for Wi-Fi 7 consumer access points offers unprecedented speed, reliability, and efficiency for wireless devices.  For more information, see the Win-Fi 7 announcements from [Wi-Fi Alliance](https://www.wi-fi.org/discover-wi-fi/wi-fi-certified-7) and the [Windows Insider](https://blogs.windows.com/windows-insider/2024/02/22/announcing-windows-11-insider-preview-build-26063-canary-channel/). |
| **Sudo for Windows** </br> [24H2] | Sudo for Windows is a new way for users to run elevated commands (as an administrator) directly from an unelevated console session. For more information, see [Sudo for Windows](/windows/sudo/). |
| **Remote Desktop Connection improvements** </br> [24H2] ||
| **Bluetooth &#174; Low Energy Audio support** </br> [24H2] | Windows has taken a significant step forward in accessibility by supporting the use of hearing aids equipped with the latest Bluetooth &#174; Low Energy Audio technology. For more information, see [Improving accessibility with Bluetooth &#174; LE Audio](https://blogs.windows.com/windows-insider/2023/10/18/announcing-windows-11-insider-preview-build-25977-canary-channel/). |

<!--

## Taskbar & System Tray Enhancements [24H2]

   The network icon in the system tray now animates when a connection is in progress. This animation replaces the disconnected globe when a network is taking time to establish a connection. 
   • Improved VPN user experience in Quick Settings for both single and multiple VPNs. 
   • New refresh button on the Wi-Fi Quick Settings flyout with indication of scen in progress. 
   • Live captions quick setting for easier access. 
   • Updated design of the progress bar on task bar and start menu.

## Accessibility Improvements [24H2] 
   • Live captions quick setting for easier access.|

## File Explorer Improvements [24H2] 
   • Support for creating 7-zip and TAR archives in addition to ZIP. 
   • New compression wizard for more formats and details. 
   • Option to apply selected action (skip, replace) for all conflicts when extracting files. 
   • PNG files now support viewing and editing metadata. |

## Energy Saver Feature [24H2] 
   • Extends battery life and reduces energy use by trading off some system performance. 
   • Can be toggled on and off via Quick Settings or configured to run automatically at a certain battery percentage. 
   • New energy saver icon for PCs that are plugged in and do not have batteries.

## Graphics Enhancements [24H2] 
   • HDR background support for JXR files. </br> • Content Adaptive Brightness Control (CABC) on plugged-in devices. 
   • Dynamic Refresh Rate toggle in advanced display settings.
   • Improved refresh rate logic for different monitors.
   • Options for tuning intensity and color boost to the color filters.

## Bluetooth Enhancements [24H2] 
   • New capabilities for controlling audio presets and ambient sounds for Bluetooth LE Audio hearing aids. 
   • Enhanced Bluetooth & devices settings page. </br> • Monitoring essential Bluetooth device details such as battery life and connection status. 

## Networking Improvements [24H2] 
   • Support for Wi-Fi 7. 
   • Multi-Link operation (MLO) for using multiple bands simultaneously. 
   • 320 MHz ultra-wide bandwidth in 6GHz. 
   • 4096-QAM modulation for increased data transmission.

## General Improvements [24H2] 
   • Voice Clarity feature for enhanced audio experience. 
   • Two new keyboard layouts for German extended layout standards (E1 and E2). 
   • New Hebrew keyboard layout.

-->

## Features Removed

The following [deprecated features](deprecated-features.md) are removed in Windows 11, version 24H2:

| Feature | Description |
|---------|-------------|
| **WordPad** | WordPad is removed from all editions of Windows starting in Windows 11, version 24H2 and Windows Server 2025. <!--8254696, 8494641--> |
| **Alljoyn** | Microsoft's implementation of AllJoyn, which included the [Windows.Devices.AllJoyn API namespace](/uwp/api/windows.devices.alljoyn), a [Win32 API](/windows/win32/api/_alljoyn/), a [management configuration service provider (CSP)](/windows/client-management/mdm/alljoynmanagement-csp), and an [Alljoyn Router Service](/windows-server/security/windows-services/security-guidelines-for-disabling-system-services-in-windows-server#alljoyn-router-service) is retired.<!--8396030--> |

## Related articles

- Windows Experience Blog: How to get the Windows 11 2024 Update
- Windows IT Pro Blog: What’s new for IT pros in Windows 11, version 24H2
- [What's new in Windows 11, version 24H2](https://learn.microsoft.com/en-us/windows/whats-new/whats-new-windows-11-version-24h2)
- [Windows Consumer: What's new in recent Windows updates](https://support.microsoft.com/windows/what-s-new-in-recent-windows-updates-2df971e0-341a-68b1-3bf8-bc3e3ff8c3a5)
- [Windows 11 requirements](/windows/whats-new/windows-11-requirements)
- [Plan for Windows 11](/windows/whats-new/windows-11-plan)
- [Prepare for Windows 11](/windows/whats-new/windows-11-prepare)
- [Windows release health](https://aka.ms/windowsreleasehealth)
- [Windows 11 release information](/windows/release-health/windows11-release-information)
