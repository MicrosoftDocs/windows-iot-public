---
title: What's new in Windows 10 IoT Enterprise, version 21H2
description: Learn more about what's new in Windows 10 IoT Enterprise, version 21H2, including servicing updates, Windows Subsystem for Linux, the latest CSPs, and more.
ms.prod: windows-iot
author: TerryWarwick
ms.author: twarwick
ms.topic: article
ms.technology: iot
ms.date: 03/30/2023
---

# What's new in Windows 10 IoT Enterprise, version 21H2

## Overview

Windows 10, version 21H2 is a feature update for Windows 10 IoT Enterprise. This article lists the new and updated features supporting IoT scenarios. Windows 10, version 21H2 includes all features and fixes in previous cumulative updates to Windows 10, version 21H1.

Windows 10 IoT Enterprise, version 21H2 follows the [Modern Lifecycle Policy](/lifecycle/policies/modern).

| Release | Version | Availability | End of Servicing |
| --- | --- | --- | --- |
| Windows 10 IoT Enterprise, version 21H2 | 19044 | 2021-11-16 | 2024-06-11 |

For more information, see [Windows 10 IoT Enterprise support lifecycle](/lifecycle/products/windows-10-iot-enterprise).

## Availability

Windows 10 IoT Enterprise, version 22H2 is available for Windows IoT Enterprise device makers through an authorized [Windows IoT Distributor](https://aka.ms/IoTDistributorList) for building new devices.  Windows IoT Enterprise is intended for fixed purpose devices with specific allowances and restrictions in the license agreement. To learn more, see [Licensing and Usage](/windows/iot/iot-enterprise/commercialization/licensing) contact an authorized [Windows IoT Distributor](https://aka.ms/IoTDistributorList) for additional guidance.

Windows 10, version 22H2 is also available to users with devices running Windows 10 IoT Enterprise, version 20H2 or later who are interested in the latest features and are ready to install this release on their device. If you would like to install the new release, open your Windows Update settings (**Settings > Update & Security > Windows Update**) and select **Check for updates**. Eligible devices may also be offered the option to choose to upgrade to Windows 11. If the update appears, you can simply select Download and install to get started. Once the download is complete and the feature update is ready to install, we’ll notify you so that you can pick a convenient time to finish the installation and reboot your device, ensuring that the update does not disrupt your activities. To learn more about the status of the 2022 Update rollout, known issues and new information, visit [Windows release health](/windows/release-health/).

## What's new

| Feature | Description |
| --- | --- |
| Customizable Windows Update UX | We are enabling you to [manage your Windows update experience](../customize/Update-Notification.md) with generic update message strings and screen accent colors. |
| Soft Real-Time | Introducing [Soft-Real Time](../soft-real-time/Soft-Real-Time.md), a new feature that allows device makers to introduce soft real-time capabilities on their devices. |
| Unified Write Filter (UWF) Updates | [Unified Write Filter](../customize/Unified-Write-Filter.md) improvements include [UWF Swapfile Created on Any Volume](/windows-hardware/customize/enterprise/uwf-wes7-ewf-to-win10-uwf), [Read Only Mode (ROM) Mode](/windows-hardware/customize/enterprise/uwf-wes7-ewf-to-win10-uwf#read-only-media-mode) and [Full Volume Commit in ROM Mode](/windows-hardware/customize/enterprise/uwf-wes7-ewf-to-win10-uwf#full-volume-commit-in-read-only-media-mode) |
| GPU Compute Support | GPU compute support in the [Windows Subsystem for Linux (WSL)](/windows/wsl/about) and [Azure IoT Edge for Linux on Windows](/windows/iot/iot-enterprise/azure-iot-edge-for-linux-on-windows) deployments for machine learning and other compute intensive workflows.|
| WPA3 H2E standards support | In this new release, there will be WPA3 H2E standards support for enhanced Wi-Fi security. To learn more, view [Faster and more secure Wi-Fi in Windows](https://support.microsoft.com/windows/faster-and-more-secure-wi-fi-in-windows-26177a28-38ed-1a8e-7eca-66f24dc63f09)|
| Get the latest CSPs | The device configuration settings catalog has been updated to list over 1,400 settings previously not available for configuration via MDM. These new MDM policies include administrative template (ADMX) policies, such as App Compatibility, Event Forwarding, Servicing, and Task Scheduler. For more information on the CSPs, see the [Configuration service provider reference](/windows/client-management/mdm/configuration-service-provider-reference). |
| Wi-Fi 6 | Wi-Fi 6 gives you better wireless coverage and performance with added security. To learn more, see [Faster and more secure Wi-Fi in Windows](https://support.microsoft.com/windows/faster-and-more-secure-wi-fi-in-windows-26177a28-38ed-1a8e-7eca-66f24dc63f09#WindowsVersion=Windows_10). |
| WPA3 H2H standards support | WPA3 provides improved Wi-Fi security by using the latest standard. To learn more, see [Faster and more secure Wi-Fi in Windows](https://support.microsoft.com/windows/faster-and-more-secure-wi-fi-in-windows-26177a28-38ed-1a8e-7eca-66f24dc63f09#WindowsVersion=Windows_10). |

## Related Topics

- [Windows 10 IoT Enterprise LTSC 2021 announcement](https://aka.ms/W10IOTLTSC2021Blog)
- [Introducing the next feature update to Windows 10: 21H2](https://blogs.windows.com/windowsexperience/2021/07/15/introducing-the-next-feature-update-to-windows-10-21h2/)
- [What's new for IT pros in Windows 10, version 21H2](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/what-s-new-for-it-pros-in-windows-10-version-21h2/ba-p/2971409)
- [Download Administrative Templates (.admx) for Windows 10 November 2021 Update [21H2]](https://aka.ms/ADMX/Windows10-21H2)
- [Release health - Windows 10, version 21H2](/windows/release-health/status-windows-10-21h2)
- [Windows 10, version 21H2 update history](https://support.microsoft.com/topic/windows-10-update-history-857b8ccb-71e4-49e5-b3f6-7073197d98fb)
- [Group Policy settings reference spreadsheet for Windows 10, version 21H2](https://aka.ms/GPsettings/Windows10-21H2)
- [Features and functionality removed in Windows 10](/windows/whats-new/removed-features)
- [Windows 10 features we're no longer developing](/windows/whats-new/deprecated-features)
