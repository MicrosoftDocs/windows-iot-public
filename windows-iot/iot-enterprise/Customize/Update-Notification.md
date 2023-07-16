---
title: Manage Update Experience
author: TerryWarwick
ms.author: twarwick
ms.date: 03/30/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about the Update Notification Feature in Windows IoT Enterprise.
keywords: Branding, Update Notification
---
# Manage Update Experience

In Windows IoT Enterprise, we know that having your device ready for use at all time is very important. We have many features to help you maximize control and customization over your devices' update screen UI and [notifications](/windows/deployment/update/waas-wu-settings#remove-access-to-use-all-windows-update-features) to ensure that you can plan and ahead and control when updates can occur. Below are some common recommended configuration settings. Consider whether each individual configuration setting applies to your device scenario.

## Unbranded Update Message Strings

Starting in Windows fall 2021 releases, update message strings have been rewritten to remove references to terms such as ‘Windows’, ‘computer’, and ‘PC’, to keep the experienced focused on your fixed-purpose device. See table below for examples.

| Original String | New String |
|-----------------|------------|
| Don't turn off your computer | Please keep your device on |
| Getting Windows ready | Getting things ready |
| Setting up Windows | Updates are underway |
| Getting ready to retry | Retrying a few things |
| We couldn't complete the updates | Something didn't go as planned |

## Update Screen Accent Color

You can additionally customize the update experience on your devices by changing the background color of the update screen from the traditional blue to whichever color best matches your branding of your organization.  

To update the accent color:

1. Open the Settings app and navigate to Personalization.
2. In the menu on the left side, navigate to Colors.
3. Scroll to the bottom of the page and select a color from the list or use the custom color picker.

> [!NOTE]
>
> This setting also affects the color of accents within the UI of the OS.

## Control UI notifications from the Windows Update client

A device can be configured in a way to hide the UI experience for Windows Update while letting the service itself run in the background and update the system. The Windows Update client still honors the policies set for configuring Automatic Updates, this policy controls the UI portion of that experience.

1. Open the Group Policy Editor (gpedit.msc) and navigate to **Computer Configuration\Administrative Templates\Windows Components\Windows Update\Display options for update notifications**
2. Set the policy to **Enabled**.
3. Specify the update notifications display options to 1 or 2.

> [!TIP]
>
> Set the value to 1 to hide all notifications except restart warnings, or to 2 to hide all notifications, including restart warnings.

## Additional Resources

* [Windows Updates in Windows IoT Enterprise](../OS-Features/Updates.md)
* [Manage device restarts after updates](/windows/deployment/update/waas-restart)
* [Manage additional Windows Update settings](/windows/deployment/update/waas-wu-settings)
* [Deploy feature updates during maintenance windows](/windows/deployment/update/feature-update-maintenance-window)
* [Deploy feature updates for user-initiated installations](/windows/deployment/update/feature-update-user-install)
