---
title: Keyboard Filter
description: Keyboard Filter
author: sydbruck
ms.author: sybruckm
ms.service: windows-iot
ms.subservice: iot
ms.date: 03/05/2024
ms.topic: article


---
# Keyboard Filter

You can use Keyboard Filter to suppress undesirable key presses or key combinations. Normally, a customer can use certain Microsoft Windows key combinations like Ctrl+Alt+Delete or Ctrl+Shift+Tab to alter the operation of a device by locking the screen or using Task Manager to close a running application. This behavior might not be desirable if your device is intended for a dedicated purpose.

The Keyboard Filter feature works with physical keyboards, the Windows on-screen keyboard, and the touch keyboard. Switching from one language to another might cause the location of suppressed keys on the keyboard layout to change. Keyboard Filter detects these dynamic layout changes and continues to suppress keys correctly.

> [!NOTE]
> Keyboard filter is not supported in a remote desktop session.

## Requirements

Keyboard Filter can be enabled on:

- Windows 10 Enterprise
- Windows 10 IoT Enterprise
- Windows 10 Education
- Windows 11 Enterprise
- Windows 11 IoT Enterprise
- Windows 11 Education

## Terminology

* **Turn on, enable:** Make the setting available to the device and optionally apply the settings to the device. Generally *turn on* is used in the user interface or control panel, whereas *enable* is used for command line.

* **Configure:** To customize the setting or subsettings.

* **Embedded Keyboard Filter:** This feature is called Embedded Keyboard Filter in Windows 10, version 1511.

* **Keyboard Filter:** This feature is called Keyboard Filter in Windows 10, version 1607 and later.

## Turn on Keyboard Filter

By default, Keyboard Filter isn't turned on. You can turn Keyboard Filter on or off for your device by using the following steps.

Turning on an off Keyboard Filter requires that you restart your device. Keyboard Filter is automatically enabled after the restart.

### Turn on Keyboard Filter by using Control Panel

1. In the Windows search bar, type **Turn Windows features on or off** and either press **Enter** or tap or select **Turn Windows features on or off** to open the **Windows Features** window.
1. In the **Windows Features** window, expand the **Device Lockdown** node, and select (to turn on) or clear (to turn off) the checkbox for **Keyboard Filter**.
1. Select **OK**. The **Windows Features** window indicates that Windows is searching for required files and displays a progress bar. Once found, the window indicates that Windows is applying the changes. When completed, the window indicates the requested changes are completed.
1. Restart your device to apply the changes.

### Configure Keyboard using Unattend

1. You can configure the Unattend settings in the [Microsoft-Windows-Embedded-KeyboardFilterService](/windows-hardware/customize/desktop/unattend/microsoft-windows-embedded-keyboardfilterservice) component to add Keyboard Filter features to your image during the design or imaging phase.
1. You can manually create an Unattend answer file or use Windows System Image Manager (Windows SIM) to add the appropriate settings to your answer file. For more information about the keyboard filter settings and XML examples, see the settings in [Microsoft-Windows-Embedded-KeyboardFilterService](/windows-hardware/customize/desktop/unattend/microsoft-windows-embedded-keyboardfilterservice).

### Turn on and configure Keyboard Filter using Windows Configuration Designer

The Keyboard Filter settings are also available as Windows provisioning settings so you can configure these settings to be applied during the image deployment time or runtime. You can set one or all keyboard filter settings by creating a provisioning package using Windows Configuration Designer and then applying the provisioning package during image deployment time or runtime.

1. Build a provisioning package in Windows Configuration Designer by following the instructions in [Create a provisioning package](/windows/configuration/provisioning-packages/provisioning-create-package), selecting the **Advanced Provisioning** option.

   > [!Note]
   > In the **Choose which settings to view and configure** window, choose **Common to all Windows desktop editions**.

1. On the **Available customizations** page, select **Runtime settings** &gt; **SMISettings**, and then set the desired values for the keyboard filter settings.
1. Once you have finished configuring the settings and building the provisioning package, you can apply the package to the image deployment time or runtime. For more information, see [Apply a provisioning package](/windows/configuration/provisioning-packages/provisioning-apply-package).

This example uses a Windows image called install.wim, but you can use the same procedure to apply a provisioning package. For more information on DISM, see [What Is Deployment Image Servicing and Management](/windows-hardware/manufacture/desktop/what-is-dism).

### Turn on and configure Keyboard Filter by using DISM

1. Open a command prompt with administrator privileges.
1. Enable the feature using the following command.

   ```cmd
   Dism /online /Enable-Feature /FeatureName:Client-KeyboardFilter
   ```

1. Once the script completes, restart the device to apply the change.

## Keyboard Filter features

Keyboard Filter has the following features:

* Supports hardware keyboards, the standard Windows on-screen keyboard, and the touch keyboard (TabTip.exe).
* Suppresses key combinations even when they come from multiple keyboards.

    For example, if a user presses the Ctrl key and the Alt key on a hardware keyboard, while at the same time pressing Delete on a software keyboard, Keyboard Filter can still detect and suppress the Ctrl+Alt+Delete functionality.

