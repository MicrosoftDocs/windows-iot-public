---
title: Remove key combination configurations
description: Remove key combination configurations
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 14f61d51-834b-4d15-8024-6728f0c8bc9c


ms.date: 05/02/2017
ms.topic: article


---
# Remove key combination configurations

The following sample Windows PowerShell script uses the Windows Management Instrumentation (WMI) providers for Keyboard Filter to create two functions to remove custom-defined key combination configurations from Keyboard Filter. It demonstrates several ways to use each function.

The first function, **Remove-Custom-Key**, removes custom key combination configurations.

The second function, **Remove-Scancode**, removes custom scan code configurations.

You cannot remove the predefined key combination configurations for Keyboard Filter, but you can disable them.

## Remove-rules.ps1

```powershell
#
# Copyright (C) Microsoft. All rights reserved.
#

<#
.Synopsis
    This script shows how to use the build in WMI providers to remove keyboard filter rules.  Rules of type WEKF_PredefinedKey cannot be removed.
.Parameter ComputerName
    Optional parameter to specify the remote computer that this script should
    manage.  If not specified, the script will execute all WMI operations
    locally.
#>

param(
    [string] $ComputerName
)

$CommonParams = @{"namespace"="root\standardcimv2\embedded"}
$CommonParams += $PSBoundParameters

function Remove-Custom-Key($Id) {
    <#
    .Synopsis
        Remove an instance of WEKF_CustomKey
    .Description
        Enumerate all instances of WEKF_CustomKey.  When an instance has an
        Id that matches $Id, delete it.
    .Example
        Remove-Custom-Key "Ctrl+V"

        This removes the instance of WEKF_CustomKey with a key Id of "Ctrl+V"
#>

    $customInstance = Get-WMIObject -class WEKF_CustomKey @CommonParams |
        where {$_.Id -eq $Id}

    if ($customInstance) {
        $customInstance.Delete();
        "Removed Custom Filter $Id.";
    } else {
        "Custom Filter $Id does not exist.";
    }
}

function Remove-Scancode($Modifiers, [int]$Code) {
    <#
    .Synopsis
        Remove and instance of WEKF_Scancode
    .Description
        Enumerate all instances of WEKF_Scancode.  When an instance has a
        matching modifiers and code, delete it.
    .Example
        Remove-Scancode "Ctrl" 37

        This removes the instance of WEKF_Scancode with Modifiers="Ctrl" and
        Scancode=37.
#>

    $scancodeInstance = Get-WMIObject -class WEKF_Scancode @CommonParams |
        where {($_.Modifiers -eq $Modifiers) -and ($_.Scancode -eq $Code)}

    if ($scancodeInstance) {
        $scancodeInstance.Delete();
        "Removed Scancode $Modifiers+$Code.";
    } else {
        "Scancode $Modifiers+$Code does not exist.";
    }
}

# Some example uses of the functions defined above.
Remove-Custom-Key "Ctrl+V"
Remove-Custom-Key "Numpad0"
Remove-Custom-Key "Shift+Numpad1"
Remove-Custom-Key "%"
Remove-Scancode "Ctrl" 37
```

## Related topics

[Windows PowerShell script samples for keyboard filter](keyboardfilter-powershell-script-samples.md)

[Keyboard filter WMI provider reference](keyboardfilter-wmi-provider-reference.md)

[Keyboard filter](keyboardfilter.md)
