---
title: Application Updates
author: rsameser
ms.author: riameser
ms.date: 3/12/2021
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about how apps can be updated in Windows 10 IoT Enterprise.
keywords: Branding, Microsoft Store Access
---

# Application Updates
OEMs and enterprise customers can deliver app updates to Windows 10 IoT Enterprise devices in the following ways:
* **Using Microsoft Store**: The app is published and updated from the Microsoft Store
* **Using Azure IoT Device Management**: The app is published to Azure Storage and updated through the Azure DM channel New for Windows 10, version 1709
* **Using OMA-DM**: The app is updated using an OMA-DM compliant device management channel such as Intune.
* **Using Device Update Center**: The app is published to Windows Update and updated like any other OEM package (driver package).  *This feature is coming soon for Windows 10 IoT Enterprise, it is currently in private preview, please see [Device Management](./Device-Management-Overview.md#device-update-center) for more information*

> [!NOTE]
>
> The first version of the app is always pre-packaged in the device during image time. The [ApplicationManagement/AllowAllTrustedApps](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#applicationmanagement-allowalltrustedapps) setting should be set for enabling installation of trusted apps.

## Using the Microsoft Store
The Microsoft Store provides unique and secure means to update the IoT Enterprise apps, independent of the OS/OEM Component updates.

This option is interesting for OEMs who have:
* **High update frequency**: App update frequency higher than the driver updates and App updates are independent of drivers.
* **Third-party ISV developers**: Third-party ISV developed app, managed with a different release schedule.

In this option, the apps that are pre-packaged need to be Microsoft Store compliant apps (store signed).

### Managing Store app updates
The following settings on the device side control the updates from Windows Store.

* [ApplicationManagement/AllowStore](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#applicationmanagement-allowstore): Enable/disable store.
* [ApplicationManagement/AllowAppStoreAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#applicationmanagement-allowappstoreautoupdate): Enable auto update of all store apps.

#### Self-updates
The Apps can be designed to control the updates by itself (either automatically or with user interaction with the appx). Windows makes available APIs that give a developer the ability to query available updates, download available updates, and install available updates.

See [Download and install package updates for your app](https://docs.microsoft.com/windows/uwp/packaging/self-install-package-updates) for more information on building this capability. In this case, the AllowAppStoreAutoUpdate should be disabled.

## Using Azure IoT Device Management
[Azure IoT Device Management (AzureDM)](https://docs.microsoft.com/windows/iot-core/manage-your-device/azureiotdm) is a highly scalable management solution available on Windows 10 IoT Enterprise. See [Application Management](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/application-management.md) for the details of installing and updating applications via AzureDM.

## Using OMA-DM
The OMA-DM interface is supported in Windows 10 IoT Enterprise and any OMA-DM compliant management solution can be used to install and update applications. Read the documentation for [EnterpriseModernAppManagement CSP](https://docs.microsoft.com/windows/client-management/mdm/enterprisemodernappmanagement-csp) for usage instructions.

## Comparisons of various options
| Item | Using Microsoft Store | Using AzureDM | Using OMA-DM |
|------|-----------------------|---------------|--------------|
| Appx Signing | Store Signed | Store signed or OEM Signed | Store signed or OEM Signed |
| Distribution/Visibility | Store private (not available in store catalog) | Private | Private |
| Infrastructure | Microsoft Store | Azure IoT / Storage | OEM Infrastructure
