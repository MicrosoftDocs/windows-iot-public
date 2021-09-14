---
title: Microsoft Store Access
author: rsameser
ms.author: riameser
ms.date: 3/12/2021
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about the Microsoft Store Access Features of Windows 10 IoT Enterprise.
keywords: Branding, Microsoft Store Access
---

# Microsoft Store Access
You have the option to decide how much access you would like your users to have when it comes to opening the Microsoft Store on Windows 10 IoT Enterprise. Access to the Microsoft store can be blocked or modified achieve a desired customer experience or meet an organization's policy. You can use AppLocker or Group Policy to configure access to Microsoft Store.

> [!NOTE]
>
> The [Long-Term-Servicing Channel (LTSC)](https://docs.microsoft.com/windows/deployment/update/waas-overview#long-term-servicing-channel) has the store service for updating preinstalled apps, but does not include the Store UI for browsing apps. The [Semi-Annual Channel (SAC)](https://docs.microsoft.com/windows/deployment/update/waas-overview#semi-annual-channel) has both the store service and UI.


## Block Microsoft Store using AppLocker
AppLocker provides policy-based access control management for applications. You can block access to Microsoft Store app with [AppLocker](https://docs.microsoft.com/windows/configuration/stop-employees-from-using-microsoft-store#block-microsoft-store-using-applocker) by creating a rule for packaged apps. You'll give the name of the Microsoft Store app as the packaged app that you want to block from client computers.


## Block Microsoft Store using Group Policy
You can also use [Group Policy](https://docs.microsoft.com/windows/configuration/stop-employees-from-using-microsoft-store#block-microsoft-store-using-group-policy) to manage access to Microsoft Store.


## Block Microsoft Store using configuration service provider
If you have Windows 10 devices in your organization that are managed using a mobile device management (MDM) system, such as Microsoft Intune, you can block access to Microsoft Store app using the following [configuration service providers (CSPs)](https://docs.microsoft.com/windows/configuration/stop-employees-from-using-microsoft-store#block-microsoft-store-using-configuration-service-provider):
* [Policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider)
* [AppLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp)

For more information, see [Configure an MDM provider](https://docs.microsoft.com/microsoft-store/configure-mdm-provider-microsoft-store-for-business).


## Show private store only using Group Policy
If you're using [Microsoft Store for Business](https://docs.microsoft.com/microsoft-store/microsoft-store-for-business-overview) and you want employees to only see apps you're managing in your private store, you can use [Group Policy](https://docs.microsoft.com/windows/configuration/stop-employees-from-using-microsoft-store#show-private-store-only-using-group-policy) to show only the private store. Microsoft Store app will still be available, but employees can't view or purchase apps. Employees can view and install apps that the admin has added to your organization's private store.


## Additional Resources
* [Configure access to Microsoft Store](https://docs.microsoft.com/windows/configuration/stop-employees-from-using-microsoft-store#options-to-configure-access-to-microsoft-store)
* [Distribute apps using your private store](https://docs.microsoft.com/microsoft-store/distribute-apps-from-your-private-store)
* [Manage access to private store](https://docs.microsoft.com/microsoft-store/manage-access-to-private-store)
