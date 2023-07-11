---
title: Unbranded Boot
description: Unbranded Boot
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 3b9be4eb-a4ab-41fe-95a7-9f52ced71ad9
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 03/06/2018
ms.topic: article


---
# Unbranded Boot

You can suppress Windows elements that appear when Windows starts or resumes and can suppress the crash screen when Windows encounters an error that it cannot recover from. This feature is known as Unbranded Boot.

> [!IMPORTANT]
> The first user to sign in to the device must be an administrator. This ensures that the **RunOnce** registry settings correctly apply the settings. Also, when using auto sign-in, you must not configure auto sign-in on your device at design time. Instead, auto sign-in should be configured manually after first signing in as an administrator.

## Requirements

Windows 10 Enterprise, Windows 10 Professional, or Windows 10 Education.

## Terminology

* **Turn on, Enable:** To make the setting available to the device and optionally apply the settings to the device. Generally "turn on" is used in the user interface or control panel, whereas "enable" is used for command line.

* **Configure:** To customize the setting or sub-settings.

* **Embedded Boot Experience:** this feature is called "Embedded Boot Experience" in Windows 10, build 1511.

* **Custom Boot Experience:** this feature is called "Custom Boot Experience" in Windows 10, build 1607 and later.

## Turn on Unbranded Boot settings

Unbranded Boot is an optional component and is not enabled by default in Windows 10. It must be enabled prior to configuring. For end-users, Unbranded Boot is available through **Control Panel** &gt; **Programs** &gt; **Programs and Features** &gt; **Turn Windows features on or off**.

If Windows has already been installed you cannot apply a provisioning package to configure Unbranded Boot; instead you must use BDCEdit to configure Unbranded boot if Windows is installed.

BCDEdit is the primary tool for editing the startup configuration and is on your development computer in the %WINDIR%\\System32 folder. You have administrator rights for it. BCDEdit is included in a typical Windows Preinstallation Environment (Windows PE) 4.0. You can download it from the [BCDEdit Commands for Boot Environment](/previous-versions/windows/hardware/design/dn653986(v=vs.85)) in the Microsoft Download Center if needed.

### Turn on Unbranded Boot by using Control Panel

1. In the **Search the web and Windows** field, type Programs and Features and either press Enter or tap or click **Programs and Features** to open it.
1. In the **Programs and Features** window, click **Turn Windows features on or off**.
1. In the **Windows Features** window, expand the **Device Lockdown** node, and check or clear the checkbox for **Unbranded Boot**.
1. Click **OK**. The **Windows Features** window indicates Windows is searching for required files and displays a progress bar. Once found, the window indicates Windows is applying the changes. When completed, the window indicates the requested changes are completed.
1. Click **Close** to close the **Windows Features** window.

## Configure Unbranded Boot settings at runtime using BCDEdit

1. Open a command prompt as an administrator.
1. To disable the F8 key during startup to prevent access to the **Advanced startup options** menu, type the following:

   ```cmd
   bcdedit.exe -set {globalsettings} advancedoptions false
   ```

1. To disable the F10 key during startup to prevent access to the **Advanced startup options** menu, type the following:

   ```cmd
   bcdedit.exe -set {globalsettings} optionsedit false
   ```

1. To suppress all Windows UI elements (logo, status indicator, and status message) during startup, type the following:

   ```cmd
   bcdedit.exe -set {globalsettings} bootuxdisabled on
   ```
   
1. To suppress error display during boot, type the following:

   ```cmd
   bcdedit.exe -set {bootmgr} noerrordisplay on
   ```
   
## Configure Unbranded Boot using Unattend

You can also configure the Unattend settings in the [Microsoft-Windows-Embedded-BootExp](/windows-hardware/customize/desktop/unattend/microsoft-windows-embedded-bootexp) component to add Unbranded Boot features to your image during the design or imaging phase. You can manually create an Unattend answer file or use Windows System Image Manager (Windows SIM) to add the appropriate settings to your answer file. For more information about the Unbranded Boot settings and XML examples, see the settings in Microsoft-Windows-Embedded-BootExp.

### Unbranded Boot settings

The following table shows Unbranded Boot settings and their values.

