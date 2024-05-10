---
title: WESL_UserSetting
description: WESL_UserSetting
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 73c5bb46-bf9e-4657-a5ae-88dbd14b79e8
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
ms.date: 05/02/2017
ms.topic: article


---
# WESL_UserSetting

This class configures which application Shell Launcher starts based on the security identifier (SID) of the signed in user, and also configures the set of return codes and return actions that Shell Launcher performs when the application exits.

## Syntax

```powershell
class WESL_UserSetting {
    [read, write, Required] string Sid;
    [read, write, Required] string Shell;
    [read, write]  Sint32 CustomReturnCodes[];
    [read, write]  Sint32 CustomReturnCodesAction[];
    [read, write] sint32 DefaultAction;

    [Static] uint32 SetCustomShell(
        [In, Required] string Sid,
        [In, Required] string Shell,
        [In] sint32 CustomReturnCodes[],
        [In] sint32 CustomReturnCodesAction[],
        [In] sint32 DefaultAction
    );
    [Static] uint32 GetCustomShell(
        [In, Required] string Sid,
        [Out, Required] string Shell,
        [Out, Required] sint32 CustomReturnCodes[],
        [Out, Required] sint32 CustomReturnCodesAction[],
        [Out, Required] sint32 DefaultAction
    );
    [Static] uint32 RemoveCustomShell(
        [In, Required] string Sid
    );
    [Static] uint32 GetDefaultShell(
        [Out, Required] string Shell,
        [Out, Required] sint32 DefaultAction
    );
    [Static] uint32 SetDefaultShell(
        [In, Required] string Shell,
        [In, Required] sint32 DefaultAction
    );
    [Static] uint32 IsEnabled(
        [Out, Required] boolean Enabled
    );
    [Static] uint32 SetEnabled(
        [In, Required] boolean Enabled);
    );
};
```

## Members

The following tables list any methods and properties that belong to this class.

### Methods

| Methods | Description |
|---------|-------------|
| [WESL_UserSetting.SetCustomShell](wesl-usersettingsetcustomshell.md) | Configures Shell Launcher for a specific user or group, based on SID. |
| [WESL_UserSetting.GetCustomShell](wesl-usersettinggetcustomshell.md) | Retrieves the Shell Launcher configuration for a specific user or group, based on the SID. |
| [WESL_UserSetting.RemoveCustomShell](wesl-usersettingremovecustomshell.md) | Removes a Shell Launcher configuration for a specific user or group, based on the SID. |
| [WESL_UserSetting.GetDefaultShell](wesl-usersettinggetdefaultshell.md) | Retrieves the default Shell Launcher configuration. |
| [WESL_UserSetting.SetDefaultShell](wesl-usersettingsetdefaultshell.md) | Sets the default Shell Launcher configuration. |
| [WESL_UserSetting.IsEnabled](wesl-usersettingisenabled.md) | Retrieves a value that indicates if Shell Launcher is enabled or disabled. |
| [WESL_UserSetting.SetEnabled](wesl-usersettingsetenabled.md) | Enables or disables Shell Launcher. |

### Properties

| Property | Data&nbsp;type | Qualifiers | Description |
|----------|----------------|------------|-------------|
| **Sid** | string | [read, write, required] | User or group SID. |
| **shell** | string | [read, write, required] | The application to start as the shell.</br>The **shell** property can be a filename in the *Path* environment variable, or it can contain a fully qualified path to the application. You can also use environment variables in the path.</br>Any spaces in the **shell** property must be part of a quote-delimited string. |
| **CustomReturnCodes** | Sint32[] |[read, write] | An array of custom return codes that can be returned by the shell. |
| **CustomReturnCodesAction** | Sint32[] | [read, write] | An array of custom return code actions that determine what action Shell Launcher takes when the shell exits. The custom actions map to the array of **CustomReturnCodes**.</br>The possible actions are:</br>0 - Restart the shell.</br>1 - Restart the device.</br>2 - Shut down the device.</br>3 - Do nothing. |
| **DefaultAction** | Sint32 | [read, write] | The default action Shell Launcher takes when the shell exits.</br>The possible actions are defined as follows:</br>0 - Restart the shell.</br>1 - Restart the device.</br>2 - Shut down the device.</br>3 - Do nothing. |

### Remarks

Only one **WESL_UserSetting** instance exists on a device with Shell Launcher.

Shell Launcher uses the custom configuration defined for the SID of the user currently signed in, if one exists. Otherwise, Shell Launcher uses a custom configuration defined for a group SID that the user is a member of, if any exist. If multiple group custom configurations for the user exist, Shell Launcher uses the first valid configuration it finds. The search order is not defined.

If there is no custom configuration for the user’s SID or any group SIDs that the user is a member of, Shell Launcher uses the default configuration.

You can find the SID for a user and any groups that the user is a member of by using the [whoami](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771299(v=ws.10)) command-line tool.

## Example

The following Windows PowerShell script demonstrates how to add and remove custom shell configurations for Shell Launcher by using the Windows Management Instrumentation (WMI) providers for Shell Launcher.

```powershell
$COMPUTER = "localhost"
$NAMESPACE = "root\standardcimv2\embedded"

# Create a handle to the class instance so we can call the static methods.
$ShellLauncherClass = [wmiclass]"\\$COMPUTER\${NAMESPACE}:WESL_UserSetting"


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

# Examples

# Set the command prompt as the default shell, and restart the device if it's closed.

$ShellLauncherClass.SetDefaultShell("cmd.exe", $restart_device)

# Display the default shell to verify that it was added correctly.

$DefaultShellObject = $ShellLauncherClass.GetDefaultShell()

"`nDefault Shell is set to " + $DefaultShellObject.Shell + " and the default action is set to " + $DefaultShellObject.defaultaction

# Set Internet Explorer as the shell for "Cashier", and restart the machine if it's closed.

$ShellLauncherClass.SetCustomShell($Cashier_SID, "c:\program files\internet explorer\iexplore.exe www.microsoft.com", ($null), ($null), $restart_shell)

# Set Explorer as the shell for administrators.

$ShellLauncherClass.SetCustomShell($Admins_SID, "explorer.exe")

# View all the custom shells defined.

"`nCurrent settings for custom shells:"
Get-WmiObject -namespace $NAMESPACE -computer $COMPUTER -class WESL_UserSetting | Select Sid, Shell, DefaultAction

# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

## Requirements

| Windows Edition        | Supported |
|:-----------------------|:---------:|
| Windows Home           | No        |
| Windows Pro            | No        |
| Windows Enterprise     | Yes       |
| Windows Education      | Yes       |
| Windows IoT Enterprise | Yes       |

## Related topics

- [Shell Launcher](shell-launcher.md)
