---
title: Hibernate Once/Resume Many (HORM)
description: Hibernate Once/Resume Many (HORM)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 602B4A95-7C98-41DC-B604-DBA7832A96ED
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 04/12/2018
ms.topic: article


---
# Hibernate Once/Resume Many (HORM)

You can use the Hibernate Once/Resume Many (HORM) feature with Unified Write Filter (UWF) to start your device in a preconfigured state. When HORM is enabled, your system always resumes and restarts from the last saved hibernation file (hiberfil.sys).

A device with HORM enabled can quickly be turned off or shut down, and then restarted into the preconfigured state, even in the event of a sudden power loss.

> [!Note]
> HORM can be used on Unified Extensible Firmware Interface (UEFI) devices running Windows 10, version 1709, or newer versions of Windows, only. In previous Windows versions, the installation procedure for UEFI creates a hidden system partition. Because UWF cannot protect hidden partitions, HORM cannot be used on any devices that contain a hidden partition, including UEFI-capable devices on older versions of Windows.

## Requirements

Windows 10 Enterprise, Windows 10 Education, or Windows IoT Core (IoT Core). Supported on x86-based and x64-based devices.

On Windows 10, version 21H2 or newer versions of Windows, Read-Only Media mode must be implemented to enable HORM.

## UWF configuration

UWF must be enabled before you can enable or disable HORM. UWF must be configured in the following ways to protect the hibernation file from becoming invalid:

* All fixed volumes that are mounted on the system must be protected by UWF.
* Your system must not have any file, folder, or registry exclusions configured for UWF.
* The UWF overlay must be configured to use RAM mode. HORM does not support disk-backed overlays.

UWF does not filter hibernation files from being written to disk. If you want to protect the preconfigured state of your device, lock down any functionality that can modify the hibernation file. For example, disable hibernation, hybrid sleep, and fast startup on your device for standard user accounts so that the saved hibernation file is not overwritten when entering a sleep, hibernate, or shutdown state.

To disable hybrid sleep and fast startup on your device, follow these steps. 

### How to disable hybrid sleep

1. Open the Local Group Policy Editor (gpedit.msc) and navigate to the following path.  
   Computer Configuration\Administrative Templates\System\Power Management\Sleep settings

2. Enable the following two settings under the path:

   Turn off hybrid sleep (plugged in)  
   Turn off hybrid sleep (on battery)
 
### How to disable fast startup

To disable fast startup, set the following registry value:

> [!IMPORTANT]  
> Follow the steps in this section carefully. Serious problems might occur if you modify the registry incorrectly. Before you modify it, [back up the registry for restoration](https://support.microsoft.com/help/322756) in case problems occur.

Key: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Power  
Name : HiberbootEnabled  
Type : DWORD  
Value : 0 (0 = Disabled、1 = Enabled)
 
###  How to prevent Windows from entering hibernation due to the system idle time out or user operations

Configure the following two policies in Local Group Policy Editor (gpedit.msc):

Policy to prevent Windows from entering hibernation by the system idle time:

1. Under the following path:  
   Computer Configuration\Administrative Templates\System\Power Management\Sleep settings

2. Enable these two settings and set the value to 0.

   Specify the system hibernate timeout (plugged in)  
   Specify the system hibernate timeout (on battery)

Disable the policy to show “Hibernation” in the power options menu:  

1. Under the following path:  
   Computer Configuration\Windows Components\File Explorer

2. Disable the following setting:  
   Show hibernate in the power options menu

> [!Note]
> - Don’t disable hibernate (i.e. powercfg /h off) because it will delete the hiberfil.sys which HORM requires.
> - Even after you set all these settings, the timestamp of hiberfil.sys is updated after the system reboot. This is because UWF cannot filter the hiberfil.sys file, and the file needs to be compressed and decompressed during the system reboot. However, this doesn’t change the content of hiberfil.sys so the preconfigured state of the device is protected.

## Configure HORM

1. On the device, open a command prompt as an administrator.
1. To enable hibernation on the device, type the following command:

    `powercfg /h on`

1. To enable UWF on your device, type the following command:

    `uwfmgr.exe filter enable`

1. To protect all volumes on your device, type the following command:

    `uwfmgr.exe volume protect all`

   > [!Note]
   > DVD RW and floppy drives throw an expected error that can be safely ignored.

1. To restart your device to enable UWF, type the following command:

    `uwfmgr.exe filter restart`

1. After the device restarts, to verify the UWF changes that you made on your device, type the following command:

    `uwfmgr.exe get-config`

1. To enable HORM on your device, type the following command:

    `uwfmgr.exe filter enable-horm`

   > [!Note]
   > Remove all file and registry exclusions before you enable HORM.

1. (Optional) In Control Panel, set the Power Option **When I press the power button** to avoid displaying the command prompt when resuming from hibernation, or use a script to close the command prompt on startup.
1. To hibernate the system one time to create an initial hibernation file, at the command prompt, type the following command:

    `shutdown /h`

1. Press the power button to wake the system from hibernation.
1. After the system starts from hibernation to create an initial hibernation file, to shut down and restart the system, type the following command:

    `uwfmgr.exe restart`

1. When HORM is enabled, you cannot change the UWF configuration. To make changes, you must first disable HORM. To disable HORM, type the following command:

    `uwfmgr.exe filter disable-horm`

1. To restart the system to finish disabling HORM, type the following command:

    `uwfmgr.exe restart`

    The system will restart normally with HORM disabled.

> [!Warning]
> Do not uninstall UWF when the filter is enabled or when HORM is enabled, either online or offline by using Windows PE.

## Fix an issue when you cannot disable HORM

In rare circumstances, your device can enter a state where you cannot disable HORM normally.

If you cannot disable HORM on your device, use following procedure to resolve this issue:

1. Start your device in Windows PE.
1. Type the following command:

    `bcdedit.exe /set {bootmgr} custom:26000024 0`

1. Restart the device:

    `shutdown /r/t 0`

1. Disable HORM:

    `uwfmgr.exe filter disable-horm`

1. Enable HORM:

    `uwfmgr.exe filter enable-horm`

1. Hibernate the device:

   `shutdown /h`
