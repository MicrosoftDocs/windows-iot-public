---
title: WEDL\_AssignedAccess
description: WEDL\_AssignedAccess
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 2be8d294-db13-4494-bd5f-ba97ed89528e
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
ms.date: 05/20/2024
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

### Methods

This class contains no methods.

### Properties

| Property | Data&nbsp;type | Qualifiers | Description |
|----------|----------------|------------|-------------|
| **UserSID** | string | [key] | The security identifier (SID) for the user account that you want to use as the assigned access account. |
| **AppUserModelId** | string | [read, write] | The Application User Model ID (AUMID) of the Windows app to launch for the assigned access account. |
| **Status** | Boolean | none | Indicates the current status of the assigned access configuration |

| Value | Description |
|:-----:|-------------|
| 0 | A valid account is configured, but no Windows app is specified. Assigned access is not enabled. |
| 1 | Assigned access is enabled. |
| 0x100 | UserSID error: cannot find the account. |
| 0x103 | UserSID error: the account profile does not exist. |
| 0x200 | AppUserModelID error: cannot find the Windows app. |
| 0x201 | Task Scheduler error: Could not schedule task. Make sure that the Task Scheduler service is running. |
| 0xffffffff | Unspecified error.|

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

| Windows Edition        | Supported |
|:-----------------------|:---------:|
| Windows Home           | No        |
| Windows Pro            | No        |
| Windows Enterprise     | Yes       |
| Windows Education      | Yes       |
| Windows IoT Enterprise | Yes       |
