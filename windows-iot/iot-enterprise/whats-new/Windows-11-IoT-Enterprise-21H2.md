---
title: What's new in Windows 11 IoT Enterprise, version 21H2?
description: Learn about what's new in Windows 11 IoT Enterprise, version 21H2.
author: TerryWarwick
ms.author: twarwick
ms.date: 08/10/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
keywords: Windows IoT Enterprise, Windows 11, Windows 11 IoT, Windows 11 IoT Enterprise
---

# What's new in Windows 11 IoT Enterprise, version 21H2

## Overview

Windows 11 IoT Enterprise, version 21H2 is the next evolution of Windows for IoT and it is build on the same foundation as Windows 10.  Investments you have made in tools for update and device management are carried forward.  Many of the same applications and tools that you used in Windows 10 IoT Enterprise can be use in Windows 11 IoT Enterprise. many of the same security settings and policies can also be applied to Windows 11 IoT Enterprise devices.  

Windows 11 IoT Enterprise follows the [Modern Lifecycle Policy](/lifecycle/policies/modern).

| Release | Version | Availability | End of Servicing |
| --- | --- | --- | --- |
| Windows 11 IoT Enterprise, version 21H2 | 22000 | 2021-10-04 | 2024-10-08 |

For more information, see [Windows 11 IoT Enterprise support lifecycle](/lifecycle/products/windows-11-iot-enterprise).

### Windows 11 Supported Processor Lists

- [Intel](/windows-hardware/design/minimum/supported/windows-11-supported-intel-processors)
- [Qualcomm](/windows-hardware/design/minimum/supported/windows-11-supported-qualcomm-processors)
- [AMD](/windows-hardware/design/minimum/supported/windows-11-supported-amd-processors)

## Availability

