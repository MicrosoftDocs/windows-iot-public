---
title: Custom Logon
description: Custom Logon
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: aaf4ddd3-eac4-4c60-90c8-38837078c43b
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 01/17/2024
ms.topic: article


---
# Custom Logon

You can use the Custom Logon feature to suppress Windows UI elements that relate to the Welcome screen and shutdown screen. For example, you can suppress all elements of the Welcome screen UI and provide a custom logon UI. You can also suppress the Blocked Shutdown Resolver (BSDR) screen and automatically end applications while the OS waits for applications to close before a shutdown.

Custom Logon settings don't modify the credential behavior of **Winlogon**, so you can use any credential provider that is compatible with Windows 10 to provide a custom sign-in experience for your device. For more information about creating a custom logon experience, see [Winlogon and Credential Providers](/windows/win32/secauthn/winlogon-and-credential-providers).

## Requirements

Custom Logon can be enabled on:

- Windows 10 Enterprise
- Windows 10 IoT Enterprise
- Windows 10 Education
- Windows 11 Enterprise
- Windows 11 IoT Enterprise
- Windows 11 Education

## Terminology

**Turn on, enable:** To make the feature available and optionally apply settings to the device. Generally *turn on* is used in the user interface or control panel, whereas *enable* is used for command line.

**Configure:** To customize the setting or subsettings.

**Embedded Logon:** This feature is called Embedded Logon in Windows 10, version 1511.

**Custom Logon:** This feature is called Custom Logon in Windows 10, version 1607 and later.

## Turn on Custom Logon

Custom Logon is an optional component and isn't turned on by default in Windows 10. It must be turned on prior to configuring. You can turn on and configure Custom Logon in a customized Windows 10 image (.wim) if Microsoft Windows hasn't been installed. If Windows has already been installed and you're applying a provisioning package to configure Custom Logon, you must first turn on Custom Logon in order for a provisioning package to be successfully applied.

The Custom Logon feature is available in the Control Panel. You can set Custom Logon by following these steps:

### Turn on Custom Logon in Control Panel

1. In the Windows search bar, type **Turn Windows features on or off** and either press **Enter** or tap or select **Turn Windows features on or off** to open the **Windows Features** window.
1. In the **Windows Features** window, expand the **Device Lockdown** node, and select (to turn on) or clear (to turn off) the checkbox for **Custom Logon**.
1. 1. Select **OK**. The **Windows Features** window indicates that Windows is searching for required files and displays a progress bar. Once found, the window indicates that Windows is applying the changes. When completed, the window indicates the requested changes are completed.

### Turn on and configure Custom Logon using DISM

1. Open a command prompt with administrator rights.
1. Enable the feature using the following command.

    ```cmd
    dism /online /enable-feature /featureName:Client-EmbeddedLogon
    ```

### Configure Custom Logon settings using Unattend

You can configure the Unattend settings in the [Microsoft-Windows-Embedded-EmbeddedLogon](/windows-hardware/customize/desktop/unattend/microsoft-windows-embedded-embeddedlogon) component to add custom logon features to your image during the design or imaging phase. You can manually create an Unattend answer file or use Windows System Image Manager (Windows SIM) to add the appropriate settings to your answer file. For more information about the custom logon settings and XML examples, see the settings in Microsoft-Windows-Embedded-EmbeddedLogon.

The following example shows how to disable all Welcome screen UI elements and the **Switch user** button.

```xml
<settings pass="specialize">
    <component name="Microsoft-Windows-Embedded-EmbeddedLogon" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <BrandingNeutral>17</BrandingNeutral>
      <AnimationDisabled>1</AnimationDisabled>
      <NoLockScreen>1</NoLockScreen>
      <UIVerbosityLevel>1</UIVerbosityLevel>
      <HideAutoLogonUI>1</HideAutoLogonUI>
    </component>
</settings>
```

## Related articles

- [Complementary features to Custom Logon](complementary-features-to-custom-logon.md)
- [Troubleshooting Custom Logon](troubleshooting-custom-logon.md)
- [Unbranded Boot](unbranded-boot.md)
- [Shell Launcher](shell-launcher.md)
