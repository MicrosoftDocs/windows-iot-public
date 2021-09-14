---
title: Shell Launcher
author: rsameser
ms.author: riameser
ms.date: 1/31/2021
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about the Shell Launcher Feature in Windows 10 IoT Enterprise.
keywords: Lockdown, Shell Launcher
---
# Shell Launcher
Using [Shell Launcher](https://docs.microsoft.com/windows/configuration/kiosk-shelllauncher), you can configure a kiosk device to run a Windows Desktop or Universal Windows Application as the user interface. The application that you specify replaces the default shell (explorer.exe) that usually runs when a user logs on. *This type of single-app kiosk does not run above the lock screen.*

Methods of controlling access to other desktop applications and system components can be used in addition to using the Shell Launcher such as, [Group Policy](https://www.microsoft.com/download/details.aspx?id=25250), [AppLocker](https://docs.microsoft.com/windows/iot-enterprise/advanced_lockdown_features#applocker), and [Mobile Device Management](https://docs.microsoft.com/windows/client-management/mdm/)

>[!NOTE]
>
> In Shell Launcher v1, available in Windows 10, you can only specify a Windows desktop application as the replacement shell. In Shell Launcher v2, available in Windows 10, version 1809 and above, you can also specify a UWP app as the replacement shell.
>
> To use Shell Launcher v2 in version 1809, you need to install the [KB4551853 update](https://support.microsoft.com/topic/may-12-2020-kb4551853-os-build-17763-1217-c2ea33f7-4506-dd13-2739-d9c7bb80b26d).

## Differences between Shell Launcher v1 and Shell Launcher v2
Shell Launcher v1 replaces ```explorer.exe```, the default shell, with ```eshell.exe```, which can launch a Windows desktop application.

Shell Launcher v2 replaces ```explorer.exe``` with ```customshellhost.exe```. This new executable file can launch a Windows desktop application or a UWP app.

In addition to allowing you to use a UWP app for your replacement shell, Shell Launcher v2 offers additional enhancements:

* You can use a custom Windows desktop application that can then launch UWP apps, such as Settings and Touch Keyboard.
* From a custom UWP shell, you can launch secondary views and run on multiple monitors.
* The custom shell app runs in full screen, and can run other apps in full screen on user’s demand.
For sample XML configurations for the different app combinations, see [Samples for Shell Launcher v2](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/ShellLauncherV2).

## Turn on Shell Launcher
Shell Launcher is an optional component and is not turned on by default in Windows 10. It must be turned on prior to configuring. You can turn on and configure Shell Launcher in a customized Windows 10 image (.wim) if Microsoft Windows has not been installed. If Windows has already been installed and you are applying a provisioning package to configure Shell Launcher, you must first turn on Shell Launcher in order for a provisioning package to successfully apply.

There are multiple ways to *enable* Shell Launcher:
* [Control Panel](https://docs.microsoft.com/windows-hardware/customize/enterprise/shell-launcher#enable-shell-launcher-using-control-panel)
* [WESL_UserSetting](https://docs.microsoft.com/windows-hardware/customize/enterprise/shell-launcher#enable-shell-launcher-by-calling-wesl_usersetting)
* [DISM](https://docs.microsoft.com/windows-hardware/customize/enterprise/shell-launcher#enable-shell-launcher-using-dism)
* [Windows Configuration Designer](https://docs.microsoft.com/windows-hardware/customize/enterprise/shell-launcher#enable-shell-launcher-using-windows-configuration-designer)

Learn the methods to [configure](https://docs.microsoft.com/windows-hardware/customize/enterprise/shell-launcher#configure-shell-launcher) Shell Launcher.

## Shell Launcher Capabilities
Explore the various capabilities of Shell Launcher:
* [Launch different shells for different user accounts](https://docs.microsoft.com/windows-hardware/customize/enterprise/shell-launcher#launch-different-shells-for-different-user-accounts)
* [Perform an action when the shell exits](https://docs.microsoft.com/windows-hardware/customize/enterprise/shell-launcher#perform-an-action-when-the-shell-exits)
* [Set your custom shell](https://docs.microsoft.com/windows-hardware/customize/enterprise/shell-launcher#set-your-custom-shell)
* [Understand Shell Launcher user rights](https://docs.microsoft.com/windows-hardware/customize/enterprise/shell-launcher#shell-launcher-user-rights)

## Additional Resources
* [Use Shell Launcher to create a Windows 10 Kiosk](https://docs.microsoft.com/windows/configuration/kiosk-shelllauncher)
* [Launch different shells for different user accounts](https://docs.microsoft.com/windows-hardware/customize/enterprise/shell-launcher#launch-different-shells-for-different-user-accounts)
* [Perform an action when the shell exits](https://docs.microsoft.com/windows-hardware/customize/enterprise/shell-launcher#perform-an-action-when-the-shell-exits)
* [Shell Launcher user rights](https://docs.microsoft.com/windows-hardware/customize/enterprise/shell-launcher#shell-launcher-user-rights)