Windows 11 IoT Enterprise, version 21H2 is available for Windows IoT Enterprise device makers through an authorized [Windows IoT Distributor](https://aka.ms/IoTDistributorList) for building new devices. Windows IoT Enterprise is intended for fixed purpose devices with specific allowances and restrictions in the license agreement. To learn more, see [Licensing and Usage](/windows/iot/iot-enterprise/commercialization/licensing) contact an authorized [Windows IoT Distributor](https://aka.ms/IoTDistributorList) for additional guidance.

Windows 11, version 21H2 is also available to users with devices running Windows 10 IoT Enterprise, version 20H2 or later who are interested in the latest features and are ready to install this release on their device if the hardware ....

. If you would like to install the new release, open your Windows Update settings (**Settings > Update & Security > Windows Update**) and select **Check for updates**. Eligible devices may also be offered the option to choose to upgrade to Windows 11. If the update appears, you can simply select Download and install to get started. Once the download is complete and the feature update is ready to install, we’ll notify you so that you can pick a convenient time to finish the installation and reboot your device, ensuring that the update does not disrupt your activities. To learn more about the status of the 2022 Update rollout, known issues and new information, visit .

Windows 11 IoT Enterprise will be delivered as an upgrade to eligible devices running Windows 10 IoT Enterprise, beginning on October 5, 2021.

For administrators managing devices on behalf of their organization, Windows 11 IoT Enterprise will be available through the same, familiar channels that you use today for Windows 10 IoT Enterprise feature updates. You will be able to use existing deployment and management tools, such as Windows Update for Business, and Microsoft Endpoint Manager. For more information, see [Plan for Windows 11](/windows/whats-new/windows-11-plan).

For devices that are not managed by an organization, the Windows 11 upgrade will be offered to eligible Windows 10 devices through Windows Update using Microsoft's intelligent rollout process to ensure a smooth upgrade experience.

For more information about device eligibility, see [Windows 11 requirements](/windows/whats-new/windows-11-requirements) and [Getting ready for the Windows 11 upgrade](https://aka.ms/upgradetowindows11).

## Licensing

The licensing requirements for Windows 11 IoT Enterprise devices are identical to what is required for Windows 10 IoT Enterprise devices.

Windows 11 IoT Enterprise will only be available as an [annual release](/lifecycle/faq/windows#windows-11). Please contact your [Windows IoT distributor](https://aka.ms/IoTDistributorList) for more information.

## Compatibility

Most accessories and associated drivers that work with Windows 10 IoT Enterprise are expected to work with Windows 11 IoT Enterprise. Check with your accessory manufacturer for specific details.

As mentioned above, Windows 11 IoT Enterprise preserves the application compatibility promise made with Windows operating systems, and does not require changes to existing support processes or tooling to sustain the currency of applications and devices.

## Familiar processes

Windows 11 IoT Enterprise is built on the same foundation as Windows 10 IoT Enterprise. Typically, you can use the same tools and solutions you use today to deploy, manage, and secure your Windows 11 IoT Enterprise device. Your current management tools and processes will also work to manage monthly quality updates for both Windows 10 IoT Enterprise and Windows 11 IoT Enterprise devices.

> [!TIP]
>
> Please see [Prepare for Windows 11](/windows/whats-new/windows-11-prepare#infrastructure-and-tools) for more details on infrastructure and tools nuanced differences in regards to [on-premises solutions (WSUS)](/windows/whats-new/windows-11-prepare#on-premises-solutions) or [Cloud-based solutions](/windows/whats-new/windows-11-prepare#cloud-based-solutions).

## Servicing

Like Windows 10 IoT Enterprise, Windows 11 IoT Enterprise will receive monthly quality updates. However, it will have a new feature update cadence. The semi-annual update cadence for Windows 10 IoT Enterprise will remain, but starting with Windows 11 IoT Enterprise, there will only be one release a year.  

Important servicing-related announcements and information about known issues and safeguard holds can be found on the [Windows release health hub](https://aka.ms/windowsreleasehealth). For more information, see [Servicing and support](/windows/whats-new/windows-11-plan#servicing-and-support).

> [!NOTE]
>
> Microsoft does not publish feature updates through Windows Update for devices running Windows 10 IoT Enterprise LTSC.
>
> Microsoft releases new LTSC editions every 2–3 years. OEMs may purchase a newer LTSC as a field upgrade for their devices, if appropriate. Please contact your [Windows IoT Distributor](https://aka.ms/IoTDistributorList) for more information.

## New Features and Functionality Updates

With every new operating system, comes exciting new features and capabilities - Windows 11 IoT Enterprise is no different.

> [!NOTE]
> Multi-app kiosk mode is not available for Windows 11 IoT Enterprise, version 21H2.  Please refer to What's new about subsequent releases for information about its return.
>
> **Update** - [Multi-app kiosk mode is now available in Windows 11](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/multi-app-kiosk-mode-now-available-in-windows-11/ba-p/3845558)., version 22H2 as part of the Windows continuous innovation releases.  To learn how you can take advantage of features introduced via Windows continuous innovation, see more about how you can access this feature in Windows 11 IoT Enterprise, version 22H2, see [Delivering continuous innovation in Windows 11](https://support.microsoft.com/windows/delivering-continuous-innovation-in-windows-11-b0aa0a27-ea9a-4365-9224-cb155e517f12).

### Security and scanning

The security and privacy features in Windows 11 are similar to Windows 10. Security for your devices starts with the hardware, and includes OS security, application security, and user & identity security. There are features available in the Windows OS to help in these areas. This section describes some of these features. For a more comprehensive view, including zero trust, see [Windows security](/windows/security/).

| Feature | Description |
| --- | --- |
| **Windows Security app** | Windows Security app is built into the OS. This app is an easy-to-use interface, and combines commonly used security features. For example, your get access to virus & threat protection, firewall & network protection, account protection, and more. </br></br> For more information, see [the Windows Security app](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center). |
|**Security baselines** | Security baselines includes security settings that already configured, and ready to be deployed to your devices. If you don't know where to start, or it's too time consuming to go through all the settings, then you should look at Security Baselines.  </br></br> For more information, see [Windows security baselines](/windows/security/threat-protection/windows-security-configuration-framework/windows-security-baselines). |
|**Microsoft Defender Antivirus** | Microsoft Defender Antivirus is built into Windows, and helps protect devices using next-generation security. When used with Microsoft Defender for Endpoint, your organization gets strong endpoint protection, and advanced endpoint protection & response. If you use Intune to manage devices, then you can create policies based on threat levels in Microsoft Defender for Endpoint.  </br></br> For more information, see: </br> - [Microsoft Defender Antivirus](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-windows)  </br> - [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint) </br> - [Enforce compliance for Microsoft Defender for Endpoint](/mem/intune/protect/advanced-threat-protection) |
| **Application Security** | The Application Security features help prevent unwanted or malicious code from running, isolate untrusted websites & untrusted Office files, protect against phishing or malware websites, and more. </br></br> For more information, see  [Windows application security](/windows/security/apps). |

### Use your same apps, and new apps, improved

| Feature | Description |
| --- | ---|
| **App Compatibility** | Your Windows 10 apps will also work on Windows 11. **[App Assure](https://www.microsoft.com/fasttrack/microsoft-365/app-assure)** is also available if there are some issues. </br></br>   You can continue to use **MSIX packages** for your UWP, Win32, WPF, and WinForm desktop application files. Continue to use **Windows Package Manager** to install Windows apps. You can create **Azure virtual desktops** that run Windows 11. Use **Azure Virtual desktop with MSIX app attach** to virtualize desktops and apps. </br></br> For more information on these features, see [Overview of apps on Windows devices](/windows/application-management/apps-in-windows-10).
| |   Using an MDM provider, like Intune, you can create policies that also manage some app settings. For a list of settings, see [App Store in Intune](/mem/intune/configuration/device-restrictions-windows-10#app-store). |
| **Windows Terminal app** | This app is included with the OS. On previous Windows versions, it's a separate download in the Microsoft Store. For more information, see [What is Windows Terminal?](/windows/terminal/). </br></br> This app combines Windows PowerShell, a command prompt, and Azure Cloud Shell all within the same terminal window. You don't need to open separate apps to use these command-line applications. It has tabs. And when you open a new tab, you can choose your command-line application:
|**Microsoft Edge** | The Microsoft Edge browser is included with the OS, and is the default browser. Internet Explorer (IE) isn't available in Windows 11. In Microsoft Edge, you can use IE Mode if a website needs Internet Explorer. Open Microsoft Edge, and enter `edge://settings/defaultBrowser` in the URL. </br></br> To save system resources, Microsoft Edge uses sleeping tabs. Users can configure these settings, and more, in `edge://settings/system`. </br></br> Using Group Policy or an MDM provider, such as Intune, you can configure some Microsoft Edge settings. For more information, see [Microsoft Edge - Policies](/deployedge/microsoft-edge-policies) and [Configure Microsoft Edge policy settings](/mem/intune/configuration/administrative-templates-configure-edge).

### Deployment and servicing

| Feature | Description |
| --- | ---|
| **Installation** | The same methods you use to install Windows 10 Iot Enterprise can also be used to install Windows 11 IoT Enterprise. For example, you can deploy Windows to your devices using Microsoft Deployment Toolkit (MDT), Configuration Manager, and more. Windows 11 IoT Enterprise will be delivered as an upgrade to eligible devices running Windows 10 IoT Enterprise. </br></br>   For more information on getting started, see [Windows client deployment resources and documentation](/windows/deployment/) and [Plan for Windows 11](/windows/whats-new/windows-11-plan). </br></br>  For more information on the end-user experience, see [Ways to install Windows 11](https://support.microsoft.com/windows/e0edbbfb-cfc5-4011-868b-2ce77ac7c70e). |
| **Microsoft Intune** | Microsoft Intune is a mobile application management (MAM) and mobile device management (MDM) provider. It helps manage devices, and manage apps on devices in your organization. You configure policies, and then deploy these policies to users and groups. You can create and deploy policies that install apps, configure device features, enforce PIN requirements, block compromised devices, and more. </br></br>  If you use Group Policy to manage your Windows 10 devices, then you can also use Group Policy to manage Windows 11 devices. In Intune, there are [administrative templates](/mem/intune/configuration/administrative-templates-windows) and the [settings catalog](/mem/intune/configuration/settings-catalog) that include many of the same policies. [Group Policy analytics](/mem/intune/configuration/group-policy-analytics) analyze your on-premises group policy objects. |
| **Windows Updates and Delivery optimization** | Windows Updates and Delivery optimization helps manage updates, and manage features on your devices. Starting with Windows 11, the OS feature updates are installed annually. For more information on servicing channels, and what they are, see [Servicing channels](/windows/deployment/update/waas-overview#servicing-channels). </br></br> Like Windows 10, Windows 11 will receive monthly quality updates. </br></br> You have options to install updates on your Windows devices, including Intune, Group Policy, Windows Server Update Services (WSUS), and more. For more information, see [Assign devices to servicing channels](/windows/deployment/update/waas-servicing-channels-windows-10-updates). </br></br> Some updates are large, and use bandwidth. Delivery optimization helps reduce bandwidth consumption. It shares the work of downloading the update packages with multiple devices in your deployment. Windows 11 updates are smaller, as they only pull down source files that are different. You can create policies that configure delivery optimization settings. For example, set the maximum upload and download bandwidth, set caching sizes, and more.  </br></br>   For more information, see [Delivery Optimization for Windows updates](/windows/deployment/update/waas-delivery-optimization).  </br></br> For more information on the end-user experience, see:  </br> - [Installation & updates](https://support.microsoft.com/office/installation-updates-2f9c1819-310d-48a7-ac12-25191269903c#PickTab=Windows_11) </br> - [Manage updates in Windows](https://support.microsoft.com/windows/manage-updates-in-windows-643e9ea7-3cf6-7da6-a25c-95d4f7f099fe)

## Related Topics

- [Windows 11 IoT Enterprise - Announcement](https://aka.ms/Win11IoTGABlog)
- [Windows 11 Overview](/windows/whats-new/windows-11)
- [Windows 11 requirements](/windows/whats-new/windows-11-requirements)
- [Plan for Windows 11](/windows/whats-new/windows-11-plan)
- [Prepare for Windows 11](/windows/whats-new/windows-11-prepare)
- [Windows release health](https://aka.ms/windowsreleasehealth)
- [Windows 11 release information](/windows/release-health/windows11-release-information)
- [Deprecated features](/windows/whats-new/deprecated-features)
- [Removed features](/windows/whats-new/removed-features)
- [Windows 11, version 22H2 update history](https://support.microsoft.com/topic/windows-11-version-21h2-update-history-a19cd327-b57f-44b9-84e0-26ced7109ba9)
