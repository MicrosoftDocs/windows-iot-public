---
title: What's new in Windows 11 IoT Enterprise, version 22H2?
description: Learn about what's new in Windows 11 IoT Enterprise, version 22H2.
author: TerryWarwick
ms.author: twarwick
ms.date: 05/05/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
keywords: Windows IoT Enterprise, Windows 11, Windows 11 IoT, Windows 11 IoT Enterprise
---

# What's new in Windows 11 IoT Enterprise, version 22H2

## Overview

Windows 11, version 22H2 is a feature update for Windows 11 IoT Enterprise. Windows 11, version 22H2 includes all previous cumulative updates to Windows 11 IoT Enterprise, version 21H2 plus some new and updated features valuable for IoT scenarios.

Windows 11 IoT Enterprise, version 21H2 follows the [Modern Lifecycle Policy](/lifecycle/policies/modern).

| Release | Version | Availability | End of Servicing |
| --- | --- | --- | --- |
| Windows 11 IoT Enterprise, version 21H2 | 22621 | 2022-09-20 | 2025-10-14 |

For more information, see [Windows 11 IoT Enterprise support lifecycle](/lifecycle/products/windows-11-iot-enterprise).

## Availability

Windows 11 IoT Enterprise, version 22H2 is available through Windows Server Update Services (including Configuration Manager), Windows Update for Business, and the Volume Licensing Service Center (VLSC). For more information, see [How to get the Windows 11, version 22H2 update](https://aka.ms/W11/how-to-get-22H2). Review the [Windows 11, version 22H2 Windows IT Pro blog post](https://aka.ms/new-in-22H2) to discover information about available deployment resources such as the [Windows Deployment Kit (Windows ADK)](/windows-hardware/get-started/adk-install).

To learn more about the status of the update rollout, known issues, and new information, see [Windows release health](/windows/release-health/).

## What's new

| Feature | Description |
| --- | --- |
| Microsoft Pluton | Designed by Microsoft and built by silicon partners, Microsoft Pluton is a secure crypto-processor built into the CPU for security at the core to ensure code integrity and the latest protection with updates delivered by Microsoft through Windows Update. Pluton protects credentials, identities, personal data and encryption keys. Information is significantly harder to be removed even if an attacker has installed malware or has complete physical possession Microsoft Pluton can be enabled on devices with Pluton capable processors running Windows 11, version 22H2. </br></br>For more information, see [Microsoft Pluton security processor](/windows/security/information-protection/pluton/microsoft-pluton-security-processor). |
| Enhanced Phishing Protection | Enhanced Phishing Protection in Microsoft Defender SmartScreen helps protect Microsoft passwords against phishing and unsafe usage. Enhanced Phishing Protection works  alongside Windows security protections to help protect Windows 11 sign-in passwords. </br></br>For more information, see [Enhanced Phishing Protection in Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/phishing-protection-microsoft-defender-smartscreen) and [Protect passwords with enhanced phishing protection](https://aka.ms/EnhancedPhishingProtectionBlog) in the Windows IT Pro blog. |
| Smart App Control | **Smart App Control** adds significant protection from malware, including new and emerging threats, by blocking apps that are malicious or untrusted. **Smart App Control** also helps to block potentially unwanted apps, which are apps that may cause your device to run slowly, display unexpected ads, offer extra software you didn't want, or do other things you don't expect. For more information, see [Smart App Control](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control#wdac-and-smart-app-control). |
| Credential Guard | Compatible Windows 11 IoT Enterprise, version 22H2 devices will have **Windows Defender Credential Guard** turned on by default. This changes the default state of the feature in Windows, though system administrators can still modify this enablement state. </br></br> For more information, see [Manage Windows Defender Credential Guard](/windows/security/identity-protection/credential-guard/credential-guard-manage).|
| Malicious and vulnerable driver blocking | The vulnerable driver blocklist is automatically enabled on devices when Smart App Control is enabled and for clean installs of Windows. </br></br> For more information, see [recommended block rules](/windows/security/threat-protection/windows-defender-application-control/microsoft-recommended-block-rules#microsoft-vulnerable-driver-blocklist).|
| Security hardening and threat protection | Windows 11, version 22H2 supports additional protection for the Local Security Authority (LSA) process to prevent code injection that could compromise credentials. For more information, see [Configuring Additional LSA Protection](/windows-server/security/credentials-protection-and-management/configuring-additional-lsa-protection?toc=/windows/security/toc.json&bc=/windows/security/breadcrumb/toc.json). |
| Windows Update notifications | You can now block user notifications for Windows Updates during active hours. This setting is especially useful for organizations that want to prevent Windows Update notifications from occurring during business hours. For more information, see [Control restart notifications](/windows/deployment/update/waas-restart#control-restart-notifications).</br></br> The organization name now appears in the Windows Update notifications when Windows clients are associated with an Azure Active Directory tenant. For more information, see [Display organization name in Windows Update notifications](/windows/deployment/update/waas-wu-settings#bkmk_display-name). |
| Start menu layout | Windows 11 IoT Enterprise, version 22H2 now supports additional CSPs for customizing the start menu layout. These CSPs allow you to hide the app list and disable context menus. </br></br> For more information, see [Supported configuration service provider (CSP) policies for Windows 11 Start menu](/windows/configuration/supported-csp-start-menu-layout-windows#existing-windows-csp-policies-that-windows-11-supports). |
| Improvements to task manager | A new command bar was added to each page to give access to common actions. Task Manager will automatically match the system wide theme configured in **Windows Settings**. Added an efficiency mode that allows you to limit the resource usage of a process.|
| Windows accessibility | Windows 11, version 22H2, includes additional improvements for people with disabilities: system-wide live captions, Focus sessions, voice access, and more natural voices for Narrator. </br></br> For more information, see [New accessibility features coming to Windows 11](https://blogs.windows.com/windowsexperience/2022/05/10/new-accessibility-features-coming-to-windows-11/) and [How inclusion drives innovation in Windows 11](https://blogs.windows.com/windowsexperience/?p=177554). For more information, see [Accessibility information for IT professionals](/windows/configuration/windows-10-accessibility-for-itpros). |
|  High Efficiency Video Coding (HEVC) support | Starting in Windows 11, version 22H2, support for High Efficiency Video Coding (HEVC) is now available. \HEVC is designed to take advantage of hardware capabilities on some newer devices to support 4K and Ultra HD content. </br></br>  For devices that don't have hardware support for HEVC videos, software support is provided, but the playback experience might vary based on the video resolution and your devices performance.

## Related Topics

- [Windows 11 requirements](/windows/whats-new/windows-11-requirements)
- [Plan for Windows 11](/windows/whats-new/windows-11-plan)
- [Prepare for Windows 11](/windows/whats-new/windows-11-prepare)
- [Windows release health](https://aka.ms/windowsreleasehealth)
- [Windows 11 release information](/windows/release-health/windows11-release-information)
- [Windows 11, version 22H2 update history](https://support.microsoft.com/topic/windows-11-version-22h2-update-history-ec4229c3-9c5f-4e75-9d6d-9025ab70fcce)
