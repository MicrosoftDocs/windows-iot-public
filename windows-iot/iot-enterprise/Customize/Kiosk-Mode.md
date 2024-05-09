---
title: Kiosk Mode
author: TerryWarwick
ms.author: twarwick
ms.date: 01/18/2024
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Learn about Kiosk Mode in Windows IoT Enterprise.
keywords: Lockdown, Kiosks, Kiosk Mode
---

# Kiosk mode

Windows IoT Enterprise allows you to build fixed purpose devices such as ATM machines, point-of-sale terminals, medical devices, digital signs, or kiosks. Kiosk mode helps you create a dedicated and locked down user experience on these fixed purpose devices. Windows IoT Enterprise offers a set of different locked-down experiences for public or specialized use: [assigned access single-app kiosks](./Single-App-Kiosk.md), [assigned access multi-app kiosks](./Multi-App-Kiosk.md), or [shell launcher](./Shell-Launcher.md).

Kiosk configurations are based upon either [assigned access](/windows/configuration/guidelines-for-assigned-access-app) or [shell launcher](./Shell-Launcher.md). There are several kiosk configuration methods that you can choose from, depending on your answers to the following questions.

> [!NOTE]
>
> A benefit of using an assigned access kiosk mode is [these policies](/windows/configuration/kiosk-policies) are automatically applied to the device to optimize the lock-down experience.

## Which type of app will your kiosk run?

Your kiosk can run a Universal Windows Platform (UWP) app or a Windows desktop application. For [digital signage](/windows/configuration/setup-digital-signage), select a digital sign player as your kiosk app. Check out the [Guidelines for Kiosk Apps](/windows/configuration/guidelines-for-assigned-access-app).

## Which type of kiosk do you need?

If you want your kiosk to run a single app for anyone to see or use, consider an [assigned-access single-app kiosk](./Single-App-Kiosk.md) that runs either a [Universal Windows Platform (UWP) app](/windows/configuration/kiosk-methods#uwp) or a [Windows desktop application](/windows/configuration/kiosk-methods#classic).

For a kiosk that people can sign in to with their accounts or that runs more than one app, consider an [assigned access multi-app kiosk](/windows/configuration/kiosk-methods#desktop).

## Which type of user account will be the kiosk account?

The kiosk account can be a local standard user account, a domain account, or an Azure Active Directory (Azure AD) account, depending on the method that you use to configure the kiosk. If you want people to sign in and authenticate on the device, you should use an assigned access multi-app kiosk configuration. The assigned access single-app kiosk configuration doesn't require people to sign in to the device, although they can sign in to the kiosk app if you select an app that has a sign-in method.

## Kiosk capabilities for Windows 10 IoT Enterprise

| Mode | Features | Description | Customer Usage  |
|------|----------|------------ |-----------------|
| Assigned access | Single-app kiosk (UWP)  | Auto launches a UWP app in full screen and prevents access to other system functions, while monitoring the lifecycle of the kiosk app. Only supports one single-app kiosk profile under one account per device. | Digital signs & single function devices
| Assigned access | Single-app kiosk (Microsoft Edge) | Auto launches Microsoft Edge and prevents access to other system functions, while monitoring the lifecycle of browser. Only supports one single-app kiosk profile under one account per device. | Public browsing kiosks & digital signs |
| Assigned access | Multi-app kiosk (Restricted User Experience) | Windows 10: Always auto launches a restricted Start menu in full screen with the list of allowed app tiles. <br/> Windows 11: Presents the familiar Windows desktop experience with a restricted set of apps. | Frontline Worker shared devices |
| Shell launcher | Shell launcher | Auto launches an app that the customer specifies and monitors the lifecycle of this app. App can be used as a "shell" if desired. No default lockdown policies like hotkey blocking are enforced in Shell Launcher. | Fixed purpose devices with a custom shell experience |

## How to configure your device for kiosk mode?

Visit the following documentation to set up a kiosk according to your scenario:

* [Configure kiosks and digital signs](/windows/configuration/kiosk-methods)
* [Set up a single-app kiosk](/windows/configuration/kiosk-single-app)
* [Set up a multi-app kiosk](/windows/configuration/lock-down-windows-10-to-specific-apps)
* [Configure Microsoft Edge kiosk mode](/deployedge/microsoft-edge-configure-kiosk-mode)

## Additional Resources

* [Find the Application User Model ID of an installed app](/windows/configuration/find-the-application-user-model-id-of-an-installed-app)
* [Validate your kiosk configuration](/windows/configuration/kiosk-validate)
* [Guidelines for choosing an app for assigned access (kiosk mode)](/windows/configuration/guidelines-for-assigned-access-app)
* [Policies enforced on kiosk devices](/windows/configuration/kiosk-policies)
* [Assigned access XML reference](/windows/configuration/kiosk-xml)
* [Use AppLocker to create a Windows 10 kiosk](/windows/configuration/lock-down-windows-10-applocker)
* [Use Shell Launcher to create a Windows 10 kiosk](/windows/configuration/kiosk-shelllauncher)
* [Use MDM Bridge WMI Provider to create a Windows 10 kiosk](/windows/configuration/kiosk-mdm-bridge)
* [Troubleshoot kiosk mode issues](/windows/configuration/kiosk-troubleshoot)
* [Plan your kiosk mode transition to Microsoft Edge](/deployedge/microsoft-edge-kiosk-mode-transition-plan)
