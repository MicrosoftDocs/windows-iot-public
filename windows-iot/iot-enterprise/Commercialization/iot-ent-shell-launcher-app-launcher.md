---
description: Configure Shell launcher or Assigned Access
title: Configure Shell launcher or Assigned Access
ms.date: 09/27/2024
ms.topic: article
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot

---

# Lab 5: Configure Shell Launcher or Assigned Access

Windows IoT Enterprise allows you to build fixed purpose devices such as ATM machines, point-of-sale terminals, medical devices, digital signs, or kiosks. Kiosk mode helps you create a dedicated and locked down user experience on these fixed purpose devices. Windows IoT Enterprise offers a set of different locked-down experiences for public or specialized use: [assigned access single-app kiosks](/windows/configuration/shell-launcher/single-app-kiosk), [assigned access multi-app kiosks](/windows/configuration/shell-launcher/multi-app-kiosk), or [shell launcher](/windows/configuration/shell-launcher).

Kiosk configurations are based upon either [assigned access](/windows/configuration/guidelines-for-assigned-access-app) or [shell launcher](/windows/configuration/shell-launcher).

## Prerequisites

Complete [Lab 4](iot-ent-sysprep-capture-deploy.md): You should have a basic image that's been sysprepped and ready to be captured.

## Complete the OOBE process on the IoT device

In lab 4, we used Sysprep to get the system ready for capture and deployment. The following steps assume you're using the image from lab 4. The steps work on system that hasn't been Sysprepped, but the OOBE experience is completed.

### Complete the OOBE process on the reference system

1. Turn on the reference IoT device and boot to the OS partition. The OS was in a Sysprep state and OOBE should begin.

1. Complete the OOBE experience. Choose the settings that match your device requirements.

## Enable and configure Shell Launcher

### Enable Shell Launcher

Once the device is booted to the desktop, enable the Shell Launcher. From an Administrative Command Prompt:

```cmd
Dism /online /Enable-Feature /all /FeatureName:Client-EmbeddedShellLauncher
```

### Configure Shell Launcher to run an OEM application

With Shell Launcher enabled, you can set an application as the Windows Shell. In the following steps, we show you how to use *powershell.exe* as the shell for the current user. In your device, you use a different application in place of *PowerShell* to configure the system to use the OEM application as the shell, but the steps are the same. See [Shell launcher](/windows/configuration/shell-launcher) to learn more.

To set *powershell.exe* as your custom shell:

1. From an Administrative Windows PowerShell Prompt run:

    ```PowerShell
    $ShellLauncherClass = [wmiclass]"\\localhost\root\standardcimv2\embedded:WESL_UserSetting"

    $ShellLauncherClass.SetDefaultShell("powershell.exe",1)

    $ShellLauncherClass.SetEnabled($TRUE)
    ```

1. Reboot the reference IoT device.
1. The system reboots and *PowerShell* starts as the default system shell.

To revert the system back to the *explorer.exe* shell, run the following commands:

1. From the current shell, open an Administrative Windows PowerShell Prompt:

    ```powershell
    Start-Process powershell -Verb RunAs
    ```

1. Then run the following commands:

    ```PowerShell
    $ShellLauncherClass = [wmiclass]"\\localhost\root\standardcimv2\embedded:WESL_UserSetting"

    $ShellLauncherClass.SetDefaultShell("explorer.exe",1)
    ```

1. Reboot the reference IoT device.
1. The system reboots and *Explorer* starts as the default system shell.

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
>For scenarios where multiple apps are needed, follow the steps at [Set up a multi-app kiosk](/windows/configuration/assigned-access/configuration-file)
