---
description: Device lockdown features
title: Device lockdown features
ms.date: 12/10/2018
ms.topic: article
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot

---
<!-- TODO: For streamline, focus on Unbranded Boot, Custom Logon, and Shell Launcher -->
# Lab 2: Device Lockdown Features

In labs [1a](iot-ent-create-a-basic-image.md) and [1b](iot-ent-customize-the-reference-device-in-audit-mode.md), we installed the OS onto a reference device and made customizations in audit mode. This lab describes several ways to lock down your device using device lockdown features that are built in to Windows. The device lockdown features aren't listed in any particular order. You can enable all of the features, some or none of the features, depending on the device you're building.

> [!NOTE]
> This lab is optional. You can build an IoT Enterprise device without enabling any of the features described in this lab. If you aren't implementing any of these features, you can continue to [Lab 3](iot-ent-configure-policy-settings.md).

For a fully automated approach to these steps, consider using the [Windows IoT Enterprise deployment framework](https://github.com/ms-iot/windows-iotent-deploy).

## Prerequisites

Complete Lab 1a: Create a basic image.

<!-- TODO: Evaluate if we want to show Keyboard filter in a VM? In Hyper-V we can simulate that by using Action->Ctrl+Alt+Del. It can be done in VMWare, VirtualBox and others as well -->
## Keyboard filter

The [Keyboard Filter](../Customize/keyboardfilter.md) enables controls that you can use to suppress undesirable key presses or key combinations. Normally, a customer can alter the operation of a device by using certain key combinations like Ctrl+Alt+Delete, Ctrl+Shift+Tab, Alt+F4, etc. The Keyboard filter prevents users from using these key combinations, which is helpful if your device is intended for a dedicated purpose.

The Keyboard Filter feature works with physical keyboards, the Windows on-screen keyboard, and the touch keyboard. Keyboard Filter also detects dynamic layout changes and continues to suppress keys correctly even if the location of the suppressed keys changes on the keyboard. An example of this scenario is switching from one language set to another.

Keyboard filter keys are stored in the Registry at *HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Embedded\KeyboardFilter*.

### Enable the Keyboard filter

There are several methods to enable the Keyboard Filter, we're providing instructions for one of those methods. For more information, see [Keyboard Filter](../Customize/keyboardfilter.md).

1. Enable the Keyboard Filter feature by running the following command from an Administrative Command Prompt:

   ```cmd
   Dism /online /enable-feature /featurename:Client-DeviceLockdown /featurename:Client-KeyboardFilter 
   ```

1. You're prompted to restart the reference device, type **Y** to reboot. The device reboots into audit mode.

   Once you enable the keyboard filter, see [Keyboard filter PowerShell script samples](../Customize/keyboardfilter-powershell-script-samples.md) to learn about blocking key combinations.

1. For this lab, we're going to provide a demo on blocking the CTRL+ALT+DEL key. In an administrative PowerShell command window, copy and paste the following commands.  

    ```PowerShell
    $key = "Ctrl+Alt+Del"
    $setkey = Get-WMIObject -class WEKF_PredefinedKey –computer localhost –namespace  root\standardcimv2\embedded | where {$_.Id -eq "$key"}; 
    $setkey.Id = $key
    $setkey.Enabled = 1;
    $setkey.Put() | Out-Null;
    ```

1. Restart the reference device and then note the CTRL+ALT+DEL key is blocked.

<!-- TODO: Do we want to remove all locked keys to continue the tutorial? -->

## Unified Write Filter (UWF)

[Unified Write Filter (UWF)](../Customize/Unified-Write-Filter.md) helps to protect your device's configuration by intercepting and redirecting any writes to the drive (app installations, settings changes, saved data) in a virtual overlay. This overlay is automatically deleted by rebooting unless configured to be retained until the Unified Write Filter is disabled.

### Enable the UWF

1. Enable the Unified Write Filter feature by running the following command from an Administrative Command Prompt:

   ```cmd
   Dism /online /enable-feature /featureName:Client-DeviceLockdown /featureName:Client-UnifiedWriteFilter
   ```

1. Restart the reference device

1. Configuring and enabling the overlay and protection is best done through scripting but for this lab we configure using command line

   For more information about the UWF, including sample scripts, see [Unified Write Filter (UWF)](../Customize/Unified-Write-Filter.md).

1. At an Administrative Command prompt, run the following commands:

   ```cmd
   uwfmgr volume protect c:
   uwfmgr filter enable
   ```

1. Restart the reference device

1. At an Administrative Command prompt, confirm that UWF is running. **Filer state** should be **ON**:

   ```cmd
   uwfmgr.exe get-config
   ```

1. Now all writes are redirected to the RAM overlay, which is discarded when the reference device is rebooted.

1. Try removing **Windows Media Player Legacy (App)** Optional feature, from an Administrative Command Prompt:

      ```cmd
      Dism /online /Disable-Feature /FeatureName:"WindowsMediaPlayer"
      ```

1. You can see that the feature is removed but when you restart the device, the feature is back.

1. Restart the reference device

1. To disable the Unified Write Filter, at an Administrative Command prompt run the following command and then reboot the device.

   ```cmd
   uwfmgr filter disable  
   ```

1. At an Administrative Command prompt, confirm that UWF is disabled. **Filer state** should be **OFF**:

   ```cmd
   uwfmgr.exe get-config
   ```

> [!NOTE]
> When using the Unified Write Filter you must take into consideration the Operating System product activation. Product activation must be done with the Unified Write Filter disabled. Also, when cloning the image to other devices the image needs to be in a Sysprep state and the filter disabled prior to capturing the image.

## Unbranded boot

[Unbranded boot](../Customize/Unbranded-Boot.md) allows you to:

- Suppress Windows elements that appear when Windows starts or resumes.
- Suppress the crash screen when Windows encounters an error that it can't recover from.

### Enable Unbranded boot

1. Enable the Unbranded boot feature by running the following command in an Administrative Command Prompt:

    ```cmd
    Dism /online /enable-feature /featureName:Client-DeviceLockdown  
    Dism /online /enable-feature /FeatureName:Client-EmbeddedBootExp 
    ```

1. Restart the reference device

### Configure Unbranded Boot settings at runtime using BCDEdit

You can customize Unbranded boot from an Administrative Command prompt in the following ways:

1. Disable the F8 key during startup to prevent access to the Advanced startup options menu:

    ```cmd
    bcdedit.exe -set {globalsettings} advancedoptions false 
    ```

1. Disable the F10 key during startup to prevent access to the Advanced startup options menu:

    ```cmd
    bcdedit.exe -set {globalsettings} optionsedit false 
    ```

1. Suppress all Windows UI elements (logo, status indicator, and status message) during startup:

    ```cmd
    bcdedit.exe -set {globalsettings} bootuxdisabled on 
    ```

Restart the reference device and notice that the Windows UI elements are suppressed during startup.

> [!NOTE]
> Anytime you rebuild the BCD information, for example using bcdboot, you'll have to re-run the above commands.

## Custom Logon

You can use the [Custom Logon](../Customize/Custom-Logon.md) feature to suppress Windows UI elements that relate to the Welcome screen and shutdown screen. For example, you can suppress all elements of the Welcome screen UI and provide a custom logon UI. You can also suppress the Blocked Shutdown Resolver (BSDR) screen and automatically end applications while the OS waits for applications to close before a shutdown. For more information, see [Custom Logon](../Customize/Custom-Logon.md).

> [!NOTE]
> Custom Logon feature will not work on images that are using a blank or evaluation product key. You must use a valid Product Key to see the changes made with the below commands.

1. Enable the Custom Logon feature by running the following command at an Administrative Command Prompt:

    ```cmd
    Dism /online /enable-feature /featurename:Client-DeviceLockdown /featurename:Client-EmbeddedLogon 
    ```

1. If prompted to restart, choose No.

1. Modify the following registry entries. If prompted to overwrite, choose Yes.

    - This command sets the *BrandingNeutral* value in the registry, which controls the display of branding information during logon.

    ```cmd
    Reg add "HKLM\SOFTWARE\Microsoft\Windows Embedded\EmbeddedLogon" /v BrandingNeutral /t REG_DWORD /d 1
    ```

    - This command sets the *HideAutoLogonUI* value in the registry, which controls the display of the auto logon user interface.

    ```cmd
    Reg add "HKLM\SOFTWARE\Microsoft\Windows Embedded\EmbeddedLogon" /v HideAutoLogonUI /t REG_DWORD /d 1
    ```

    - This command sets the *HideFirstLogonAnimation* value in the registry, which controls the display of the first logon animation.

    ```cmd
    Reg add "HKLM\SOFTWARE\Microsoft\Windows Embedded\EmbeddedLogon" /v HideFirstLogonAnimation /t REG_DWORD /d 1
    ```

    - This command sets the *AnimationDisabled* value in the registry, which controls whether the logon UI animation is disabled.

    ```cmd
    Reg add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Authentication\LogonUI" /v AnimationDisabled /t REG_DWORD /d 1
    ```

    - This command sets the *NoLockScreen* value in the registry, which controls whether the lock screen is displayed.

    ```cmd
    Reg add "HKLM\SOFTWARE\Policies\Microsoft\Windows\Personalization" /v NoLockScreen /t REG_DWORD /d 1
    ```

    - This command sets the *UIVerbosityLevel* value in the registry, which controls the verbosity level of the user interface.

    ```cmd
    Reg add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon" /v UIVerbosityLevel /t REG_DWORD /d 1
    ```

1. Restart the reference device. You should no longer see the Windows UI elements that relate to the Welcome screen and shutdown screen.

## Next steps

You completed enabling lockdown features. You can use group policies to further customize your device's user experience. Lab 3 covers how to configure policy settings.

>[!div class="nextstepaction"]
>[Go to lab 3](iot-ent-configure-policy-settings.md)
