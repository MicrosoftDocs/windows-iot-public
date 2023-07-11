---
title: WEDL\_AssignedAccess
description: WEDL\_AssignedAccess
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 2be8d294-db13-4494-bd5f-ba97ed89528e


ms.date: 05/02/2017
ms.topic: article


---
# WEDL\_AssignedAccess

This Windows Management Instrumentation (WMI) provider class configures settings for assigned access.

## Syntax

```powershell
class WEDL_AssignedAccess {
    [Key] string UserSID;
    [Read, Write] string AppUserModelId;
    [Read] sint32 Status;
};
```

## Members

The following tables list any methods and properties that belong to this class.

### <a href="" id="mth"></a>Methods

This class contains no methods.

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
<td><p><strong>UserSID</strong></p></td>
<td><p>string</p></td>
<td><p>[key]</p></td>
<td><p>The security identifier (SID) for the user account that you want to use as the assigned access account.</p></td>
</tr>
<tr class="even">
<td><p><strong>AppUserModelId</strong></p></td>
<td><p>string</p></td>
<td><p>[read, write]</p></td>
<td><p>The Application User Model ID (AUMID) of the Windows app to launch for the assigned access account.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Status</strong></p></td>
<td><p>Boolean</p></td>
<td><p>none</p></td>
<td><p>Indicates the current status of the assigned access configuration:</p>
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
<td><p>A valid account is configured, but no Windows app is specified. Assigned access is not enabled.</p></td>
</tr>
<tr class="even">
<td><p>1</p></td>
<td><p>Assigned access is enabled.</p></td>
</tr>
<tr class="odd">
<td><p>0x100</p></td>
<td><p>UserSID error: cannot find the account.</p></td>
</tr>
<tr class="even">
<td><p>0x103</p></td>
<td><p>UserSID error: the account profile does not exist.</p></td>
</tr>
<tr class="odd">
<td><p>0x200</p></td>
<td><p>AppUserModelID error: cannot find the Windows app.</p></td>
</tr>
<tr class="even">
<td><p>0x201</p></td>
<td><p>Task Scheduler error: Could not schedule task. Make sure that the Task Scheduler service is running.</p></td>
</tr>
<tr class="odd">
<td><p>0xffffffff</p></td>
<td><p>Unspecified error.</p></td>
</tr>
</tbody>
</table>
<p> </p></td>
</tr>
</tbody>
</table>

### Remarks

Changes to assigned access do not affect any sessions that are currently signed in; you must sign out and sign back in.

## Example

The following Windows PowerShell script demonstrates how to use this class to set up an assigned access account.

```powershell
#
#---Define variables---
#

$COMPUTER = "localhost"
$NAMESPACE = "root\standardcimv2\embedded"

# Define the assigned access account. 
# To use a different account, change $AssignedAccessAccount to a user account that is present on your device.

$AssignedAccessAccount = "KioskAccount"

# Define the Windows app to launch, in this example, use the Application Model User ID (AUMID) for Windows Calculator.
# To use a different Windows app, change $AppAUMID to the AUMID of the Windows app to launch.
# The Windows app must be installed for the account.

$AppAUMID = "Microsoft.WindowsCalculator_8wekyb3d8bbwe!App"

#
#---Define helper functions---
#

function Get-UsernameSID($AccountName) {

# This function retrieves the SID for a user account on a machine.
# This function does not check to verify that the user account actually exists.

    $NTUserObject = New-Object System.Security.Principal.NTAccount($AccountName)
    $NTUserSID = $NTUserObject.Translate([System.Security.Principal.SecurityIdentifier])

    return $NTUserSID.Value
}

#
#---Set up the new assigned access account---
#

# Get the SID for the assigned access account.

$AssignedAccessUserSID = Get-UsernameSID($AssignedAccessAccount)

# Check to see if an assigned access account is already set up, and if so, clear it.

$AssignedAccessConfig = get-WMIObject -namespace $NAMESPACE -computer $COMPUTER -class WEDL_AssignedAccess

if ($AssignedAccessConfig) {

# Configuration already exists.  Delete it so that we can create a new one, since only one assigned access account can be set up at a time.

    $AssignedAccessConfig.delete();

}

# Configure assigned access to launch the specified Windows app for the specified account.

Set-WmiInstance -class WEDL_AssignedAccess -ComputerName $COMPUTER -Namespace $NAMESPACE -Arguments @{
        UserSID = $AssignedAccessUserSID;
        AppUserModelId = $AppAUMID
        } | Out-Null;

# Confirm that the settings were created properly.

$AssignedAccessConfig = get-WMIObject -namespace $NAMESPACE -computer $COMPUTER -class WEDL_AssignedAccess

if ($AssignedAccessConfig) {

    "Set up assigned access for the " + $AssignedAccessAccount + " account."
    "  UserSID = " + $AssignedAccessConfig.UserSid
    "  AppModelId = " + $AssignedAccessConfig.AppUserModelId

} else {

    "Could not set up assigned access account."
}
```

## Requirements

| Windows Edition       | Supported |
|:----------------------|:----------|
| Windows 10 Home       | No        |
| Windows 10 Pro        | Yes       |
| Windows 10 Enterprise | Yes       |
| Windows 10 Education  | Yes       |