* Supports numeric keypads and keys designed to access media player and browser functionality.
* Can configure a key to breakout of a locked down user session to return to the Welcome screen.
* Automatically handles dynamic layout changes.
* Can be enabled or disabled for administrator accounts.
* Can force disabling of Ease of Access functionality.
* Supports x86 and x64 architectures.

## Keyboard scan codes and layouts

When a key is pressed on a physical keyboard, the keyboard sends a scan code to the keyboard driver. The driver then sends the scan code to the OS and the OS converts the scan code into a virtual key based on the current active layout. The layout defines the mapping of keys on the physical keyboard, and has many variants. A key on a keyboard always sends the same scan code when pressed, however this scan code can map to different virtual keys for different layouts. For example, in the English (United States) keyboard layout, the key to the right of the P key maps to “{“. However, in the Swedish (Sweden) keyboard layout, the same key maps to “Å”.

Keyboard Filter can block keys either by the scan code or the virtual key. Blocking keys by the scan code is useful for custom keyboards that have special scan codes that don't translate into any single virtual key. Blocking keys by the virtual key is more convenient because it's easier to read and Keyboard Filter suppresses the key correctly even when the location of the key changes because of a layout change.

When you configure Keyboard Filter to block keys by using the virtual key, you must use the English names for the virtual keys. For more information about the names of the virtual keys, see keyboard filter key names.

For the Windows on-screen keyboard, keyboard filter converts each keystroke into a scan code based on the layout, and back into a virtual key. This allows keyboard filter to suppress the on-screen keyboard keys in the same manner as physical keyboard keys if they're configured with either scan code or virtual key.

## Keyboard Filter and ease of access features

By default, ease of access features are enabled and Keyboard Filter is disabled for administrator accounts.

If Sticky Keys are enabled, a user can bypass Keyboard Filter in certain situations. You can configure keyboard filter to disable all ease of access features and prevent users from enabling them.

You can enable ease of access features for administrator accounts, while still disabling them for standard user accounts, by making sure that Keyboard Filter is disabled for administrator accounts.

## Keyboard Filter configuration

You can configure the following options for Keyboard Filter:

* Set/unset predefined key combinations to be suppressed.
* Add/remove custom defined key combinations to be suppressed.
* Enable/disable keyboard filter for administrator accounts.
* Force disabling ease of access features.
* Configure a breakout key sequence to break out of a locked down account.

Most configuration changes take effect immediately. Some changes, such as enabling or disabling Keyboard Filter for administrators, don't take effect until the user signs out of the account and then back in. If you change the breakout key scan code, you must restart the device before the change take effect.

You can configure keyboard filter by using Windows Management Instrumentation (WMI) providers. You can use the Keyboard Filter WMI providers directly in a PowerShell script or in an application.

For more information about Keyboard Filter WMI providers, see [Keyboard Filter WMI provider reference](keyboardfilter-wmi-provider-reference.md).

## Keyboard breakout

You may need to sign in to a locked down device with a different account in order to service or configure the device. You can configure a breakout key to break out of a locked down account by specifying a key scan code. A user can press this key consecutively five times to switch to the Welcome screen so that you can sign in to a different account.

The breakout key is set to the scan code for the left Windows logo key by default. You can use the [WEKF_Settings](wekf-settings.md) WMI class to change the breakout key scan code. If you change the breakout key scan code, you must restart the device before the change takes effect.

## Keyboard Filter considerations

Starting a device in Safe Mode bypasses keyboard filter. The Keyboard Filter service isn't loaded in Safe Mode, and keys aren't blocked in Safe Mode.

Keyboard filter can't block the Sleep key.

Some hardware keys, such as rotation lock, don't have a defined virtual key. You can still block these keys by using the scan code of the key.

The add (+), multiply (\*), subtract (-), divide (/), and decimal (.) keys have different virtual keys and scan codes on the numeric keypad than on the main keyboard. You must block both keys to block these keys. For example, to block the multiply key, you must add a rule to block “\*” and a rule to block Multiply.

When locking the screen by using the on-screen keyboard, or a combination of a physical keyboard and the on-screen keyboard, the on-screen keyboard sends an extra Windows logo key keystroke to the OS. If your device is using the Windows 10 shell and you use keyboard filter to block Windows logo key+L, the extra Windows logo key keystroke causes the shell to switch between the **Start** screen and the last active app when a user attempts to lock the device by using the on-screen keyboard, which may be unexpected behavior.

Some custom keyboard software, such as Microsoft IntelliType Pro, can install Keyboard Filter drivers that prevent Keyboard Filter from being able to block some or all keys, typically extended keys like BrowserHome and Search.

## In this section

* [Keyboard Filter key names](keyboardfilter-key-names.md)
* [Predefined key combinations](predefined-key-combinations.md)
* [Keyboard Filter WMI provider reference](keyboardfilter-wmi-provider-reference.md)
* [Windows PowerShell script samples for Keyboard Filter](keyboardfilter-powershell-script-samples.md)