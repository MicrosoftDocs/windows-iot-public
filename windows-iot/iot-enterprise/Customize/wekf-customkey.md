---
title: WEKF_CustomKey
description: WEKF_CustomKey
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 7d67c0ce-844c-4534-96d4-2c7f21a69c8e
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# WEKF_CustomKey

Adds or removes custom-defined key combinations.

## Syntax

```powershell
class WEKF_CustomKey {
    [Static] uint32 Add(
        [In] string CustomKey
    );
    [Static] uint32 Remove(
        [In] string CustomKey
    );

    [Key] string Id;
    [Read, Write] boolean Enabled;
};
```

## Members

The following tables list any methods and properties that belong to this class.

### Methods

| Methods | Description |
|---------|-------------|
| [WEKF_CustomKey.Add](wekf-customkeyadd.md) | Creates a new custom key combination and enables Keyboard Filter to block the new key combination. |
| [WEKF_CustomKey.Remove](wekf-customkeyremove.md) | Removes the specified custom key combination. Keyboard Filter stops blocking the key combination that was removed. |

### Properties

| Property | Data&nbsp;type | Qualifiers | Description  |
|----------|----------------|------------|--------------|
| **Id** | string | [key] | The name of the custom key combination. |
| **Enabled** | Boolean | [read, write] | Indicates if the key is blocked or unblocked. This property can be one of the following values </br>- **true**  Indicates that the key is blocked.</br>- **false** Indicates that the key is not blocked. |

### Remarks

You can specify key combinations by including the modifier keys in the name. The most common modifier names are “Ctrl”, “Shift”, “Alt”, and “Win”. You cannot block a combination of non-modifier keys. For example, you can block a key combination of “Ctrl+Shift+F”, but you cannot block a key combination of “A+D”.

When you block a shift-modified key, you must enter the key as “Shift” + the unmodified key. For example, to block the % key on an English keyboard layout, you must specify the key as “Shift+5”. Attempting to block “%”, results in Keyboard Filter blocking “5” instead.

When you specify the key combination to block, you must use the English names for the keys. For a list of the key names you can specify, see Keyboard Filter key names.

## Example

The following code demonstrates how to add or enable a custom key combination that Keyboard Filter will block by using the Windows Management Instrumentation (WMI) providers for Keyboard Filter. This example modifies the properties directly and does not call any of the methods defined in **WEKF_CustomKey**.

```powershell
<#
.Synopsis
    This script shows how to use the WMI provider to enable and add 
    Keyboard Filter rules through Windows PowerShell on the local computer.
.Parameter ComputerName
    Optional parameter to specify a remote machine that this script should
    manage.  If not specified, the script will execute all WMI operations
    locally.
#>
param (
    [String] $ComputerName
)

$CommonParams = @{"namespace"="root\standardcimv2\embedded"}
$CommonParams += $PSBoundParameters

function Enable-Custom-Key($Id) {
    <#
    .Synopsis
        Toggle on a Custom Key Keyboard Filter Rule
    .Description
        Use Get-WMIObject to enumerate all WEKF_CustomKey instances,
        filter against key value "Id", and set that instance's "Enabled"
        property to 1/true.

        In the case that the Custom instance does not exist, add a new
        instance of WEKF_CustomKey using Set-WMIInstance.
    .Example
        Enable-Custom-Key "Ctrl+V"

        Enable filtering of the Ctrl + V sequence.
#>

    $custom = Get-WMIObject -class WEKF_CustomKey @CommonParams |
        where {
            $_.Id -eq "$Id"
        };

    if ($custom) {
# Rule exists.  Just enable it.
        $custom.Enabled = 1;
        $custom.Put() | Out-Null;
        "Enabled Custom Filter $Id.";

    } else {
        Set-WMIInstance `
            -class WEKF_CustomKey `
            -argument @{Id="$Id"} `
            @CommonParams | Out-Null

        "Added Custom Filter $Id.";
    }
}


# Some example uses of the function defined above.

Enable-Custom-Key "Ctrl+V"
Enable-Custom-Key "Numpad0"
Enable-Custom-Key "Shift+Numpad1"
```

## Requirements

| Windows Edition        | Supported |
|:-----------------------|:---------:|
| Windows Home           | No        |
| Windows Pro            | No        |
| Windows Enterprise     | Yes       |
| Windows Education      | Yes       |
| Windows IoT Enterprise | Yea       |

## Related topics

[Keyboard Filter WMI provider reference](keyboardfilter-wmi-provider-reference.md)

[Keyboard Filter key names](keyboardfilter-key-names.md)
