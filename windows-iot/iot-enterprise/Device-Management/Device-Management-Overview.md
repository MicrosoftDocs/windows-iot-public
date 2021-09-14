---
title: Device Management Overview
author: rsameser
ms.author: riameser
ms.date: 3/12/2021
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about the Device Management feature of Windows 10 IoT Enterprise.
keywords: IoT Enterprise, Device Management, MDM, Intune, SCCM, Azure Device Twin, Endpoint Manager, Device Health
---
# Device Management Overview
Managing a device is now easier than ever on Windows 10 IoT Enterprise. There are multiple options that your organization can choose from in order to best manage your devices, such as Microsoft Intune, Endpoint Manager, and third-party OMA-DM based management tools. OEMs can also select Azure Device Agent, which leaves it up to their customers to select the device management solution that fits them best.  

## Mobile Device Management
Windows 10 provides an enterprise management solution to help IT pros manage company security policies and business applications, while avoiding compromise of the users’ privacy on their personal devices. A built-in management component can communicate with the management server. Learn [What's new in mobile device enrollment and management](https://docs.microsoft.com/windows/client-management/mdm/new-in-windows-mdm-enrollment-management#whatsnew10) to further understand the capabilities that are being offered.


### Microsoft Intune
[Microsoft Intune](https://docs.microsoft.com/mem/intune/fundamentals/what-is-intune) is a cloud-based service that focuses on mobile device management (MDM) and mobile application management (MAM). You control how your organization’s devices are used and can configure specific policies to control applications. Intune is part of [Microsoft's Enterprise Mobility + Security (EMS) suite](https://www.microsoft.com/microsoft-365/enterprise-mobility-security?rtc=1). Intune integrates with Azure Active Directory (Azure AD) to control who has access, and what they can access. It also integrates with Azure Information Protection for data protection. Here's a [guide](https://docs.microsoft.com/mem/intune/enrollment/windows-bulk-enroll) on how to enroll your devices in Microsoft Intune.


## Microsoft Endpoint Manager (Formerly SCCM)
[Microsoft Endpoint Manager](https://docs.microsoft.com/mem/configmgr/core/understand/introduction) is an integrated solution for managing all of your devices. Microsoft brings together Configuration Manager and Intune, without a complex migration, and with simplified licensing. Continue to leverage your existing Configuration Manager investments, while taking advantage of the power of the Microsoft cloud at your own pace.

> [!NOTE]
> Starting in version 1910, [Configuration Manager](https://docs.microsoft.com/mem/configmgr/core/understand/what-happened-to-sccm) current branch is now part of Microsoft Endpoint Manager. Version 1906 and earlier are still branded System Center Configuration Manager (SCCM). The Microsoft Endpoint Manager brand will appear in the product and documentation over the coming months.


## Azure IoT Device Agent
The [Azure IoT Device Agent](https://docs.microsoft.com/windows/iot-core/manage-your-device/azureiotda) is supported on Windows 10 IoT Enterprise and enables remote device management capabilities.

Azure IoT Device Agent provides a ready-to-build [open source solution](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/device-agent.md) that:
* Manages the device identity provisioning with IoT Hub.
* Manages the cloud connection and its renewal.
* Provides a plug-in model for platform components, which allows easy onboarding to various Azure services. (This model includes discovery, initialization, error reporting, and state aggregation.)
* Comes with a set of ready-to-ship plug-ins for very commonly used platform components.


## Device Update Center
[Device Update Center (DUC)](https://docs.microsoft.com/windows-hardware/service/iot/using-device-update-center) is available for IoT Core today. DUC is not really device management, but it is included in this list for completeness. DUC is update control that is staged before device management in the control chain. DUC is a great solution if you are looking to push app updates or control OS updates for a SKU of devices collectively (vs. individual devices as addressed above by Device Management). This means that you can still use device management if you choose DUC for upstream control. This service is often used with [Azure Device Agent](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/device-agent.md) by appliance device builders.

We are working on bringing Device Update Center to Windows IoT Enterprise in the coming months, it is currently in Private Preview.

To learn more about DUC, please review this animated YouTube video on [Microsoft Device Update Center Primer](https://www.youtube.com/watch?v=mbclu-nWKbU).
