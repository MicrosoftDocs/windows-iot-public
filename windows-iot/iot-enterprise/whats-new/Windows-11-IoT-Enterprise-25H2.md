---
title: What's new in Windows 11 IoT Enterprise, version 25H2?
titleSuffix: Windows IoT Enterprise
description: Learn about new and updated features that are of interest to device makers and IT pros working with Windows 11 IoT Enterprise, version 25H2.
author: vanloke323-Microsoft
ms.author: vlokeshwar
ms.date: 09/30/2025
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
keywords: Windows IoT Enterprise, Windows 11, Windows 11 IoT, Windows 11 IoT Enterprise
appliesto: "✅ Windows 11"
---

# What's new in Windows 11 IoT Enterprise, version 25H2

## Overview

Windows 11 IoT Enterprise, version 25H2 is a feature update for Windows 11 IoT Enterprise. Windows 11 IoT Enterprise, version 25H2 includes all updates to Windows 11 IoT Enterprise, version 24H2 plus some new and updated features. This article lists the new and updated features valuable for IoT scenarios.

### Servicing Lifecycle

Windows 11 IoT Enterprise follows the [Modern Lifecycle Policy](/lifecycle/policies/modern).

| Release Version | Build | Start Date | End&nbsp;of&nbsp;Servicing |
|---------|---------|--------------|----------------------------|
| Windows&nbsp;11&nbsp;IoT&nbsp;Enterprise,&nbsp;version&nbsp;22H2 | 26200 | 2025&#8209;09&#8209;30 | 2028&#8209;10&#8209;10 |

For more information, see [Windows 11 IoT Enterprise support lifecycle](/lifecycle/products/windows-11-iot-enterprise).

### New Devices

Windows 11 IoT Enterprise, version 25H2 is available for preinstallation by an Original Equipment Manufacturer (OEM).

- For information regarding the purchase of devices with Windows IoT Enterprise preinstalled, contact your preferred OEM.

