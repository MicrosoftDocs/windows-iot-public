---
title: Shell Launcher
description: Shell Launcher
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: c65f1400-9d2a-406e-8b43-74eaafb0ccae
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.date: 06/07/2018
ms.topic: article


---
# Shell Launcher

Using Shell Launcher, you can configure a kiosk device to use almost any application or executable as your custom shell. The application that you specify replaces the default shell (explorer.exe) that usually runs when a user logs on.

You can also configure Shell Launcher to launch different shell applications for different users or user groups.

There are a few exceptions to the applications and executables you can use as a custom shell:

- You can't use the following executable as a custom shell: `C:\\Windows\\System32\\Eshell.exe`. Using Eshell.exe as the default shell will result in a blank screen after user signs in.
- You can't use a Universal Windows app as a custom shell.
- You can't use a custom shell to launch Universal Windows apps, for example, the Settings app.  
- You can't use an application that launches a different process and exits as a custom shell. For example, you can't specify **write.exe** in Shell Launcher. Shell Launcher launches a custom shell and monitors the process to identify when the custom shell exits. **Write.exe** creates a 32-bit wordpad.exe process and exits. Because Shell Launcher isn't aware of the newly created wordpad.exe process, Shell Launcher takes action based on the exit code of **Write.exe**, and restart the custom shell.
- You can't prevent the system from shutting down. For Shell Launcher V1 and V2, you can't block the session ending by returning FALSE upon receiving the [WM_QUERYENDSESSION](/windows/win32/shutdown/wm-queryendsession) message in a graphical application or returning FALSE in the [handler routine](/windows/console/handlerroutine) that is added through the [SetConsoleCtrlHandler](/windows/console/setconsolectrlhandler) function in a console application.

> [!NOTE]
> You cannot configure both Shell Launcher and assigned access on the same system.
>
> Use **Shell Launcher V2**, you can specify a Universal Windows app as a custom shell.  Check [Use Shell Launcher to create a Windows 10 kiosk](/windows/configuration/kiosk-shelllauncher) for the differences between Shell Launcher v1 and Shell Launcher V2.

Shell Launcher processes the **Run** and **RunOnce** registry keys before starting the custom shell, so your custom shell doesn’t need to handle the automatic startup of other applications and services.

Shell Launcher also handles the behavior of the system when your custom shell exits. You can configure the shell exit behavior if the default behavior doesn't meet your needs.

