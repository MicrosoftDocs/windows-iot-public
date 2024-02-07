---
title: What's new in Windows 11 IoT Enterprise LTSC 2024
titleSuffix: Windows IoT Enterprise
description: Learn about new and updated features that are of interest to device makers and IT Pros working with Windows 11 IoT Enterprise LTSC 2024.
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
author: TerryWarwick
ms.author: twarwick
ms.date: 02/07/2024
---

# What's new in Windows 11 Enterprise LTSC 2024

> [!WARNING]
> THIS IS AN IN-PROGRESS ROUGH DRAFT. The wording and feature list may change before publishing.

## Overview

Windows IoT Enterprise LTSC is designed for specialty devices and use cases where functionality and features remain constant for the life of the device.  These devices are typically found in industries including, but not limited to, banking, healthcare, hospitality, manufacturing and retail. Devices that require regulatory certification and devices that perform a critical business function, which can't accept feature updates for years at a time.  

We designed Windows IoT Enterprise LTSC with these use cases in mind. We support each Windows IoT Enterprise LTSC release for 10 years, and that features and functionality don't change over the course of that 10-year lifecycle.

Every new Windows release comes exciting new features and capabilities - **Windows 11 IoT Enterprise LTSC 2024** is no different. This article provides a high level overview of notable updates in this release that are of interest to device makers and IT Pros.

### Availability

Windows 11 IoT Enterprise LTSC 2024 is available for Windows IoT Enterprise device makers through an authorized [Windows IoT Distributor](../windows-iot-distributors.md) for building new devices. Windows IoT Enterprise is intended for fixed purpose devices with specific allowances and restrictions in the license agreement. For more information, see [Licensing and Usage](/windows/iot/iot-enterprise/commercialization/licensing) or contact an authorized [Windows IoT Distributor](../windows-iot-distributors.md) for further assistance.

### Upgrade

Upgrading from one version of Windows IoT Enterprise LTSC to the next version requires a new license. If your device came preinstalled with a previous version of Windows IoT Enterprise LTSC, contact your device maker to see if they offer upgrades for your device.

### Servicing Lifecycle

Windows 11 IoT Enterprise LTSC 2024 continues to offer a 10-year support lifecycle, which includes quality updates distributed via Windows Update monthly.

Windows 11 IoT Enterprise LTSC 2024 follows the [Fixed Lifecycle Policy](/lifecycle/policies/fixed).

| Version | Build  | Availability | End of Servicing |
| --- | --- | --- | --- |
| 2024 | TBD | ~Q2 CY2024 | ~Q1 CY2035 |

For more information, see [Windows 11 IoT Enterprise LTSC 2024 support lifecycle](/lifecycle/products/windows-11-iot-enterprise-ltsc-2024).

## Windows IoT Spotlight

Windows 11 IoT Enterprise LTSC 2024 release includes the cumulative enhancements provided by the following annual releases:

- [Windows 11 IoT Enterprise, version 21H2](Windows-11-IoT-Enterprise-21H2.md)
- [Windows 11 IoT Enterprise, version 22H2](Windows-11-IoT-Enterprise-22H2.md)
- [Windows 11 IoT Enterprise, version 23H2](Windows-11-IoT-Enterprise-23H2.md)
- [Windows 11 IoT Enterprise, version 24H2](Windows-11-IoT-Enterprise-24H2.md)

