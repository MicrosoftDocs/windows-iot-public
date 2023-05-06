---
title: Device Management Overview
author: TerryWarwick
ms.author: twarwick
ms.date: 04/04/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about the Device Management feature of Windows 10 IoT Enterprise.
keywords: IoT Enterprise, Device Management, MDM, Intune, SCCM, Azure Device Twin, Endpoint Manager, Device Health
---
# Device Management Overview

Managing a device is now easier than ever on Windows IoT Enterprise. There are multiple options that your organization can choose from in order to best manage your devices, such as Azure Arc, Microsoft Intune, Endpoint Manager, and third-party OMA-DM based management tools.

## Azure Arc for Server on Windows IoT Enterprise

Azure Arc unlocks new hybrid scenarios by enabling new Azure services and management features on any infrastructure. Azure Arc-enabled servers is now supported on [Windows IoT Enterprise](/azure/azure-arc/servers/prerequisites#supported-environments). With Azure Arc, you can extend Azure Resource Manager capabilities to your Windows IoT Enterprise devices and manage them on Azure. Connect your Windows IoT Enterprise machines to Azure Arc as described [here.](/azure/azure-arc/servers/learn/quick-enable-hybrid-vm)

When you connect your machine as an Azure Arc-enabled server, you can perform the following actions:

* Monitor operating system performance and discover application components to monitor processes and dependencies with other resources using [VM insights](/azure/azure-monitor/vm/vminsights-overview). Collect other log data, such as performance data and events, from the operating system or workloads running on the machine and this data is stored in a [Log Analytics workspace](/azure/azure-monitor/logs/log-analytics-workspace-overview).
* Assign [Azure Policy guest configurations](/azure/governance/machine-configuration/overview) to audit settings on the machine.

We are actively working on expanding this list of supported actions.

## Mobile Device Management

Windows 10 provides an enterprise management solution to help IT pros manage company security policies and business applications, while avoiding compromise of the users’ privacy on their personal devices. A built-in management component can communicate with the management server. Learn [What's new in mobile device enrollment and management](/windows/client-management/mdm/new-in-windows-mdm-enrollment-management#whatsnew10) to further understand the capabilities that are being offered.

### Microsoft Intune

[Microsoft Intune](/mem/intune/fundamentals/what-is-intune) is a cloud-based service that focuses on mobile device management (MDM) and mobile application management (MAM). You control how your organization’s devices are used and can configure specific policies to control applications. Intune is part of [Microsoft's Enterprise Mobility + Security (EMS) suite](https://www.microsoft.com/microsoft-365/enterprise-mobility-security?rtc=1). Intune integrates with Azure Active Directory (Azure AD) to control who has access, and what they can access. It also integrates with Azure Information Protection for data protection. Here's a [guide](/mem/intune/enrollment/windows-bulk-enroll) on how to enroll your devices in Microsoft Intune.

## Microsoft Endpoint Manager (Formerly SCCM)

[Microsoft Endpoint Manager](/mem/configmgr/core/understand/introduction) is an integrated solution for managing all of your devices. Microsoft brings together Configuration Manager and Intune, without a complex migration, and with simplified licensing. Continue to leverage your existing Configuration Manager investments, while taking advantage of the power of the Microsoft cloud at your own pace.

> [!NOTE]
> Starting in version 1910, [Configuration Manager](/mem/configmgr/core/understand/what-happened-to-sccm) current branch is now part of Microsoft Endpoint Manager. Version 1906 and earlier are still branded System Center Configuration Manager (SCCM). The Microsoft Endpoint Manager brand will appear in the product and documentation over the coming months.

## Update Management

Windows Server Update Services are update controls and mechanisms that are not full device management solutions, but are included in the list for completeness.

### Windows Server Update Services (WSUS)

[Windows Server Update Services (WSUS)](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) enables organizations to deploy the latest Microsoft product updates to their Windows IoT devices. You can use WSUS to fully manage the distribution of updates that are released through Microsoft Update to devices on your network.

A WSUS server provides features that you can use to manage and distribute updates through a management console. A WSUS server can also be the update source for other WSUS servers within the organization. The WSUS server that acts as an update source is called an upstream server. In a WSUS implementation, at least one WSUS server on your network must be able to connect to Microsoft Update to get available update information.

* [Deploy WSUS](/windows-server/administration/windows-server-update-services/deploy/deploy-windows-server-update-services)
* [Update Management with WSUS](/windows-server/administration/windows-server-update-services/manage/update-management-with-windows-server-update-services)