- For information regarding OEM preinstallation of Windows IoT Enterprise on new devices for sale, see [OEM Licensing](../Commercialization/Licensing.md#oem-licensing).

### Upgrade

Windows 11 IoT Enterprise, version 25H2 is available as an upgrade to devices running Windows 11 IoT Enterprise (non-LTSC) via Windows Update, Windows Autopatch, and the Microsoft 365 admin center. Note that downloads in the Microsoft 365 admin center and similar channel can be delayed. The upgrade will become available via Windows Server Update Services (WSUS) on October 14, 2025, with the October security update. For more information, see [How to get the Windows 11 2025 Update]( https://aka.ms/how-to-get-25H2) and [An IT pro’s guide to Windows 11, version 25H2](https://aka.ms/25H2-for-IT-pros).

To learn more about the status of the update rollout, known issues, and new information, see [Windows release health](/windows/release-health/).

## Developer

| Feature | Description |
| ------- | ----------- |
| **Taskbar pinning improvements** </br> [25H2] | IT admins no longer need to restart explorer.exe to apply the [pinning policy](../configuration/taskbar/pinned-apps.md). After an admin applies the policy, users might see a pin on their taskbar within approximately 8 hours, depending on the refresh interval. Admins can also configure taskbar policies so users can unpin specific apps, ensuring they aren't repinned during the next policy refresh. To turn on this feature, use the [PinGeneration option](../configuration/taskbar/pinned-apps.md#pingeneration). The PinGeneration option is available for Windows 11 IoT Enterprise, version 23H2 or later devices. |
| **Energy saver settings** </br> [25H2] | IT admins can manage energy saver settings on Windows 11 IoT Enterprise devices through group policies or configuration service providers (CSP) using Microsoft Intune. This feature helps extend battery life by limiting background activity, dimming the screen, and contributing to environmental sustainability. For more information about this policy, see [EnableEnergySaver](../client-management/mdm/policy-csp-power.md#enableenergysaver) in the Power Policy CSP. |

## Management

| Feature | Description |
| ------- | ----------- |
| **Policy-based removal of preinstalled Microsoft Store apps** </br> [25H2] | Policy-based inbox app removal provides IT admins an easy way to remove preinstalled Microsoft Store apps (inbox apps) from Enterprise and Education editions of Windows 11 IoT, version 25H2 and later. This policy can streamline device provisioning and prevent removed apps such as Microsoft Clipchamp, Media Player, and Microsoft Teams from reappearing. For more information, see [Policy-based removal of preinstalled Microsoft Store apps](../configuration/policy-based-inbox-app-removal/policy-based-inbox-app-removal.md) and [RemoveDefaultMicrosoftStorePackages](../client-management/mdm/policy-csp-applicationmanagement.md#removedefaultmicrosoftstorepackages) in the ApplicationManagement Policy CSP. |
| **Windows Backup for Organizations** </br> [25H2] | [Windows Backup for Organizations](../configuration/windows-backup.md) is generally available. Users experience seamless device transitions with backup and restore of their user settings and Microsoft Store apps. For more information, see [Windows Backup for Organizations FAQ](../configuration/windows-backup/windows-backup-faq.md). |
| **Quick machine recovery** </br> [25H2] | Quick machine recovery enables the recovery of Windows devices when they encounter critical errors that prevent them from booting. Quick machine recovery automatically searches for remediations in the cloud and recovers from widespread boot failures. This reduces the burden on IT administrators when multiple devices are affected. For more information about enabling and configuring quick machine recovery, see [Quick machine recovery](../configuration/quick-machine-recovery.md). |

## Networking

| Feature | Description |
| ------- | ----------- |
| **Wi-Fi 7 for enterprise connectivity** </br> [25H2] | The performance enhancements introduced by [Wi-Fi 7 for consumers](https://support.microsoft.com/topic/26177a28-38ed-1a8e-7eca-66f24dc63f09) are now extended to enterprise environments. Wi-Fi 7 support for enterprise access points is designed to address evolving security needs while helping support reliable connectivity in high-density, high-throughput scenarios. Wi-Fi 7 offers enterprises advanced seamless roaming capabilities to help ensure that devices can easily transition between access points. and Additionally, it enforces the use of WPA3-Enterprise. For more information, see [https://aka.ms/WiFi7forEnterprise](ttps://aka.ms/WiFi7forEnterprise). |

## Privacy & Security

| Feature | Description |
| ------- | ----------- |
| **Privacy & security** </br> [25H2] | **Settings** > **Privacy & security** > **Text and Image Generation** displays the apps that use on-device generative AI models provided by Windows. Users can also choose which apps are permitted to use the generative AI technologies. |
| **Windows Hello interface** </br> [25H2] | Redesigned to support fast, clear communication that appears across multiple authentication flows. The Windows security credential experience for passkey offers a more intuitive interface designed to support fast, secure sign-in and easy switching between authentication options such as passkeys or connected devices. |
| **System dialog box** </br> [25H2] | When an app requests access to location, camera, microphone, or other device capabilities, Windows shows a redesigned system dialog box. To emphasize the privacy prompt, the screen dims slightly, and the prompt appears at the center of the screen. |

## User Experience

| Feature | Description |
| ------- | ----------- |
| **File Explorer: AI actions** </br> [25H2] | Right click or Shift+F10 on a file and select **AI actions** to edit images or summarize documents. If the file is an image (.jpg, .jpeg, or .png), AI options such as **Blur background**, **Erase objects**, and **Remove background**, are displayed in the context menu. |
| **File Explorer: Context menu** </br> [25H2] | **New Folder** command appears on the context menu, by right-clicking items in the left pane. |
| **File Explorer: Options** </br> [25H2] | Enable **Restore previous folder windows at logon** in **Options** to restore all the previously open tabs in each File Explorer window. |
| **File Explorer: Save restartable apps** </br> [25H2] | **Settings** > **Accounts** > **Sign in options** to enable the feature **Automatically save my restartable apps and restart them when I sign back in**. |
| **File Explorer: Archive files extraction** </br> [25H2] | Enhanced performance when extracting archive files. This performance improvement helps with copy- pasting large numbers of files out of large 7z or .rar archive. |
| **File Explorer: Activity and Recommended section** </br> [25H2] | When signed in with a Microsoft Entra ID, File Explorer displays people icons in the **Activity** column and the **Recommended** section at the top of File Explorer Home. |
| **Task Manager: Improvements** </br> [25H2] | Many improvements are made in the Task Manager performance including faster release process, resizing the windows, and reliability. Task Manager now uses standard metrics to show CPU workload consistently across all pages to align with industry standards and non-Microsoft tools. |
| **Task Manager: Accessibility** </br> [25H2] | Improvements in the keyboard focus, tab key navigation, text scaling, the readout of item names by screen readers, and high-contrast heatmaps. |

## Features removed in Windows 11 IoT, version 25H2

The following [deprecated features](/windows/whats-new/deprecated-features.md) are [removed](/windows/whats-new/removed-features) in Windows 11 IoT, version 25H2:

- **PowerShell 2.0**: PowerShell 2.0 is no longer included in Windows 11 IoT, version 25H2. For more information, see [Update to the latest version of PowerShell](../powershell/scripting/install/installing-powershell-core-on-windows.md).
- **Windows Management Instrumentation command-line (WMIC) utility**: [WMIC is removed](https://support.microsoft.com/topic/e9e83c7f-4992-477f-ba1d-96f694b8665d) from Windows 11 IoT, version 25H2. All later releases for Windows 11 won't include WMIC.

## Related content

- [How to get the Windows 11 2025 Update](https://blogs.windows.com/windowsexperience/?p=179899) | Windows Experience Blog
- [An IT pro's guide to Windows 11, version 25H2](https://aka.ms/25H2-for-IT-pros) | Windows IT Pro Blog
- [Get ready for Windows 11, version 25H2](https://techcommunity.microsoft.com/blog/windows-itpro-blog/get-ready-for-windows-11-version-25h2/4426437) | Windows IT Pro Blog
- [What's new in Windows 11, version 25H2](/windows/whats-new/whats-new-windows-11-version-25h2)
- [Windows 11 requirements](/windows/whats-new/windows-11-requirements)
- [Windows release health](https://aka.ms/windowsreleasehealth)
- [Windows 11 release information](/windows/release-health/windows11-release-information)
