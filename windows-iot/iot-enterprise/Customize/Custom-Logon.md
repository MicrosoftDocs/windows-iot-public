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
ms.date: 05/02/2017
ms.topic: article


---
# Custom Logon

You can use the Custom Logon feature to suppress Windows UI elements that relate to the Welcome screen and shutdown screen. For example, you can suppress all elements of the Welcome screen UI and provide a custom logon UI. You can also suppress the Blocked Shutdown Resolver (BSDR) screen and automatically end applications while the OS waits for applications to close before a shutdown.

Custom Logon settings do not modify the credential behavior of **Winlogon**, so you can use any credential provider that is compatible with Windows 10 to provide a custom sign-in experience for your device. For more information about creating a custom logon experience, see [Winlogon and Credential Providers](/windows/win32/secauthn/winlogon-and-credential-providers).

## Requirements

Windows 10 Enterprise or Windows 10 Education.

## Terminology

**Turn on, enable:** To make the setting available to the device and optionally apply the settings to the device. Generally *turn on* is used in the user interface or control panel, whereas *enable* is used for command line.

**Configure:** To customize the setting or sub-settings.

**Embedded Logon:** This feature is called Embedded Logon in Windows 10, version 1511.

**Custom Logon:** This feature is called Custom Logon in Windows 10, version 1607 and later.

## Turn on Custom Logon

Custom Logon is an optional component and is not turned on by default in Windows 10. It must be turned on prior to configuring. You can turn on and configure Custom Logon in a customized Windows 10 image (.wim) if Microsoft Windows has not been installed. If Windows has already been installed and you are applying a provisioning package to configure Custom Logon, you must first turn on Custom Logon in order for a provisioning package to be successfully applied.

The Custom Logon feature is available in the Control Panel. You can set Custom Logon by following these steps:

### Turn on Custom Logon in Control Panel

1. In the **Search the web and Windows** field, type **Turn Windows features on or off**.
1. In the **Windows Features** window, expand the **Device Lockdown** node, and select or clear the checkbox for **Custom Logon**.

### Turn on and configure Custom Logon using DISM

1. Open a command prompt with administrator rights.
1. Copy install.wim to a temporary folder on hard drive (in the following steps, we'll assume it's called C:\\wim).
1. Create a new directory.

    ```cmd
    md c:\wim
    ```

1. Mount the image.

    ```cmd
    dism /mount-wim /wimfile:c:\bootmedia\sources\install.wim /index:1 /MountDir:c:\wim
    ```

1. Enable the feature.

    ```cmd
    dism /image:c:\wim /enable-feature /featureName:Client-EmbeddedLogon
    ```

1. Commit the change.

    ```cmd
    dism /unmount-wim /MountDir:c:\wim /Commit
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

## Related topics

- [Complementary features to Custom Logon](complementary-features-to-custom-logon.md)
- [Troubleshooting Custom Logon](troubleshooting-custom-logon.md)
- [Unbranded Boot](unbranded-boot.md)
- [Shell Launcher](shell-launcher.md)
