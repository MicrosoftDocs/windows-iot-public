---
description: Configure Shell launcher or Assigned Access
title: Configure Shell launcher or Assigned Access
ms.date: 12/10/2018
ms.topic: article
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot

---

# Lab 5: Configure Shell Launcher or Assigned Access

Many IoT device scenarios require a custom user experience by either automatically launching an application at Windows startup, or a custom shell experience. Using a custom shell experience enables the OEM to create a controlled user experience where the Windows UI is hidden and the OEM application is the focus.
Windows IoT Enterprise has two custom shell features that enable this custom user experience.

- **Shell Launcher** enables OEMs to set a classic, non-UWP, app as the system shell. The advantage to using Shell Launcher is the ability to provide custom actions based on the exit code of the OEM application. For example if the OEM application exits with a specific exit code, the system can be configured to automatically restart the application, reboot or shutdown the device, etc.

- **Assigned Access** enables OEMs to set a UWP application as the system shell. Similar to Shell Launcher, Assigned Access can automatically restart the application when it's closed, keeping the device in the intended user experience.

For a fully automated approach to enabling these features, consider using the [Windows IoT Enterprise deployment framework](https://github.com/ms-iot/windows-iotent-deploy).

## Prerequisites

Complete [Lab 4](iot-ent-sysprep-capture-deploy.md): You should have a basic image that's been sysprepped and ready to be captured.

## Complete the OOBE process on the IoT device

In lab 4, we used Sysprep to get the system ready for capture and deployment. The following steps assume you're using the image from lab 4. The steps work on system that hasn't been Sysprepped, but the OOBE experience is completed.

### Complete the OOBE process on the reference system

1. Turn on the reference IoT device and boot to the OS partition. The OS was in a Sysprep state and OOBE should begin.

1. Complete the OOBE experience. Choose the settings that match your device requirements.  

> [!NOTE]
> The OOBE experience can be fully automated using an Answer File along with Sysprep to answer the OOBE questions in advance. For more information, see the example Answer Files in the [Windows IoT Enterprise deployment framework](https://github.com/ms-iot/windows-iotent-deploy).

## Enable and configure Shell Launcher

### Enable Shell Launcher

Once the device is booted to the desktop, enable the Shell Launcher. From an Administrative Command Prompt:

```cmd
Dism /online /Enable-Feature /FeatureName:Client-EmbeddedShellLauncher 
```

### Configure Shell Launcher to run an OEM application

With Shell Launcher enabled, you can set an application as the Windows Shell. In the following steps, we show you how to use notepad.exe as the shell for the current user. In your device, you use a different application in place of Notepad.exe to configure the system to use the OEM application as the shell, but the steps are the same. See [Shell launcher](/windows-hardware/customize/enterprise/shell-launcher) to learn more.

To set Notepad.exe as your custom shell:

1. From PowerShell run:

    ```PowerShell
    $ShellLauncherClass = [wmiclass]"\\localhost\root\standardcimv2\embedded:WESL_UserSetting"

    $ShellLauncherClass.SetDefaultShell("notepad.exe",1)

    $ShellLauncherClass.SetEnabled($TRUE)
    ```

1. Reboot the reference IoT device.
1. The system reboots and Notepad starts as the default system shell.

## Enable and configure Assigned Access

The following lab steps provide links on how to install a UWP application suitable for Assigned Access and to configure the system to launch the application automatically at startup. The UWP application must be able to run above the lock screen in order to work correctly with assigned access.

> [!NOTE]
> See details on the UWP application requirements for Assigned Access at [Create a kiosk app for Assigned Access](/windows-hardware/drivers/partnerapps/create-a-kiosk-app-for-assigned-access).

### Sideload a UWP application and configure Assigned Access to run it

In this lab, you add a UWP app to your image by sideloading it onto the system. For production scenarios, follow the guidance on deploying signed UWP applications.

1. Compile the UWP application and build the APPX package following the steps at [Packaging UWP apps](/windows/uwp/packaging/packaging-uwp-apps).

1. Sideload the UWP application following the steps at [Sideload your app package](/windows/uwp/packaging/packaging-uwp-apps#sideload-your-app-package)

1. Follow the steps at [Set up a kiosk using Windows PowerShell](/windows/configuration/kiosk-single-app#set-up-a-kiosk-using-windows-powershell) to complete the process.

> [!NOTE]
>For scenarios where multiple apps are needed, follow the steps at [Set up a multi-app kiosk](/windows/configuration/lock-down-windows-10-to-specific-apps)
