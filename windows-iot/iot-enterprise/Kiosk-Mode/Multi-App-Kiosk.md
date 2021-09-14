---
title: Multi-App Kiosk
author: rsameser
ms.author: riameser
ms.date: 3/30/2021
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about the Multi-App Kiosk in Windows 10 IoT Enterprise.
keywords: Lockdown, Multi-App, Kiosk
---

# Assigned access multi-app kiosk
An assigned access multi-app kiosk runs one or more apps from the desktop. People using the kiosk see a customized Start that shows only the tiles for the apps that are allowed. With this approach, you can configure a locked-down experience for different account types. A multi-app kiosk is appropriate for devices that are shared by multiple people. Here's a [guide](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps) on how to set up a multi-app kiosk.

## Benefits of using a multi-app kiosk
The benefit of a kiosk that runs only one or more specified apps is to provide an easy-to-understand experience for individuals by putting in front of them only the things they need to use, and removing from their view the things they don’t need to access.

A multi-app kiosk is appropriate for devices that are shared by multiple people. Each user can authenticate with the device and receive a customized lockdown experience based on the configuration.

## Configuring your multi-app kiosk
* [Configure a kiosk in Microsoft Intune](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#configure-a-kiosk-in-microsoft-intune)
* [Configure a kiosk using a provisioning package](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#configure-a-kiosk-using-a-provisioning-package)

> [!NOTE]
>
> When you configure a multi-app kiosk, [specific policies](https://docs.microsoft.com/windows/configuration/kiosk-policies) are enforced that will affect all non-administrator users on the device.

## Additional Resources
* [New features and improvements](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps)
* [Set up a multi-app kiosk](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps)
* [Kiosk apps for assigned access: Best practices](https://docs.microsoft.com/windows-hardware/drivers/partnerapps/create-a-kiosk-app-for-assigned-access)
* [Guidelines for choosing an app for assigned access](https://docs.microsoft.com/windows/configuration/guidelines-for-assigned-access-app)
* [Configure kiosks and digital signs](https://docs.microsoft.com/windows/configuration/kiosk-methods)
* [Prepare a device for kiosk configuration](https://docs.microsoft.com/windows/configuration/kiosk-prepare)
* [More kiosk methods and reference information](https://docs.microsoft.com/windows/configuration/kiosk-additional-reference)
