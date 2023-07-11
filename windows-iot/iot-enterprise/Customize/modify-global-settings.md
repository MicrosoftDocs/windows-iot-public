---
title: Modify global settings
description: Modify global settings
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: b1388f15-e3a4-4513-8721-8ba3ce19747a


ms.date: 05/02/2017
ms.topic: article


---
# Modify global settings

The following sample Windows PowerShell scripts use the Windows Management Instrumentation (WMI) providers to modify global settings for Keyboard Filter.

The function **Get-Setting** retrieves the value of a global setting for Keyboard Filter.

In the first script, the function **Set-DisableKeyboardFilterForAdministrators** modifies the value of the **DisableKeyboardFilterForAdministrators** setting.

In the second script, the function **Set-ForceOffAccessibility** modifies the value of the **ForceOffAccessibility** setting.

## Set-DisableKeyboardFilterForAdministrators.ps1

```powershell
#
# Copyright (C) Microsoft. All rights reserved.
#

<#
.Synopsis
    This script shows how to enumerate WEKF_Settings to find global settings
    that can be set on the keyboard filter.  In this specific script, the
    global setting to be set is "DisableKeyboardFilterForAdministrators".
.Parameter ComputerName
    Optional parameter to specify a remote computer that this script should
    manage.  If not specified, the script will execute all WMI operations
    locally.
.Parameter On
    Switch if present that sets "DisableKeyboardFilterForAdministrators" to
    true.  If not present, sets the setting to false.
#>

param (
    [Switch] $On = $False,
    [String] $ComputerName
)

$CommonParams = @{"namespace"="root\standardcimv2\embedded"};
if ($PSBoundParameters.ContainsKey("ComputerName")) {
    $CommonParams += @{"ComputerName" = $ComputerName};
}

function Get-Setting([String] $Name) {
    <#
    .Synopsis
        Get a WMIObject by name from WEKF_Settings
    .Parameter Name
        The name of the setting, which is the key for the WEKF_Settings class.
#>
    $Entry = Get-WMIObject -class WEKF_Settings @CommonParams |
        where {
            $_.Name -eq $Name
        }

    return $Entry
}

function Set-DisableKeyboardFilterForAdministrators([Bool] $Value) {
    <#
    .Synopsis
        Set the DisableKeyboardFilterForAdministrators setting to true or
        false.
    .Description
        Set DisableKeyboardFilterForAdministrators to true or false based
        on $Value
    .Parameter Value
        A Boolean value
#>

    $Setting = Get-Setting("DisableKeyboardFilterForAdministrators")
    if ($Setting) {
        if ($Value) {
            $Setting.Value = "true" 
        } else {
            $Setting.Value = "false"
        }
        $Setting.Put() | Out-Null;
    } else {
        Write-Error "Unable to find DisableKeyboardFilterForAdministrators setting";
    }
}

Set-DisableKeyboardFilterForAdministrators $On
```

## Set-ForceOffAccessibility.ps1

```powershell
#
# Copyright (C) Microsoft. All rights reserved.
#

<#
.Synopsis
    This script shows how to enumerate WEKF_Settings to find global settings
    that can be set on the keyboard filter.  In this specific script, the
    global setting to be set is "ForceOffAccessibility".
.Parameter ComputerName
    Optional parameter to specify a remote computer that this script should
    manage.  If not specified, the script will execute all WMI operations
    locally.
.Parameter Enabled
    Switch if present that sets "ForceOffAccessibility" to true.  If not
    present, sets the setting to false.
#>

param (
    [Switch] $Enabled = $False,
    [String] $ComputerName
)

$CommonParams = @{"namespace"="root\standardcimv2\embedded"};
if ($PSBoundParameters.ContainsKey("ComputerName")) {
    $CommonParams += @{"ComputerName" = $ComputerName};
}

function Get-Setting([String] $Name) {
    <#
    .Synopsis
        Get a WMIObject by name from WEKF_Settings
    .Parameter Name
        The name of the setting, which is the key for the WEKF_Settings class.
#>
    $Entry = Get-WMIObject -class WEKF_Settings @CommonParams |
        where {
            $_.Name -eq $Name
        }

    return $Entry
}

function Set-ForceOffAccessibility([Bool] $Value) {
    <#
    .Synopsis
        Set the ForceOffAccessibility setting to true or false.
    .Description
        Set ForceOffAccessibility to true or false based on $Value
    .Parameter Value
        A Boolean value
#>

    $Setting = Get-Setting("ForceOffAccessibility")
    if ($Setting) {
        if ($Value) {
            $Setting.Value = "true" 
        } else {
            $Setting.Value = "false"
        }
        $Setting.Put() | Out-Null;
    } else {
        Write-Error "Unable to find ForceOffAccessibility setting";
    }
}

Set-ForceOffAccessibility $Enabled
```

## Related topics

[Windows PowerShell script samples for keyboard filter](keyboardfilter-powershell-script-samples.md)

[WEKF\_Settings](wekf-settings.md)

[Keyboard filter](keyboardfilter.md)
