---
title: WESL_UserSetting
description: WESL_UserSetting
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 73c5bb46-bf9e-4657-a5ae-88dbd14b79e8
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
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

### <a href="" id="mth"></a>Methods

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Methods</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="wesl-usersettingsetcustomshell.md" data-raw-source="[WESL_UserSetting.SetCustomShell](wesl-usersettingsetcustomshell.md)">WESL_UserSetting.SetCustomShell</a></p></td>
<td><p>Configures Shell Launcher for a specific user or group, based on SID.</p></td>
</tr>
<tr class="even">
<td><p><a href="wesl-usersettinggetcustomshell.md" data-raw-source="[WESL_UserSetting.GetCustomShell](wesl-usersettinggetcustomshell.md)">WESL_UserSetting.GetCustomShell</a></p></td>
<td><p>Retrieves the Shell Launcher configuration for a specific user or group, based on the SID.</p></td>
</tr>
<tr class="odd">
<td><p><a href="wesl-usersettingremovecustomshell.md" data-raw-source="[WESL_UserSetting.RemoveCustomShell](wesl-usersettingremovecustomshell.md)">WESL_UserSetting.RemoveCustomShell</a></p></td>
<td><p>Removes a Shell Launcher configuration for a specific user or group, based on the SID.</p></td>
</tr>
<tr class="even">
<td><p><a href="wesl-usersettinggetdefaultshell.md" data-raw-source="[WESL_UserSetting.GetDefaultShell](wesl-usersettinggetdefaultshell.md)">WESL_UserSetting.GetDefaultShell</a></p></td>
<td><p>Retrieves the default Shell Launcher configuration.</p></td>
</tr>
<tr class="odd">
<td><p><a href="wesl-usersettingsetdefaultshell.md" data-raw-source="[WESL_UserSetting.SetDefaultShell](wesl-usersettingsetdefaultshell.md)">WESL_UserSetting.SetDefaultShell</a></p></td>
<td><p>Sets the default Shell Launcher configuration.</p></td>
</tr>
<tr class="even">
<td><p><a href="wesl-usersettingisenabled.md" data-raw-source="[WESL_UserSetting.IsEnabled](wesl-usersettingisenabled.md)">WESL_UserSetting.IsEnabled</a></p></td>
<td><p>Retrieves a value that indicates if Shell Launcher is enabled or disabled.</p></td>
</tr>
<tr class="odd">
<td><p><a href="wesl-usersettingsetenabled.md" data-raw-source="[WESL_UserSetting.SetEnabled](wesl-usersettingsetenabled.md)">WESL_UserSetting.SetEnabled</a></p></td>
<td><p>Enables or disables Shell Launcher.</p></td>
</tr>
</tbody>
</table>

### <a href="" id="pro"></a>Properties

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Data type</th>
<th>Qualifiers</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>**Sid**</p></td>
<td><p>string</p></td>
<td><p>[read, write, required]</p></td>
<td><p>User or group SID.</p></td>
</tr>
<tr class="even">
<td><p>**shell**</p></td>
<td><p>string</p></td>
<td><p>[read, write, required]</p></td>
<td><p>The application to start as the shell.</p>
<p>The **shell** property can be a filename in the *Path* environment variable, or it can contain a fully qualified path to the application. You can also use environment variables in the path.</p>
<p>Any spaces in the **shell** property must be part of a quote-delimited string.</p></td>
</tr>
<tr class="odd">
<td><p>**CustomReturnCodes**</p></td>
<td><p>Sint32[]</p></td>
<td><p>[read, write]</p></td>
<td><p>An array of custom return codes that can be returned by the shell.</p></td>
</tr>
<tr class="even">
<td><p>**CustomReturnCodesAction**</p></td>
<td><p>Sint32[]</p></td>
<td><p>[read, write]</p></td>
<td><p>An array of custom return code actions that determine what action Shell Launcher takes when the shell exits. The custom actions map to the array of **CustomReturnCodes**.</p>
<p>The possible actions are defined in the following table:</p>
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>0</p></td>
<td><p>Restart the shell.</p></td>
</tr>
<tr class="even">
<td><p>1</p></td>
<td><p>Restart the device.</p></td>
</tr>
<tr class="odd">
<td><p>2</p></td>
<td><p>Shut down the device.</p></td>
</tr>
<tr class="even">
<td><p>3</p></td>
<td><p>Do nothing.</p></td>
</tr>
</tbody>
</table>
<p> </p></td>
</tr>
<tr class="odd">
<td><p>**DefaultAction**</p></td>
<td><p>Sint32</p></td>
<td><p>[read, write]</p></td>
<td><p>The default action Shell Launcher takes when the shell exits.</p>
<p>The possible actions are defined in the following table:</p>
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>0</p></td>
<td><p>Restart the shell.</p></td>
</tr>
<tr class="even">
<td><p>1</p></td>
<td><p>Restart the device.</p></td>
</tr>
<tr class="odd">
<td><p>2</p></td>
<td><p>Shut down the device.</p></td>
</tr>
<tr class="even">
<td><p>3</p></td>
<td><p>Do nothing.</p></td>
</tr>
</tbody>
</table>
<p> </p></td>
</tr>
</tbody>
</table>

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

| Windows Edition       | Supported |
|:----------------------|:----------|
| Windows 10 Home       | No        |
| Windows 10 Pro        | No        |
| Windows 10 Enterprise | Yes       |
| Windows 10 Education  | Yes       |

## Related topics

[Shell Launcher](shell-launcher.md)