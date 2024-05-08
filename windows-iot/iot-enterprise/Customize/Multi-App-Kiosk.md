---
title: Multi-App Kiosk
author: TerryWarwick
ms.author: twarwick
ms.date: 08/16/2023
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Learn about the Multi-App Kiosk in Windows IoT Enterprise.
keywords: Lockdown, Multi-App, Kiosk
---

# Assigned access multi-app kiosk

An assigned access multi-app kiosk runs one or more apps from the desktop. People using the kiosk see a customized Start that shows only the tiles for the apps that are allowed. With this approach, you can configure a locked-down experience for different account types. A multi-app kiosk is appropriate for devices that are shared by multiple people. Here's a [guide](/windows/configuration/lock-down-windows-10-to-specific-apps) on how to set up a multi-app kiosk.

> [!NOTE]
> Multi-app kiosk mode is not available for Windows 11 IoT Enterprise, version 21H2 or 22H2.  Please refer to [What's new for subsequent releases](../whats-new/Release-History.md#windows-11-iot-enterprise) for information about its return.
>
> **Update** - [Multi-app kiosk mode is now available in Windows 11](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/multi-app-kiosk-mode-now-available-in-windows-11/ba-p/3845558)., version 22H2 as part of the Windows continuous innovation releases.  To learn how you can take advantage of features introduced via Windows continuous innovation, see more about how you can access this feature in Windows 11 IoT Enterprise, version 22H2, see [Delivering continuous innovation in Windows 11](https://support.microsoft.com/windows/delivering-continuous-innovation-in-windows-11-b0aa0a27-ea9a-4365-9224-cb155e517f12).

## Benefits of using a multi-app kiosk

The benefit of a kiosk that runs multiple specified apps is to provide an easy-to-understand experience for individuals by showing them only the things they need to use, and removing the things they don’t need to access.

A multi-app kiosk is appropriate for devices that are shared by multiple people. Each user can authenticate with the device and receive a customized lockdown experience based on the configuration.

## Configuring your multi-app kiosk

* [Configure a kiosk in Microsoft Intune](/windows/configuration/lock-down-windows-10-to-specific-apps#configure-a-kiosk-in-microsoft-intune)
* [Configure a kiosk using a provisioning package](/windows/configuration/lock-down-windows-10-to-specific-apps#configure-a-kiosk-using-a-provisioning-package)

> [!NOTE]
>
> When you configure a multi-app kiosk, [specific policies](/windows/configuration/kiosk-policies) are enforced that will affect all non-administrator users on the device.

## Additional Resources

* [New features and improvements](/windows/configuration/lock-down-windows-10-to-specific-apps)
* [Set up a multi-app kiosk](/windows/configuration/lock-down-windows-10-to-specific-apps)
* [Kiosk apps for assigned access: Best practices](/windows-hardware/drivers/partnerapps/create-a-kiosk-app-for-assigned-access)
* [Guidelines for choosing an app for assigned access](/windows/configuration/guidelines-for-assigned-access-app)
* [Configure kiosks and digital signs](/windows/configuration/kiosk-methods)
* [More kiosk methods and reference information](/windows/configuration/kiosk-additional-reference)