| Feature | Description |
| --- | --- |
| **Hardware Requirements** | System hardware requirement have been updated to provide more flexibility to device makers.  For more information, see [Minimum Hardware Requirements for Windows IoT Enterprise](../Hardware/Hardware_Requirements.md) |
| **Restricted User Experience** </br> [23H2] <!--6444738--> | <!-- You can configure a multi-app kiosk, which displays a customized start menu of allowed apps. For more information, see [Set up a multi-app kiosk on Windows 11 devices](/windows/configuration/lock-down-windows-11-to-specific-apps). --> |
| **Removable Packages** | Removable package support for Windows IoT Enterprise LTSC has expanded from 20 to 36 removable packages.  For more information, see [Removable Packages](../Optimize/Removable-Packages.md). |
| **Wireless Display** | The Wireless Display optional feauture is now available for Windows 11 IoT Enterprise LTSC, allowing other devices to wirelessly project to a device running Windows 11 IoT Enterprise LTSC.  Requires Miracast-compatable hardware.  For more information, see [Screen mirroring and projecting to your PC](https://support.microsoft.com/en-us/windows/screen-mirroring-and-projecting-to-your-pc-5af9f371-c704-1c7f-8f0d-fa607551d09c). |

## Accessibility

| Feature | Description |
| --- | --- |
| **Windows accessibility** </br> [22H2] | Improvements for people with disabilities: system-wide live captions, Focus sessions, voice access, and more natural voices for Narrator. </br> For more information, see:</br>&nbsp;&nbsp;• [New accessibility features coming to Windows 11](https://blogs.windows.com/windowsexperience/2022/05/10/new-accessibility-features-coming-to-windows-11/)</br>&nbsp;&nbsp;• [How inclusion drives innovation in Windows 11](https://blogs.windows.com/windowsexperience/?p=177554)</br>&nbsp;&nbsp;• [Accessibility information for IT professionals](/windows/configuration/windows-10-accessibility-for-itpros). |
| **Braille displays**  </br> [23H2] <!--7579823-->        | Braille displays work seamlessly and reliably across multiple screen readers, improving the end user experience. We also added support for new braille displays and new braille input and output languages in Narrator. For more information, see [Accessibility information for IT professionals](/windows/configuration/windows-accessibility-for-ITPros). |
| **Narrator improvements**  </br> [23H2] <!--kb5019509--> | Scripting functionality was added to Narrator. Narrator includes more natural voices. For more information, see [Complete guide to Narrator](https://support.microsoft.com/en-us/windows/complete-guide-to-narrator-e4397a0d-ef4f-b386-d8ae-c172f109bdb1)<!--8138352, 8138357--> |

## Applications

Windows 11 IoT Enterprise is built on the same foundation as Windows 10 IoT Enterprise. Typically, you can use the same tools and solutions you use today to deploy, manage, and secure your Windows 11 IoT Enterprise device. Your current management tools and processes to manage monthly quality updates for both Windows 10 IoT Enterprise and Windows 11 IoT Enterprise devices.

Windows 11 IoT Enterprise preserves the application compatibility promise made with Windows operating systems. Windows 11 IoT Enterprise doesn't require changes to existing support processes or tooling to sustain the currency of applications and devices.

Most accessories and associated drivers that work with Windows 10 IoT Enterprise are expected to work with Windows 11 IoT Enterprise. Check with your accessory manufacturer for specific details.

| Feature | Description |
| --- | --- |
| **Internet Explorer** | Internet Explorer (IE) is no longer available in Windows 11 IoT Enterprise LTSC 2024, however you can use IE Mode if a website needs Internet Explorer. For more information, see [Internet Explorer (IE) Mode](/deployedge/edge-ie-mode) |
| **Microsoft Edge** </br> [21H2] | The Microsoft Edge browser is the default browser. For information about configuring Microsoft Edge on Windows, see [Configure Microsoft Edge policy settings on Windows devices](/deployedge/configure-microsoft-edge). |
| **Support for existing Windows apps on Arm** | Windows on Arm runs native Arm apps, and many unmodified x86 & x64 apps, but for the best performance and battery life, apps should be built to be Arm-native wherever possible. For more information, see [Windows on ARM processor](/windows/arm/overview)|
| **Arm64EC (“Emulation Compatible”)** | Arm64EC (“Emulation Compatible”) enables you to build new native apps or incrementally transition existing x64 apps to take advantage of the native speed and performance possible with Arm-powered devices, including better power consumption, battery life, and accelerated AI & ML workloads. For more information, see [Arm64EC - Build and port apps for native performance on Arm](/windows/arm/arm64ec)|

## Security

The security and privacy features in Windows 11 are similar to Windows 10. Security for your devices starts with the hardware, and includes OS security, application security, and user & identity security. There are features available in the Windows OS to help in these areas. This section describes some of these features. For a more comprehensive view, including zero trust, see [Windows security](/windows/security/).

| Feature | Description |
| --- | --- |
| **Windows Security app** </br> [21H2] | Windows Security app is an easy-to-use interface, and combines commonly used security features. For example, your get access to virus & threat protection, firewall & network protection, account protection, and more. For more information, see [the Windows Security app](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center). |
| **Security baselines** </br> [21H2] | Security baselines include security settings that are already configured, and ready to be deployed to your devices. If you don't know where to start, or it's too time consuming to go through all the settings, then you should look at Security Baselines. For more information, see [Windows security baselines](/windows/security/threat-protection/windows-security-configuration-framework/windows-security-baselines). |
| **Microsoft Defender Antivirus** </br> [21H2] | Microsoft Defender Antivirus helps protect devices using next-generation security. When used with Microsoft Defender for Endpoint, your organization gets strong endpoint protection, and advanced endpoint protection & response. If you use Intune to manage devices, then you can create policies based on threat levels in Microsoft Defender for Endpoint. For more information, see:</br>&nbsp;&nbsp;• [Microsoft Defender Antivirus](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-windows)</br>&nbsp;&nbsp;• [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)</br>&nbsp;&nbsp;• [Enforce compliance for Microsoft Defender for Endpoint](/mem/intune/protect/advanced-threat-protection) |
| **Application Security** </br> [21H2] | The Application Security features help prevent unwanted or malicious code from running, isolate untrusted websites & untrusted Office files, protect against phishing or malware websites, and more. For more information, see  [Windows application security](/windows/security/apps). |
| **Microsoft Pluton** </br> [22H2] | Designed by Microsoft and built by silicon partners, Microsoft Pluton is a secure crypto-processor built into the CPU for security at the core to ensure code integrity and the latest protection with updates delivered by Microsoft through Windows Update. Pluton protects credentials, identities, personal data and encryption keys. Information is harder to be removed even if an attacker installed malware or has complete physical possession. For more information, see [Microsoft Pluton security processor](/windows/security/information-protection/pluton/microsoft-pluton-security-processor). |
| **Enhanced Phishing Protection** </br> [22H2] | Enhanced Phishing Protection in Microsoft Defender SmartScreen helps protect Microsoft passwords against phishing and unsafe usage. Enhanced Phishing Protection works alongside Windows security protections to help protect sign-in passwords. For more information, see:</br>&nbsp;&nbsp;• [Enhanced Phishing Protection in Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/phishing-protection-microsoft-defender-smartscreen)</br>&nbsp;&nbsp;• [Protect passwords with enhanced phishing protection](https://aka.ms/EnhancedPhishingProtectionBlog) in the Windows IT Pro blog. |
| **Smart App Control** </br> [22H2] | Smart App Control adds significant protection from malware, including new and emerging threats, by blocking apps that are malicious or untrusted. Smart App Control helps block potentially unwanted apps that make your device run slowly, display unexpected ads, offer extra software you didn't want, or do other things you don't expect. For more information, see [Smart App Control](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control#wdac-and-smart-app-control). |
| **Credential Guard** </br> [22H2] | Credential Guard, enabled by default, uses Virtualization-based security (VBS) to isolate secrets so that only privileged system software can access them. Unauthorized access to these secrets can lead to credential theft attacks like pass the hash and pass the ticket. For more information, see [Configure Credential Guard](/windows/security/identity-protection/credential-guard/configure).|
| **Malicious and vulnerable driver blocking** </br> [22H2] | The vulnerable driver blocklist is automatically enabled on devices when Smart App Control is enabled and for clean installs of Windows. For more information, see [recommended block rules](/windows/security/threat-protection/windows-defender-application-control/microsoft-recommended-block-rules#microsoft-vulnerable-driver-blocklist).|
| **Security hardening and threat protection** </br> [22H2] | Enhanced support with Local Security Authority (LSA) to prevent code injection that could compromise credentials. For more information, see [Configuring Additional LSA Protection](/windows-server/security/credentials-protection-and-management/configuring-additional-lsa-protection?toc=/windows/security/toc.json&bc=/windows/security/breadcrumb/toc.json). |
| **Passkeys in Windows** </br> [23H2] <!--8138341--> | Windows provides a native experience for passkey management. You can use the Settings app to view and manage passkeys saved for apps or websites. For more information, see [Support for passkeys in Windows](/windows/security/identity-protection/passkeys). |
| **Windows passwordless experience** </br> [23H2] <!--8138336--> | Windows passwordless experience is a security policy that promotes a user experience without passwords on [Microsoft Entra](https://www.microsoft.com/security/business/microsoft-entra?ef_id=_k_910ee369e9a812f6048b86296a6a402c_k_&OCID=AIDcmmdamuj0pc_SEM__k_910ee369e9a812f6048b86296a6a402c_k_&msclkid=910ee369e9a812f6048b86296a6a402c) joined devices. </br>When the policy is enabled, certain Windows authentication scenarios don't offer users the option to use a password, helping organizations and preparing users to gradually move away from passwords. For more information, see [Windows passwordless experience](/windows/security/identity-protection/passwordless-experience/). |
| **Web sign-in for Windows** </br> [23H2] <!--8344016--> | You can enable a web-based sign-in experience on [Microsoft Entra](https://www.microsoft.com/security/business/microsoft-entra?ef_id=_k_910ee369e9a812f6048b86296a6a402c_k_&OCID=AIDcmmdamuj0pc_SEM__k_910ee369e9a812f6048b86296a6a402c_k_&msclkid=910ee369e9a812f6048b86296a6a402c) joined devices, unlocking new sign-in options and capabilities. For more information, see [Web sign-in for Windows](/windows/security/identity-protection/web-sign-in). |
| **Federated sign-in** </br> [23H2] <!--7593916, 7593946--> | Federated sign-in is a great way to simplify the sign-in process for your users: instead of having to remember a username and password defined in [Microsoft Entra](https://www.microsoft.com/security/business/microsoft-entra?ef_id=_k_910ee369e9a812f6048b86296a6a402c_k_&OCID=AIDcmmdamuj0pc_SEM__k_910ee369e9a812f6048b86296a6a402c_k_&msclkid=910ee369e9a812f6048b86296a6a402c) ID, they can sign-in using their existing credentials from the federated identity provider. For more information, see [Configure federated sign-in for Windows devices](/education/windows/federated-sign-in). |
| **Windows Hello for Business authentication improvement** </br> [23H2] <!--7771685--> | Peripheral face and fingerprint sensors can be used for Windows Hello for Business authentication on devices where Enhanced Sign-in Security (Secure Biometrics) has been enabled at the factory. For more information, see [Common questions about Windows Hello for Business](/windows/security/identity-protection/hello-for-business/hello-faq). |
| **LAPS native integration** </br> [23H2] <!--6399966--> | Use Windows Local Administrator Password Solution (LAPS) to regularly rotate and manage local administrator account passwords. For more information, see [Local Administrator Password Solution (LAPS)](/windows-server/identity/laps/laps-overview) |

## Servicing

Like Windows 10, Windows 11 IoT Enterprise LTSC 2024 receives monthly quality updates. Some updates are large, and use bandwidth. </br>

| Feature | Description |
| --- | --- |
| **Windows Updates and Delivery optimization** </br> [21H2] | Delivery optimization helps reduce bandwidth consumption. It shares the work of downloading the update packages with multiple devices in your deployment. Windows 11 updates are smaller, as they only pull down source files that are different. You can create policies that configure delivery optimization settings. For example, set the maximum upload and download bandwidth, set caching sizes, and more. For more information, see:</br>&nbsp;&nbsp;• [Delivery Optimization for Windows updates](/windows/deployment/update/waas-delivery-optimization)</br>&nbsp;&nbsp;• [Installation & updates](https://support.microsoft.com/office/installation-updates-2f9c1819-310d-48a7-ac12-25191269903c#PickTab=Windows_11)</br>&nbsp;&nbsp;• [Manage updates in Windows](https://support.microsoft.com/windows/manage-updates-in-windows-643e9ea7-3cf6-7da6-a25c-95d4f7f099fe)|
| **Control Windows Update notifications** </br> [22H2] | You can now block user notifications for Windows Updates during active hours. This setting is especially useful for organizations that want to prevent Windows Update notifications from occurring during business hours. For more information, see [Control restart notifications](/windows/deployment/update/waas-restart#control-restart-notifications).|
| **Organization name in update notifications** |The organization name now appears in the Windows Update notifications when Windows clients are associated with a Microsoft Entra ID tenant. For more information, see [Display organization name in Windows Update notifications](/windows/deployment/update/waas-wu-settings#bkmk_display-name). |

## Management

| Feature | Description |
| --- | --- |
| **Microsoft Intune** </br> [21H2] | Microsoft Intune is a mobile application management (MAM) and mobile device management (MDM) provider. It helps manage devices, and manage apps on devices in your organization. You configure policies, and then deploy these policies to users and groups. You can create and deploy policies that install apps, configure device features, enforce PIN requirements, block compromised devices, and more. </br></br>  If you use Group Policy to manage your Windows 10 devices, then you can also use Group Policy to manage Windows 11 devices. In Intune, there are [administrative templates](/mem/intune/configuration/administrative-templates-windows) and the [settings catalog](/mem/intune/configuration/settings-catalog) that include many of the same policies. [Group Policy analytics](/mem/intune/configuration/group-policy-analytics) analyze your on-premises group policy objects. |
| **Control Windows Update notifications** </br> [22H2] | You can now block user notifications for Windows Updates during active hours. This setting is especially useful for organizations that want to prevent Windows Update notifications from occurring during business hours. For more information, see [Control restart notifications](/windows/deployment/update/waas-restart#control-restart-notifications).|
| **Organization name in update notifications** |The organization name now appears in the Windows Update notifications when Windows clients are associated with a Microsoft Entra ID tenant. For more information, see [Display organization name in Windows Update notifications](/windows/deployment/update/waas-wu-settings#bkmk_display-name). |
| **Start menu layout** </br> [22H2] | New Configuration Service Providers (CSPs) for customizing the start menu layout. These CSPs allow you to hide the app list and disable context menus. For more information, see [Supported configuration service provider (CSP) policies for Windows 11 Start menu](/windows/configuration/supported-csp-start-menu-layout-windows#existing-windows-csp-policies-that-windows-11-supports). |
| **Declared configuration protocol** </br> [23H2] <!--7771694 --> | Declared configuration protocol is a new protocol for device configuration management that's based on a desired state model and uses OMA-DM SyncML protocol. It allows the server to provide the device with a collection of settings for a specific scenario, and the device to handle the configuration request and maintain its state. For more information, see [What is the declared configuration protocol](/windows/client-management/declared-configuration).|
| **Control File Explorer Home Recommended section** </br> [23H2] <!--8092554, DisableGraphRecentItems, WIP.23475, WIP.23403-->|  Configure the Recommended section added to File Explorer Home for users signed into Windows with a Microsoft Entra ID account. For more information, see [DisableGraphRecentItems](/windows/client-management/mdm/policy-csp-fileexplorer#disablegraphrecentitems). </br> To configure using Local Group Policy Editor, see `Computer Configuration\Administrative Templates\Windows Components\File Explorer\Turn off files from Office.com in Quick Access View`.|
| **Taskbar Button Policies**  </br> [23H2] <!--07525381, 8092554, WIP.25252--> | Policies to customize taskbar buttons were added to provide you with more control over the taskbar search experience across your organization. For more information, see [Supported taskbar CSPs](/windows/configuration/supported-csp-taskbar-windows).|
| **Control Start Menu Recommended section**  </br> [23H2] <!--8092554, WIP.23475-->| Configure the Recommended section of the Start Menu, which displays personalized website recommendations. For more information, see [HideRecoPersonalizedSites](/windows/client-management/mdm/policy-csp-start). </br>To configure using Local Group Policy Editor, see `Computer Configuration\Administrative Templates\Start Menu and Taskbar\Remove Personalized Website Recommendations from the Recommended section in the Start Menu`.|

## User Experience

| Feature | Description |
| --- | --- |
| **Task Manager**  </br> [22H2]/[23H2] | A new command bar was added to each page to give access to common actions. Task Manager matches the system wide theme configured in Windows Settings. Added an efficiency mode that allows you to limit the resource usage of a process. </br> <!--kb5019509--> Process filtering, theme settings, and the ability to opt out of efficiency mode notification were added to Task Manager. |
| **Taskbar overflow menu**  </br> [23H2] | The taskbar offers an entry point to a menu that shows all of your overflowed apps in one spot.<!--kb5019509--> |
| **Taskbar Optimize for touch**  </br> [23H2] | Taskbar touch optimization is available for devices that can be used as a tablet. Once enabled, the user can switch between a collapsed taskbar, saving screen space, and an expanded taskbar, optimized for touch. The taskbar changes to this optimized version when you disconnect or fold back the keyboard on a 2-in-1 device. To enable or disable this feature on a tablet capable device, go to Settings > Personalization > Taskbar > Taskbar behaviors. See also [February 28, 2023 - KB5022913](https://support.microsoft.com/kb/5022913)  |
| **File Explorer Tabs** </br> [23H2] <!--kb5019509--> | File Explorer includes tabs to help you organize your File Explorer sessions. |
| **Windows Ink as input** </br> [23H2] | Windows Ink allows users to handwrite directly onto most editable fields <!--8092554, WIP.23481-->|
| **Uninstall Win32 app** </br> [23H2] | Selecting Uninstall for a Win32 app from the right-click menu uses the Installed Apps page in Settings rather than Programs and Features in Control Panel. <!--[February 28, 2023 - KB5022913](https://support.microsoft.com/topic/february-28-2023-kb5022913-os-build-22621-1344-preview-3e38c0d9-924d-4f3f-b0b6-3bd49b2657b9) --> For more information, see [September 2023 - KB5030310](https://support.microsoft.com/kb/5030310)  |
| **Dev Drive** </br> [23H2] | Dev Drive is a new form of storage volume available to improve performance for key developer workloads. For more information, see [Set up a Dev Drive on Windows 11](/windows/dev-drive/) and [September 2023 - KB5030310](https://support.microsoft.com/kb/5030310). |
|  **High Efficiency Video Coding (HEVC) support**  </br> [22H2] | HEVC is designed to take advantage of hardware capabilities on some newer devices to support 4K and Ultra HD content. For devices that don't have hardware support for HEVC videos, software support is provided, but the playback experience might vary based on the video resolution and your devices performance. |

## Related articles

- [Release History](Release-History.md)
- [Minimum Hardware Requirements](../Hardware/Hardware_Requirements.md)
- [Windows IoT Distributors](../windows-iot-distributors.md)
