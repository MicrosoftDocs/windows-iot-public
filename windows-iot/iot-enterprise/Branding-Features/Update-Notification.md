---
title: Update Notification
author: rsameser
ms.author: riameser
ms.date: 1/31/2021
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about the Update Notification Feature in Windows 10 IoT Enterprise.
keywords: Branding, Update Notification
---
# Update Notification
In Windows 10 IoT Enterprise, we know that having your device ready for use at all time is very important. We have many features to help you maximize control over your devices' [update notifications](https://docs.microsoft.com/windows/deployment/update/waas-wu-settings#remove-access-to-use-all-windows-update-features) to ensure that you can plan and ahead and control when updates can occur. Below are some common recommended configuration settings. Consider whether each individual configuration setting applies to your device scenario.

## Control UI notifications from the Windows Update client
A device can be configured in a way to hide the UI experience for Windows Update while letting the service itself run in the background and update the system. The Windows Update client still honors the policies set for configuring Automatic Updates, this policy controls the UI portion of that experience.

1. Open the Group Policy Editor (gpedit.msc) and navigate to **Computer Configuration\Administrative Templates\Windows Components\Windows Update\Display options for update notifications**
2. Set the policy to **Enabled**.
3. Specify the update notifications display options to 1 or 2.

> [!TIP]
>
> Set the value to 1 to hide all notifications except restart warnings, or to 2 to hide all notifications, including restart warnings.


## Disable access to the Windows Update user experience
In some scenarios, configuring Automatic Updates isn't enough to preserve a desired device experience. For example, an end-user may still have access to the Windows Update settings, which would allow manual updates via Windows Update. You can configure Group policy to prohibit access to Windows Update through settings.

To prohibit access to Windows update:
1. Open the Group Policy Editor (gpedit.msc) and navigate to **Computer Configuration\Administrative Templates\Windows Components\Windows update\Remove access to use all Windows update features**.
2. Set this policy to **Enabled** to prevent the "Check for updates" option for users. Note: Any background update scans, downloads, and installations will continue to work as configured. This policy simply prevents the user from accessing the manual check through settings. Use the steps in the previous section to also disable scans, downloads, and installations.

> [!IMPORTANT]
>
> Be sure to have a well-designed servicing strategy for your device. Disabling Windows Update capabilities leaves the device in a vulnerable state if your device isn't getting updates in another way.


## Additional Resources
* [Windows Updates in Windows 10 IoT Enterprise](../OS-Features/Updates.md)
* [Manage device restarts after updates](https://docs.microsoft.com/windows/deployment/update/waas-restart)
* [Manage additional Windows Update settings](https://docs.microsoft.com/windows/deployment/update/waas-wu-settings)
* [Deploy feature updates during maintenance windows](https://docs.microsoft.com/windows/deployment/update/feature-update-maintenance-window)
* [Deploy feature updates for user-initiated installations](https://docs.microsoft.com/windows/deployment/update/feature-update-user-install)