<table>
<thead valign="bottom">
<tr class="header">
<th>Setting</th>
<th>Description</th>
</tr>
</thead>
<tbody valign="top">
<tr class="odd">
<td>DisableBootMenu</td>
<td>Contains an integer that disables the F8 and F10 keys during startup to prevent access to the Advanced startup options menu.
<p>Set to 1 to disable the menu; otherwise; set to 0 (zero). The default value is 0.</p></td>
</tr>
<tr class="even">
<td>DisplayDisabled</td>
<td>Contains an integer that configures the device to display a blank screen when Windows encounters an error that it cannot recover from.
<p>Set to 1 to display a blank screen on error; otherwise; set to 0 (zero). The default value is 0.</p></td>
</tr>
<tr class="odd">
<td>HideAllBootUI</td>
<td>Contains an integer that suppresses all Windows UI elements (logo, status indicator, and status message) during startup.
<p>Set to 1 to suppress all Windows UI elements during startup; otherwise; set to 0 (zero). The default value is 0.</p></td>
</tr>
<tr class="even">
<td>HideBootLogo</td>
<td>Contains an integer that suppresses the default Windows logo that displays during the OS loading phase.
<p>Set to 1 to suppress the default Windows logo; otherwise; set to 0 (zero). The default value is 0.</p></td>
</tr>
<tr class="odd">
<td>HideBootStatusIndicator</td>
<td>Contains an integer that suppresses the status indicator that displays during the OS loading phase.
<p>Set to 1 to suppress the status indicator; otherwise; set to 0 (zero). The default value is 0.</p></td>
</tr>
<tr class="even">
<td>HideBootStatusMessage</td>
<td>Contains an integer that suppresses the startup status text that displays during the OS loading phase.
<p>Set to 1 to suppress the startup status text; otherwise; set to 0 (zero). The default value is 0.</p></td>
</tr>
</tbody>
</table>

## <a href="" id="custom-boot"></a>Customize the boot screen using Windows Configuration Designer and Deployment Image Servicing and Management (DISM)

If Windows has not been installed and you are using Windows Configuration Designer to create installation media with settings for Unbranded Boot included in the image, or you are applying a provisioning package during setup, you must enable Unbranded Boot on the installation media with DISM in order for a provisioning package to successfully apply. First you have to create the image or package.

1. Create a provisioning package or create a new Windows image in Windows Configuration Designer by following the instructions in [Create a provisioning package](/windows/configuration/provisioning-packages/provisioning-create-package).

1. In the Available customizations page, select **Runtime settings** &gt; **SMISettings** and then set the value for the boot screen settings. The following values are just examples.
   * **HideAllBootUI**=FALSE
   * **HideBootLogo**=FALSE
   * **HideBootStatusIndicator**=TRUE
   * **HideBootStatusMessage**=TRUE
   * **CrashDumpEnabled**=Full dump

   > [!Tip]
   > See [SMISettings](/windows/configuration/wcd/wcd-smisettings) in the Windows Configuration Designer reference for more information about the available SMISettings.

1. Once you have finished configuring the settings and building the package or image, you use DISM to apply the settings.
   1. Open a command prompt with administrator privileges.
   1. Copy install.wim to a temporary folder on hard drive (in the following steps, it assumes it's called c:\\wim).
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
      dism /image:c:\wim /enable-feature /featureName:Client-EmbeddedBootExp
      ```

   1. Commit the change.

      ```cmd
      dism /unmount-wim /MountDir:c:\wim /Commit
      ```

In the following image, the BootLogo is identified by the green outline, the BootStatusIndicator is identified by the red outline, and the BootStatusMessage is identified by the blue outline.

![unbranded boot screen](images/boot.jpg)

## <a href="" id="replace-logo"></a>Replace the startup logo

The only supported way to replace the startup logo with a custom logo is to modify the Boot Graphics Resource Table (BGRT) on a device that uses UEFI as the firmware interface. If your device uses the BGRT to include a custom logo, it is always displayed and you cannot suppress the custom logo.

## Suppress Crash Screens

Microsoft offers Windows 10 IoT Enterprise customers methods to manage crash screens.
### Errors During Boot Phase
The **noerrordisplay** switch takes care of exhaustively suppressing all error display during the boot phase.
For example, if **noerrordisplay** to on, and if the boot manager hits a *WinLoad Error* or *Bad Disk Error*, the system will sit at a black screen and require manual reset.
Review [Configure Unbranded Boot settings at runtime using BCDEdit](/windows-hardware/customize/enterprise/unbranded-boot#configure-unbranded-boot-settings-at-runtime-using-bcdedit) to enable the **noerrordisplay** setting.
> [!NOTE]
>
> BCDEdit is the primary tool for editing the startup configuration and is on your development computer in the %WINDIR%\System32 folder. You have administrator rights for it. BCDEdit is included in a typical Windows Preinstallation Environment (Windows PE) 4.0. You can download it from the [BCDEdit Commands for Boot Environment](/previous-versions/windows/hardware/design/dn653986(v=vs.85)) in the Microsoft Download Center if needed.

### Exception Error

To ensure that there is no crash screen if Windows encounters an error it cannot recover from, enable the [DisplayDisabled](/windows-hardware/customize/desktop/unattend/microsoft-windows-embedded-bootexp-displaydisabled) setting using [Unattend](/windows-hardware/customize/enterprise/unbranded-boot#configure-unbranded-boot-using-unattend).
You can also configure the Unattend settings in the Microsoft-Windows-Embedded-BootExp component to add Unbranded Boot features to your image during the design or imaging phase. You can manually create an Unattend answer file or use Windows System Image Manager (Windows SIM) to add the appropriate settings to your answer file. For more information about the Unbranded Boot settings and XML examples, see the settings in [Microsoft-Windows-Embedded-BootExp](/windows-hardware/customize/desktop/unattend/microsoft-windows-embedded-bootexp).

## Related topics

[Custom Logon](custom-logon.md)
