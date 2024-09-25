---
title: What's new in Windows 11 IoT Enterprise, version 23H2?
titleSuffix: Windows IoT Enterprise
description: Learn about new and updated features that are of interest to device makers and IT Pros working with Windows 11 IoT Enterprise, version 23H2.
author: TerryWarwick
ms.author: twarwick
ms.date: 09/23/2024
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
keywords: Windows IoT Enterprise, Windows 11, Windows 11 IoT, Windows 11 IoT Enterprise
---

# What's new in Windows 11 IoT Enterprise, version 23H2

## Overview

Windows 11 IoT Enterprise, version 23H2 is a feature update for Windows 11 IoT Enterprise. Windows 11 IoT Enterprise, version 23H2 includes all updates to Windows 11 IoT Enterprise, version 22H2 plus some new and updated features. This article lists the new and updated features valuable for IoT scenarios.

### Servicing Lifecycle

Windows 11 IoT Enterprise follows the [Modern Lifecycle Policy](/lifecycle/policies/modern).

| Release Version | Build | Start Date | End&nbsp;of&nbsp;Servicing |
|---------|---------|--------------|----------------------------|
| Windows&nbsp;11&nbsp;IoT&nbsp;Enterprise,&nbsp;version&nbsp;23H2 | 22631 | 2023-10-31 | 2026-11-10 |

For more information, see [Windows 11 IoT Enterprise support lifecycle](/lifecycle/products/windows-11-iot-enterprise).

### New Devices

Windows 11 IoT Enterprise, version 23H2 is available for pre-install by an Original Equipment Manufacturer (OEM).

- If you are a customer looking to purchase devices with Windows IoT Enterprise preinstalled contact your preferred OEM.

