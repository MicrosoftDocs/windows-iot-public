---
title: What's new in Windows 10 IoT Enterprise, version 22H1
description: Learn more about what's new in Windows 10 IoT Enterprise, version 22H1.
ms.prod: windows-iot
author: TerryWarwick
ms.author: twarwick
ms.topic: article
ms.technology: iot
ms.date: 03/13/2023
---

# What's new in Windows 10 IoT Enterprise, version 21H1

## Overview

Windows 10, version 21H1 is a feature update for Windows 10 IoT Enterprise. This article lists the new and updated features supporting IoT scenarios. Windows 10, version 21H1 includes all features and fixes in previous cumulative updates to Windows 10, version 20H2.

Windows 10 IoT Enterprise, version 21H2 follows the [Modern Lifecycle Policy](/lifecycle/policies/modern).

| Release | Version | Availability | End of Servicing |
| --- | --- | --- | --- |
| Windows 10 IoT Enterprise, version 21H1 | 19043 | 2021-05-18 | 2022-12-13 |

For more information, see [Windows 10 IoT Enterprise support lifecycle](/lifecycle/products/windows-10-iot-enterprise).

## Availability

Windows 10 IoT Enterprise, version 21H1 is available for Windows IoT Enterprise device makers through an authorized [Windows IoT Distributor](https://aka.ms/IoTDistributorList) for building new devices. Windows IoT Enterprise is intended for fixed purpose devices with specific allowances and restrictions in the license agreement. To learn more, see [Licensing and Usage](/windows/iot/iot-enterprise/commercialization/licensing) contact an authorized [Windows IoT Distributor](https://aka.ms/IoTDistributorList) for additional guidance.

Windows 10, version 21H1 is also available to users with devices running Windows 10 IoT Enterprise, version 20H2 or later who are interested in the latest features and are ready to install this release on their device. If you would like to install the new release, open your Windows Update settings (**Settings > Update & Security > Windows Update**) and select **Check for updates**. Eligible devices may also be offered the option to choose to upgrade to Windows 11. If the update appears, you can simply select Download and install to get started. Once the download is complete and the feature update is ready to install, we’ll notify you so that you can pick a convenient time to finish the installation and reboot your device, ensuring that the update does not disrupt your activities. To learn more about the status of the 2022 Update rollout, known issues and new information, visit .

## What's new

| Feature | Description |
| --- | --- |
| Windows Assessment and Deployment Toolkit (ADK) | There's no new ADK for Windows 10, version 21H1. The ADK for Windows 10, version 2004 will also work with Windows 10, version 21H1.  For more information, see [Download and install the Windows ADK](/windows-hardware/get-started/adk-install). |
| Windows Management Instrumentation (WMI) Group Policy Service (GPSVC) | An issue is fixed that caused changes by an Active Directory (AD) administrator to user or computer group memberships to propagate slowly. Although the access token eventually updates, these changes might not appear when the administrator uses gpresult /r or gpresult /h to create a report. |
| Windows Defender Application Guard (WDAG) | Performance improvements: </br> 1) Reduce the time to open a Microsoft Defender Application (WDAG) Office document using a UNC or SMB share link. </br> 2) Fix memory issue that could cause a WDAG container to use almost 1 GB of working set memory when the container is idle.  </br> 3) The performance of Robocopy is improved when copying files over 400 MB in size.
| Microsoft Edge | The new Chromium-based [Microsoft Edge](https://www.microsoft.com/edge/business) browser is included with this release.  For more information about what's new in Edge, see the [Microsoft Edge insider](https://www.microsoftedgeinsider.com/whats-new). |

## Related Topics

- [What's new in Windows 10, version 21H1 for IT Pros](/windows/whats-new/whats-new-windows-10-version-21h1)
- [IT tools to support Windows 10, version 21H1](https://aka.ms/tools-for-21H1)
- [Introducing the next feature update to Windows 10, version 21H1](https://blogs.windows.com/windowsexperience/2021/02/17/introducing-the-next-feature-update-to-windows-10-version-21h1/)
- [Features and functionality removed in Windows 10](/windows/whats-new/removed-features.md): Removed features.
- [Windows 10 features we're no longer developing](/windows/whats-new/deprecated-features.md): Features that aren't being developed.