Methods of controlling access to other desktop applications and system components can be used in addition to using the Shell Launcher such as, [Group Policy](https://www.microsoft.com/download/details.aspx?id=25250), [AppLocker](/windows/iot/iot-enterprise/customize/application-control#applocker), and [Mobile Device Management](/windows/client-management/mdm/)

> [!NOTE]
>
> In Shell Launcher v1, available in Windows 10, you can only specify a Windows desktop application as the replacement shell. In Shell Launcher v2, available in Windows 10, version 1809 and above, you can also specify a UWP app as the replacement shell.
>
> To use Shell Launcher v2 in version 1809, you need to install the [KB4551853 update](https://support.microsoft.com/topic/may-12-2020-kb4551853-os-build-17763-1217-c2ea33f7-4506-dd13-2739-d9c7bb80b26d).

## Differences between Shell Launcher v1 and Shell Launcher v2

Shell Launcher v1 replaces ```explorer.exe```, the default shell, with ```eshell.exe```, which can launch a Windows desktop application.
Shell Launcher v2 replaces ```explorer.exe``` with ```customshellhost.exe```. This new executable file can launch a Windows desktop application or a UWP app.
In addition to allowing you to use a UWP app for your replacement shell, Shell Launcher v2 offers more enhancements:

- You can use a custom Windows desktop application that can then launch UWP apps, such as Settings and Touch Keyboard.
- From a custom UWP shell, you can launch secondary views and run on multiple monitors.
- The custom shell app runs in full screen, and can run other apps in full screen on user’s demand.
For sample XML configurations for the different app combinations, see [Samples for Shell Launcher v2](https://github.com/microsoft/Windows-IoT-Samples/tree/master/samples/ShellLauncher/ShellLauncherV2).

## Requirements

Windows 10 Enterprise or Windows 10 Education.

## Terminology

- **Turn on, enable:** To make the setting available to the device and optionally apply the settings to the device.
- **Configure:** To customize the setting or subsettings.
- **Embedded Shell Launcher:** This feature is called Embedded Shell Launcher in Windows 10, version 1511.
- **Custom Shell Launcher:** This feature is called Shell Launcher in Windows 10, version 1607 and later.

## Turn on Shell Launcher

Shell Launcher is an optional component and isn't turned on by default in Windows 10. It must be turned on prior to configuring. You can turn on and configure Shell Launcher in a customized Windows 10 image (.wim) if Microsoft Windows hasn't been installed. If Windows has already been installed, you must turn on Shell Launcher before applying a provisioning package to configure Shell Launcher.

### Enable Shell Launcher using Control Panel

1. In the **Search the web and Windows** field, type **Programs and Features** and either press **Enter** or tap or select **Programs and Features** to open it.
1. In the **Programs and Features** window, select **Turn Windows features on or off**.
1. In the **Windows Features** window, expand the **Device Lockdown** node, select or clear the checkbox for **Shell Launcher**, and then select **OK.**
1. The **Windows Features** window indicates that Windows is searching for required files and displays a progress bar. Once found, the window indicates that Windows is applying the changes. When completed, the window indicates the requested changes are completed.
1. Select **Close** to close the **Windows Features** window.

> [!NOTE]
> Turning on Shell Launcher does not require a device restart.

### Enable Shell Launcher by calling WESL_UserSetting

1. Enable or disable Shell Launcher by calling the WESL_UserSetting.SetEnabled function in the Windows Management Instrumentation (WMI) class WESL_UserSetting.
1. If you enable or disable Shell Launcher using WESL_UserSetting, the changes don't affect any sessions that are currently signed in; you must sign out and sign back in.

This example uses a Windows image called install.wim, but you can use the same procedure to apply a provisioning package (for more information on DISM, see [What Is Deployment Image Servicing and Management](/windows-hardware/manufacture/desktop/what-is-dism).

### Enable Shell Launcher using DISM

1. Open a command prompt with administrator privileges.
1. Copy install.wim to a temporary folder on hard drive (in the following steps, we assume it's called C:\\wim).
1. Create a new directory.

    ```CMD
    md c:\wim
    ```

1. Mount the image.

    ```CMD
    dism /mount-wim /wimfile:c:\bootmedia\sources\install.wim /index:1 /MountDir:c:\wim
    ```

1. Enable the feature.

    ```CMD
    dism /image:c:\wim /enable-feature /all /featureName:Client-EmbeddedShellLauncher
    ```

1. Commit the change.

    ```CMD
    dism /unmount-wim /MountDir:c:\wim /Commit
    ```

### Enable Shell Launcher using Windows Configuration Designer

The Shell Launcher settings are also available as Windows provisioning settings so you can configure these settings to be applied during the image runtime. You can set one or all Shell Launcher settings by creating a provisioning package using Windows Configuration Designer and then applying the provisioning package during image deployment time or runtime. If Windows hasn't been installed and you're using Windows Configuration Designer to create installation media with settings for Shell Launcher included in the image or you're applying a provisioning package during setup, you must enable Shell Launcher on the installation media with DISM in order for a provisioning package to successfully apply.

Use the following steps to create a provisioning package that contains the ShellLauncher settings.

1. Build a provisioning package in Windows Configuration Designer by following the instructions in [Create a provisioning package for Windows 10](/windows/configuration/provisioning-packages/provisioning-create-package).
1. In the **Available customizations** page, select **Runtime settings** > **SMISettings** > **ShellLauncher**.
1. Set the value of **Enable** to **ENABLE**. More options to configure Shell Launcher appears, and you can set the values as desired.
1. Once you have finished configuring the settings and creating the provisioning package, you can apply the package to the image deployment time or runtime. See the [Apply a provisioning package](/windows/configuration/provisioning-packages/provisioning-apply-package) for more information. The process for applying the package to a Windows 10 Enterprise image is the same.

## Configure Shell Launcher

There are two ways you can configure Shell Launcher:

1. In Windows 10, version 1803, you can configure Shell Launcher using the **ShellLauncher** node of the Assigned Access Configuration Service Provider (CSP). See [AssignedAccess CSP](/windows/client-management/mdm/assignedaccess-csp) for details. Configuring Shell Launcher using this method also automatically enables Shell Launcher on the device, if the device supports it.
1. Use the Shell Launcher WMI providers directly in a PowerShell script or application.

You can configure the following options for Shell Launcher:

- Enable or disable Shell Launcher.
- Specify a shell configuration for a specific user or group.
- Remove a shell configuration for a specific user or group.
- Change the default shell configuration.
- Get information on a shell configuration for a specific user or group.

Any changes don't take effect until a user signs in.

## Launch different shells for different user accounts

By default, Shell Launcher runs the default shell, which is specified when you create the OS image at design time. The default shell is set to Cmd.exe, but you can specify any executable file to be the default shell.

You can configure Shell Launcher to launch a different shell for specific users or groups if you don't want to run the default shell. For example, you might configure a device to run a custom application shell for guest accounts, but run the standard Windows Explorer shell for administrator accounts in order to service the device.

If you use the WMI providers to configure Shell Launcher for a user or group at run time, you must use the security identifier (SID) for that user or group; you can't use the user name or group name.

For more information about common security identifiers, see [Well-known SIDs](/windows/win32/secauthz/well-known-sids).

When the current signed in account belongs to two or more groups that have different configurations defined for each group, Shell Launcher uses the first configuration it finds. The search order isn't defined, so we recommend that you avoid assigning a user to multiple groups with different Shell Launcher configurations.

## Perform an action when the shell exits

When a custom shell exits, Shell Launcher can perform one of four actions:

|Action|Description|
|:---:|:---|
|0|Restart the shell.|
|1|Restart the device.|
|2|Shut down the device.|
|3|Do nothing.|

> [!IMPORTANT]
> Make sure that your shell application does not automatically exit and is not automatically closed by any features such as Dialog Filter, as this can lead to an infinite cycle of exiting and restarting, unless the return code action is set to do nothing.

### Default return code action

You can define a default return code action for Shell Launcher with the DefaultReturnCodeAction setting. If you don't change the initial value, the default return code action is set to 0 (zero), which indicates that Shell Launcher restarts the shell when the shell exits.

### Map the exit code to a Shell Launcher action

Shell Launcher can take a specific action based on the exit code returned by the shell. For any given exit code returned by the shell, you can configure the action that Shell Launcher takes by mapping that exit code to one of the shell exit actions.

If the exit code doesn't match a defined value, Shell Launcher performs the default return code action.

For example, your shell might return exit code values of -1, 0, 1, or 255 depending on how the shell exits. You can configure Shell Launcher to:

- restart the device (1) when the shell returns an exit code of value -1
- restart the shell (0) when the shell returns an exit code of value 0
- do nothing (3) when the shell returns an exit code of value 1
- shut down the device (2) when the shell returns an exit code of value 255

Your custom return code action mapping would look like this:

|Exit code|Action|
|:----:|----|
|-1|1 (restart the device)|
|0|0 (restart the shell)|
|1|3 (do nothing)|
|255|2 (shut down the device)|

## Set your custom shell

Modify the following PowerShell script as appropriate and run the script on the device.

```PowerShell
# Check if shell launcher license is enabled
function Check-ShellLauncherLicenseEnabled
{
    [string]$source = @"
using System;
using System.Runtime.InteropServices;

static class CheckShellLauncherLicense
{
    const int S_OK = 0;

    public static bool IsShellLauncherLicenseEnabled()
    {
        int enabled = 0;

        if (NativeMethods.SLGetWindowsInformationDWORD("EmbeddedFeature-ShellLauncher-Enabled", out enabled) != S_OK) {
            enabled = 0;
        }
        return (enabled != 0);
    }

    static class NativeMethods
    {
        [DllImport("Slc.dll")]
        internal static extern int SLGetWindowsInformationDWORD([MarshalAs(UnmanagedType.LPWStr)]string valueName, out int value);
    }

}
"@

    $type = Add-Type -TypeDefinition $source -PassThru

    return $type[0]::IsShellLauncherLicenseEnabled()
}

[bool]$result = $false

$result = Check-ShellLauncherLicenseEnabled
"`nShell Launcher license enabled is set to " + $result
if (-not($result))
{
    "`nThis device doesn&#39;t have required license to use Shell Launcher"
    exit
}

$COMPUTER = "localhost"
$NAMESPACE = "root\standardcimv2\embedded"

# Create a handle to the class instance so we can call the static methods.
try {
    $ShellLauncherClass = [wmiclass]"\\$COMPUTER\${NAMESPACE}:WESL_UserSetting"
    } catch [Exception] {
    write-host $_.Exception.Message; 
    write-host "Make sure Shell Launcher feature is enabled"
    exit
    }


# This well-known security identifier (SID) corresponds to the BUILTIN\Administrators group.

$Admins_SID = "S-1-5-32-544"

# Create a function to retrieve the SID for a user account on a machine.

function Get-UsernameSID($AccountName) {

    $NTUserObject = New-Object System.Security.Principal.NTAccount($AccountName)
    $NTUserSID = $NTUserObject.Translate([System.Security.Principal.SecurityIdentifier])

    return $NTUserSID.Value
}

# Get the SID for a user account named "Cashier". Rename "Cashier" to an existing account on your system to test this script.

$Cashier_SID = Get-UsernameSID("Cashier")

# Define actions to take when the shell program exits.

$restart_shell = 0
$restart_device = 1
$shutdown_device = 2
$do_nothing = 3

# Examples. You can change these examples to use the program that you want to use as the shell.

# This example sets the command prompt as the default shell, and restarts the device if the command prompt is closed. 

$ShellLauncherClass.SetDefaultShell("cmd.exe", $restart_device)

# Display the default shell to verify that it was added correctly.

$DefaultShellObject = $ShellLauncherClass.GetDefaultShell()

"`nDefault Shell is set to " + $DefaultShellObject.Shell + " and the default action is set to " + $DefaultShellObject.defaultaction

# Set Internet Explorer as the shell for "Cashier", and restart the machine if Internet Explorer is closed.

$ShellLauncherClass.SetCustomShell($Cashier_SID, "c:\program files\internet explorer\iexplore.exe www.microsoft.com", ($null), ($null), $restart_shell)

# Set Explorer as the shell for administrators.

$ShellLauncherClass.SetCustomShell($Admins_SID, "explorer.exe")

# View all the custom shells defined.

"`nCurrent settings for custom shells:"
Get-WmiObject -namespace $NAMESPACE -computer $COMPUTER -class WESL_UserSetting | Select Sid, Shell, DefaultAction

# Enable Shell Launcher

$ShellLauncherClass.SetEnabled($TRUE)

$IsShellLauncherEnabled = $ShellLauncherClass.IsEnabled()

"`nEnabled is set to " + $IsShellLauncherEnabled.Enabled

# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)

# Disable Shell Launcher

$ShellLauncherClass.SetEnabled($FALSE)

$IsShellLauncherEnabled = $ShellLauncherClass.IsEnabled()

"`nEnabled is set to " + $IsShellLauncherEnabled.Enabled
```

> [!NOTE]
> The previous script includes examples of multiple configuration options, including removing a custom shell and disabling Shell Launcher. It is not intended to be run as-is.

## Shell Launcher user rights

A custom shell is launched with the same level of user rights as the account that is signed in. This means that a user with administrator rights can perform any system action that requires administrator rights, including launching other applications with administrator rights, while a user without administrator rights can't.

> [!WARNING]
> If your shell application requires administrator rights and needs to be elevated, and User Account Control (UAC) is present on your device, you must disable UAC in order for Shell Launcher to launch the shell application.

## Related articles

- [Unbranded Boot](unbranded-boot.md)
- [Custom Logon](custom-logon.md)
- [Use Shell Launcher to create a Windows 10 Kiosk](/windows/configuration/kiosk-shelllauncher)
- [Launch different shells for different user accounts](/windows-hardware/customize/enterprise/shell-launcher#launch-different-shells-for-different-user-accounts)
- [Perform an action when the shell exits](/windows-hardware/customize/enterprise/shell-launcher#perform-an-action-when-the-shell-exits)
- [Shell Launcher user rights](/windows-hardware/customize/enterprise/shell-launcher#shell-launcher-user-rights)