- If you are an OEM wanting to pre-install Windows IoT Enterprise on your new devices for sale, see [OEM Licensing](../Commercialization/Licensing.md#oem-licensing) for more information.

### Upgrade

Windows 11 IoT Enterprise, version 23H2 is available as an upgrade to devices running Windows 11 IoT Enterprise (non-LTSC) through Windows Update, Windows Server Update Services (including Configuration Manager), Windows Update for Business, and the Volume Licensing Service Center (VLSC). For more information, see [How to get the Windows 11, version 23H2 update]( https://aka.ms/how-to-get-23H2). Review the [Windows 11, version 23H2 Windows IT Pro blog post](https://aka.ms/new-in-23H2) to discover information about available deployment resources such as the [Windows Deployment Kit (Windows ADK)](/windows-hardware/get-started/adk-install).

To learn more about the status of the update rollout, known issues, and new information, see [Windows release health](/windows/release-health/).

## Accessibility

| Feature | Description |
| ------- | ----------- |
| **Braille displays** <!--7579823-->        | The compatibility of braille displays was expanded. Braille displays work seamlessly and reliably across multiple screen readers, improving the end user experience. We also added support for new braille displays and new braille input and output languages in Narrator. For more information, see [Accessibility information for IT professionals](/windows/configuration/windows-accessibility-for-ITPros). |
| **Narrator improvements** <!--kb5019509--> | Scripting functionality was added to Narrator. Narrator includes more natural voices. <!--8138352, 8138357--> |

## Applications

| Feature </br> [Release]| Description |
| --- | --- |
| **Task Manager**  </br> [22H2]/[23H2] | A new command bar was added to each page to give access to common actions. Task Manager matches the system wide theme configured in Windows Settings. Added an efficiency mode that allows you to limit the resource usage of a process. </br> <!--kb5019509--> Process filtering, theme settings, and the ability to opt out of efficiency mode notification were added to Task Manager. |
| **File Explorer Tabs** </br> [23H2] <!--kb5019509--> | File Explorer includes tabs to help you organize your File Explorer sessions. |
| **Copilot in Windows** <!--8138371, 8092554, WIP.23493 --> | Copilot in Windows provides centralized generative AI assistance to your users right from the Windows desktop. For more information, see [Manage Copilot in Windows](/windows/client-management/manage-windows-copilot) and [September 2023 - KB5030310](https://support.microsoft.com/kb/5030310)  |

## Management

| Feature | Description |
| ------- | ----------- |
| **Declared configuration protocol** <!--7771694 --> | Declared configuration protocol is a new protocol for device configuration management that's based on a desired state model and uses OMA-DM SyncML protocol. It allows the server to provide the device with a collection of settings for a specific scenario, and the device to handle the configuration request and maintain its state. For more information, see [What is the declared configuration protocol](/windows/client-management/declared-configuration). |
| **Control File Explorer Home Recommended section** <!--8092554, DisableGraphRecentItems, WIP.23475, WIP.23403-->|  **Recommended** section added to File Explorer Home for users signed into Windows with an Azure Active Directory account. </br> **CSP**:./Device/Vendor/MSFT/Policy/Config/FileExplorer/[DisableGraphRecentItems](/windows/client-management/mdm/policy-csp-fileexplorer#disablegraphrecentitems) </br> </br> **Group Policy**: Computer Configuration\Administrative Templates\Windows Components\File Explorer\\**Turn off files from Office.com in Quick Access View**|
| **Control File Explorer Home: Recommended section** <!--8092554, DisableGraphRecentItems, WIP.23475, WIP.23403-->|  **Recommended** section added to File Explorer Home for users signed into Windows with an Azure Active Directory account. </br> **CSP**:./Device/Vendor/MSFT/Policy/Config/FileExplorer/[DisableGraphRecentItems](/windows/client-management/mdm/policy-csp-fileexplorer#disablegraphrecentitems) </br> </br> **Group Policy**: Computer Configuration\Administrative Templates\Windows Components\File Explorer\\**Turn off files from Office.com in Quick Access View**|
| **Control Taskbar Search Button** <!--07525381, 8092554, WIP.25252--> |[Policies to customize Windows 11 taskbar buttons](/windows/configuration/supported-csp-taskbar-windows#csp-policies-to-customize-windows-11-taskbar-buttons) were added to provide you with more control over the taskbar search experience across your organization. |
| **Control Start Menu Recommended section** <!--8092554, WIP.23475-->| The Recommended section of the Start Menu displays personalized website recommendations. </br> **CSP**: ./Device/Vendor/MSFT/Policy/Config/Start/[HideRecoPersonalizedSites](/windows/client-management/mdm/policy-csp-start)</br> </br>**Group Policy**: Computer Configuration\Administrative Templates\Start Menu and Taskbar\\**Remove Personalized Website Recommendations from the Recommended section in the Start Menu**|
| **Temporary enterprise feature control** <!--7790977--> | Controls were added to temporarily disable certain features that were introduced during monthly cumulative updates for managed Windows 11, version 22H2 devices. For more information, see [Temporary enterprise feature control](/windows/whats-new/temporary-enterprise-feature-control). |
| **Copilot in Windows** <!--8138371, 8092554, WIP.23493 --> | Copilot in Windows provides centralized generative AI assistance to your users right from the Windows desktop. For more information, see [Manage Copilot in Windows](/windows/client-management/manage-windows-copilot) and [September 2023 - KB5030310](https://support.microsoft.com/kb/5030310)  |
| **Multi-app kiosk** <!--6444738--> | You can configure a multi-app kiosk, which displays a customized start menu of allowed apps. For more information, see [Set up a multi-app kiosk on Windows 11 devices](/windows/configuration/lock-down-windows-11-to-specific-apps). |

## Security

| Feature | Description |
| ------- | ----------- |
| **Passkeys in Windows** <!--8138341--> | Windows provides a native experience for passkey management. You can use the Settings app to view and manage passkeys saved for apps or websites. For more information, see [Support for passkeys in Windows](/windows/security/identity-protection/passkeys). |
| **Windows passwordless experience** <!--8138336--> | Windows passwordless experience is a security policy that promotes a user experience without passwords on [Microsoft Entra](https://www.microsoft.com/security/business/microsoft-entra?ef_id=_k_910ee369e9a812f6048b86296a6a402c_k_&OCID=AIDcmmdamuj0pc_SEM__k_910ee369e9a812f6048b86296a6a402c_k_&msclkid=910ee369e9a812f6048b86296a6a402c) joined devices. </br>When the policy is enabled, certain Windows authentication scenarios don't offer users the option to use a password, helping organizations and preparing users to gradually move away from passwords. For more information, see [Windows passwordless experience](/windows/security/identity-protection/passwordless-experience/). |
| **Web sign-in for Windows** <!--8344016--> | You can enable a web-based sign-in experience on [Microsoft Entra](https://www.microsoft.com/security/business/microsoft-entra?ef_id=_k_910ee369e9a812f6048b86296a6a402c_k_&OCID=AIDcmmdamuj0pc_SEM__k_910ee369e9a812f6048b86296a6a402c_k_&msclkid=910ee369e9a812f6048b86296a6a402c) joined devices, unlocking new sign-in options and capabilities. For more information, see [Web sign-in for Windows](/windows/security/identity-protection/web-sign-in). |
| **Federated sign-in** <!--7593916, 7593946--> | Federated sign-in is a great way to simplify the sign-in process for your users: instead of having to remember a username and password defined in [Microsoft Entra](https://www.microsoft.com/security/business/microsoft-entra?ef_id=_k_910ee369e9a812f6048b86296a6a402c_k_&OCID=AIDcmmdamuj0pc_SEM__k_910ee369e9a812f6048b86296a6a402c_k_&msclkid=910ee369e9a812f6048b86296a6a402c) ID, they can sign-in using their existing credentials from the IdP. For more information, see [Configure federated sign-in for Windows devices](/education/windows/federated-sign-in). |
| **Windows Hello for Business authentication improvement** <!--7771685--> | Peripheral face and fingerprint sensors can be used for Windows Hello for Business authentication on devices where Enhanced Sign-in Security (Secure Biometrics) has been enabled at the factory. Previously this functionality was blocked. For more information, see [Common questions about Windows Hello for Business](/windows/security/identity-protection/hello-for-business/hello-faq). |
| **LAPS native integration** <!--6399966--> | Use Windows Local Administrator Password Solution (LAPS) to regularly rotate and manage local administrator account passwords. For more information, see [Local Administrator Password Solution (LAPS)](/windows-server/identity/laps/laps-overview) |

## User Experience

| Feature | Description |
| ------- | ----------- |
| **Taskbar: Button Policies** <!--07525381, 8092554, WIP.25252--> |[Policies to customize Windows 11 taskbar buttons](/windows/configuration/supported-csp-taskbar-windows#csp-policies-to-customize-windows-11-taskbar-buttons) were added to provide you with more control over the taskbar search experience across your organization. |
| **Taskbar: overflow menu** | The taskbar offers an entry point to a menu that shows all of your overflowed apps in one spot.<!--kb5019509--> |
| **Taskbar: Optimize for touch** | Taskbar touch optimization is available for devices that can be used as a tablet. Once enabled, the user can switch between a collapsed taskbar, saving screen space, and an expanded taskbar, optimized for touch. The taskbar changes to this optimized version when you disconnect or fold back the keyboard on a 2-in-1 device. To enable or disable this feature on a tablet capable device, go to Settings > Personalization > Taskbar > Taskbar behaviors. </br> See also [February 28, 2023 - KB5022913](https://support.microsoft.com/kb/5022913)  |
| **Start Menu: Recommended section** <!--8092554, WIP.23475-->| The Recommended section of the Start Menu displays personalized website recommendations. </br> **CSP**: ./Device/Vendor/MSFT/Policy/Config/Start/[HideRecoPersonalizedSites](/windows/client-management/mdm/policy-csp-start)</br> </br>**Group Policy**: Computer Configuration\Administrative Templates\Start Menu and Taskbar\\**Remove Personalized Website Recommendations from the Recommended section in the Start Menu**|
| **File Explorer Tabs** <!--kb5019509--> | File Explorer includes tabs to help you organize your File Explorer sessions. |
| **File Explorer Home: Recommended section** <!--8092554, DisableGraphRecentItems, WIP.23475, WIP.23403-->|  **Recommended** section added to File Explorer Home for users signed into Windows with an Azure Active Directory account. </br> **CSP**:./Device/Vendor/MSFT/Policy/Config/FileExplorer/[DisableGraphRecentItems](/windows/client-management/mdm/policy-csp-fileexplorer#disablegraphrecentitems) </br> </br> **Group Policy**: Computer Configuration\Administrative Templates\Windows Components\File Explorer\\**Turn off files from Office.com in Quick Access View**|
| **Task Manager enhancements** <!--kb5019509--> | Process filtering, theme settings, and the ability to opt out of efficiency mode notification were added to Task Manager. |
| **Windows Ink as input** | Windows Ink allows users to handwrite directly onto most editable fields <!--8092554, WIP.23481-->|
| **Uninstall Win32 app** | Selecting **Uninstall** for a Win32 app from the right-click menu uses the **Installed Apps** page in **Settings** rather than **Programs and Features** under the **Control Panel**. <!--[February 28, 2023 - KB5022913](https://support.microsoft.com/topic/february-28-2023-kb5022913-os-build-22621-1344-preview-3e38c0d9-924d-4f3f-b0b6-3bd49b2657b9) --> </br></br> See also [September 2023 - KB5030310](https://support.microsoft.com/kb/5030310)  |
| **Dev Home** <!--8092554, WIP.23506--> | Dev Home is a new app that provides a central location for developers to start building, testing, and deploying Windows apps. For more information, see [Dev Home](/windows/dev-home/). To identify the appx package: `Get-AppxPackage -Name Microsoft.Windows.DevHome` </br> See also [September 2023 - KB5030310](https://support.microsoft.com/kb/5030310) |
| **Dev Drive** | Dev Drive is a new form of storage volume available to improve performance for key developer workloads. For more information, see [Set up a Dev Drive on Windows 11](/windows/dev-drive/) and [September 2023 - KB5030310](https://support.microsoft.com/kb/5030310). |
| **Suggested actions** <!--kb5019509--> | Copied text in certain formats, such as phone numbers or dates, offer suggested actions such as calling the number or adding the event to your calendar. |

## Features Removed

The following [deprecated features](/windows/whats-new/deprecated-features) and [removed features](/windows/whats-new/removed-features) are removed Windows 11, version 23H2:

| Feature | Description |
|---------|-------------|
| **Microsoft Teams** | Chat is being removed from the Microsoft Teams in-box app. Teams is removed from the taskbar for enterprise editions of Windows 11, version 23H2 or later. To identify the appx package: `Get-AppxPackage -Name MicrosoftTeams` <!--8349096--> |

## Related content

- [How to get the Windows 11 2023 Update](https://blogs.windows.com/windowsexperience/?p=178531) | Windows Experience Blog
- [What's new for IT pros in Windows 11, version 23H2](https://aka.ms/new-in-23h2) | Windows IT Pro Blog
- [What's new in Windows 11, version 23H2](/windows/whats-new/whats-new-windows-11-version-23h2)
- [Windows Consumer: What's new in recent Windows updates](https://support.microsoft.com/windows/what-s-new-in-recent-windows-updates-2df971e0-341a-68b1-3bf8-bc3e3ff8c3a5)
- [Windows 11 requirements](/windows/whats-new/windows-11-requirements)
- [Plan for Windows 11](/windows/whats-new/windows-11-plan)
- [Prepare for Windows 11](/windows/whats-new/windows-11-prepare)
- [Windows release health](https://aka.ms/windowsreleasehealth)
- [Windows 11 release information](/windows/release-health/windows11-release-information)
