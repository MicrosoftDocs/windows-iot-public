---
description: Device lockdown features
title: Device lockdown features
ms.date: 12/10/2018
ms.topic: article
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot

---


# Lab 2: Device Lockdown Features

In labs [1a](iot-ent-create-a-basic-image.md) and [1b](iot-ent-customize-the-reference-device-in-audit-mode.md) we installed the OS onto a reference device and made customizations in audit mode. This lab describes several ways lock down your device using device lockdown features that are built in to Windows. The device lockdown features aren't listed in any particular order, and you can enable some, all, or none of the features, depending on the device you're building.

> [!NOTE]
> This lab is optional. You can build an IoT Enterprise device without enabling any of the features described in this lab. If you aren't implementing any of these features, you can continue to [Lab 3](iot-ent-configure-policy-settings.md). 
 
For a fully automated approach to these steps consider using the [Windows 10 IoT Enterprise deployment framework](https://github.com/ms-iot/windows-iotent-deploy).

## Prerequisites 

Complete Lab 1a: Create a basic image. 

## Keyboard filter 

### Keyboard filter overview
 
The [Keyboard Filter](/windows-hardware/customize/enterprise/keyboardfilter) enables controls that you can use to suppress undesirable key presses or key combinations. Normally, a customer can alter the operation of a device by using certain key combinations like Ctrl+Alt+Delete, Ctrl+Shift+Tab, Alt+F4, etc. The Keyboard filter prevents users from using these key combinations, which is helpful if your device is intended for a dedicated purpose.

The Keyboard Filter feature works with physical keyboards, the Windows on-screen keyboard, and the touch keyboard. Keyboard Filter also detects dynamic layout changes, such as switching from one language set to another, and continues to suppress keys correctly, even if the location of suppressed keys has changed on the keyboard layout.  

Keyboard filter keys are stored in the Registry at **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Embedded\KeyboardFilter**.

### Enable the Keyboard filter 

There are several methods to enable the Keyboard Filter, we're providing instructions for one of those methods in this lab.  
 
> [!NOTE]
> See [Keyboard Filter](/windows-hardware/customize/enterprise/keyboardfilter) for more information.
 
 
1. Enable the Keyboard Filter feature by running the following command from an Administrative Command Prompt:

    ```
    DISM /online /enable-feature /featurename:Client-DeviceLockdown /featurename:Client-KeyboardFilter 
    ```

2. You are prompted to restart the reference device, type **Y** to reboot. The device reboots into audit mode.

Once you've enabled the keyboard filter, see [Keyboard filter PowerShell script samples](/windows-hardware/customize/enterprise/keyboardfilter-powershell-script-samples) to learn about blocking key combinations.
 
3. For this lab we're going to provide a demo on blocking the CTRL+ALT+DEL key. In an administrative PowerShell command window, copy and paste the following commands.  
    
    ```PowerShell
    $key = "Ctrl+Alt+Del"
    $setkey = Get-WMIObject -class WEKF_PredefinedKey –computer localhost –namespace  root\standardcimv2\embedded | where {$_.Id -eq "$key"}; 
    $setkey.Id = $key
    $setkey.Enabled = 1;
    $setkey.Put() | Out-Null;
    ```

4. Restart the reference device and then note the CTRL+ALT+DEL key is blocked.


## Unified Write Filter (UWF)
 
### Unified Write Filter overview

[Unified Write Filter (UWF)](/windows-hardware/customize/enterprise/unified-write-filter) is a Windows 10 device lockdown feature that helps to protect your device's configuration by intercepting and redirecting any writes to the drive (app installations, settings changes, saved data) to a virtual overlay.  This overlay can be deleted by rebooting or, in certain configurations, the overlay can be retained until the Unified Write Filter is disabled.

### Enable the UWF
 

1. Enable the Unified Write Filter feature by running the following command from an Administrative Command Prompt:

    ```cmd
    DISM /online /enable-feature /featureName:Client-DeviceLockdown /featureName:Client-UnifiedWriteFilter
    ```

2. Restart the reference device 

3. Configuring and enabling the overlay and protection is best done through scripting but for this lab we'll configure using command line

 For more information about the UWF, including sample scripts, see [Unified write filter](/windows-hardware/customize/enterprise/unified-write-filter).

4. At an Admistrative Command prompt, run the following commands

    ```cmd
    uwfmgr volume protect c:
    uwfmgr filter enable
    ```

5. Restart the reference device

6. Now all writes are redirected to the RAM overlay and won't be retained when the reference device is rebooted.

7. To disable the Unified Write Filter, at an Administrative Command prompt run the following command and then reboot the device.

    ```cmd
    uwfmgr filter disable  
    ```

> [!NOTE]
> When using the Unified Write Filter you must take into consideration the Operating System product activation. Product activation must be done with the Unified Write Filter disabled. Also, when cloning the image to other devices the image needs to be in a Sysprep state and the filter disabled prior to capturing the image.

## Unbranded boot

### Unbranded boot overview

[Unbranded boot](/windows-hardware/customize/enterprise/unbranded-boot) allows you to suppress Windows elements that appear when Windows starts or resumes, and can suppress the crash screen when Windows encounters an error that it can't recover from.

### Enable Unbranded boot

1. Enable the Unbranded boot feature by running the following command in an Administrative Command Prompt:

    ```cmd
    DISM /online /enable-Feature /featureName:Client-DeviceLockdown  
    DISM /online /Enable-Feature /FeatureName:Client-EmbeddedBootExp 
    ```

2. Restart the reference device
 
### Configure Unbranded Boot settings at runtime using BCDEdit

You can customize Unbranded boot from an Administrative Command prompt in the following ways:
 
- Disable the F8 key during startup to prevent access to the Advanced startup options menu:
    
    ```cmd
    bcdedit.exe -set {globalsettings} advancedoptions false 
    ```

- Disable the F10 key during startup to prevent access to the Advanced startup options menu:
    
    ```cmd
    bcdedit.exe -set {globalsettings} optionsedit false 
    ```

- Suppress all Windows UI elements (logo, status indicator, and status message) during startup:
    
    ```cmd
    bcdedit.exe -set {globalsettings} bootuxdisabled on 
    ```

> [!NOTE]
> Anytime you rebuild the BCD information, for example using bcdboot, you'll have to re-run the above commands.

## Custom Logon 
 
You can use the [Custom Logon](/windows-hardware/customize/enterprise/custom-logon) feature to suppress Windows 10 UI elements that relate to the Welcome screen and shutdown screen. For example, you can suppress all elements of the Welcome screen UI and provide a custom logon UI. You can also suppress the Blocked Shutdown Resolver (BSDR) screen and automatically end applications while the OS waits for applications to close before a shutdown.
 
See [Custom logon](/windows-hardware/customize/enterprise/custom-logon) for more information.
 
> [!NOTE]
> Custom Logon feature will not work on images that are using a blank or evaluation product key. You must use a valid Product Key to see the changes made with the below commands.

1. Enable the Custom Logon feature by running the following command at an Administrative Command Prompt:

    ```
    DISM /online /enable-feature /featurename:Client-DeviceLockdown /featurename:Client-EmbeddedLogon 
    ```
2. If prompted to restart, choose No.

3. Next at an Administrative Command prompt modify the following registry entries. If prompted to overwrite, choose Yes.

    ```
    Reg add "HKLM\SOFTWARE\Microsoft\Windows Embedded\EmbeddedLogon" /v  BrandingNeutral  /t REG_DWORD /d 1 
    Reg add "HKLM\SOFTWARE\Microsoft\Windows Embedded\EmbeddedLogon" /v  HideAutoLogonUI  /t REG_DWORD /d 1 
    Reg add "HKLM\SOFTWARE\Microsoft\Windows Embedded\EmbeddedLogon" /v  HideFirstLogonAnimation  /t REG_DWORD /d 1 
    Reg add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Authentication\LogonUI" /v AnimationDisabled /t REG_DWORD /d 1 
    Reg add "HKLM\SOFTWARE\Policies\Microsoft\Windows\Personalization"  /v  NoLockScreen /t REG_DWORD /d 1 
    Reg add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon" /v  UIVerbosityLevel  /t REG_DWORD /d 1
    ```

3.  Restart the reference device. You should no longer see the Windows UI elements that relate to the Welcome screen and shutdown screen.

## Next steps

Your device now has device lockdown features in place. You can use group policies to further customize your device's user experience. Lab 3 covers how to configure policy settings.

>[!div class="nextstepaction"]
>[Go to lab 3](iot-ent-configure-policy-settings.md)
