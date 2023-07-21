---
title: UWF_Filter
description: UWF_Filter
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: efcf470f-29c8-40d3-87b8-db0fdbb57bfe
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# UWF_Filter

Enables or disables Unified Write Filter (UWF), resets configuration settings for UWF, and shuts down or restarts your device.

## Syntax

```powershell
class UWF_Filter{
    [key]  string Id;
    [read] boolean CurrentEnabled;
    [read] boolean NextEnabled;
    UInt32 Enable();
    UInt32 Disable();
    UInt32 ResetSettings();
    UInt32 ShutdownSystem();
    UInt32 RestartSystem();
};
```

## Members

The following tables list any methods and properties that belong to this class.

### Methods

| Methods  | Description |
|----------|-------------|
| [UWF_Filter.Enable](uwf-filterenable.md) | Enables UWF on the next restart. |
| [UWF_Filter.Disable](uwf-filterdisable.md) | Disables UWF on the next restart. |
| [UWF_Filter.ResetSettings](uwf-filterresetsettings.md) | Restores UWF settings to the orig inal state that was captured at install time. |
| [UWF_Filter.ShutdownSystem](uwf-filtershutdownsystem.md) |Safely shuts down a system protected by UWF, even if the overlay is full. |
| [UWF_Filter.RestartSystem](uwf-filterrestartsystem.md) | Safely restarts a system protected by UWF, even if the overlay is full. |

### Properties

| Property | Data&nbsp;type | Qualifiers | Description |
|----------|----------------|------------|-------------|
| **Id**   | string         | [key]      | A unique ID. This is always set to **UWF_Filter** |
| **CurrentEnabled** | Boolean | [read] | Indicates if UWF is enabled for the current session. |
| **NextEnabled** | Boolean | [read] | Indicates if UWF is enabled after the next restart. |

### Remarks

You must use an administrator account to make any changes to the configuration settings for UWF. Users with any kind of account can read the current configuration settings.

## Example

The following example demonstrates how to enable or disable UWF by using the WMI provider in a PowerShell script.

The PowerShell script creates three functions to help enable or disable UWF. It then demonstrates how to use each function.

The first function, `Disable-UWF`, retrieves a WMI object for **UWF_Filter**, and calls the **Disable()** method to disable UWF after the next device restart.

The second function, `Enable-UWF`, retrieves a WMI object for **UWF_Filter**, and calls the **Enable()** method to enable UWF after the next device restart.

The third function, `Display-UWFState`, examines the properties of the **UWF_Filter** object, and prints out the current settings for **UWF_Filter**.

```powershell
$COMPUTER = "localhost"
$NAMESPACE = "root\standardcimv2\embedded"

# Create a function to disable the Unified Write Filter driver after the next restart.
function Disable-UWF() {

# Retrieve the UWF_Filter settings.
    $objUWFInstance = Get-WMIObject -namespace $NAMESPACE -class UWF_Filter;

    if(!$objUWFInstance) {
        "Unable to retrieve Unified Write Filter settings."
        return;
    }

# Call the method to disable UWF after the next restart.  This sets the NextEnabled property to false.

    $retval = $objUWFInstance.Disable();

# Check the return value to verify that the disable is successful
    if ($retval.ReturnValue -eq 0) {
        "Unified Write Filter will be disabled after the next system restart."
    } else {
        "Unknown Error: " + "{0:x0}" -f $retval.ReturnValue
    }
}

# Create a function to enable the Unified Write Filter driver after the next restart.
function Enable-UWF() {

# Retrieve the UWF_Filter settings.
    $objUWFInstance = Get-WMIObject -namespace $NAMESPACE -class UWF_Filter;

    if(!$objUWFInstance) {
        "Unable to retrieve Unified Write Filter settings."
    return;
    }

# Call the method to enable UWF after the next restart.  This sets the NextEnabled property to false.

    $retval = $objUWFInstance.Enable();

# Check the return value to verify that the enable is successful
    if ($retval.ReturnValue -eq 0) {
        "Unified Write Filter will be enabled after the next system restart."
    } else {
        "Unknown Error: " + "{0:x0}" -f $retval.ReturnValue
    }
}

# Create a function to display the current settings of the Unified Write Filter driver.
function Display-UWFState() {

# Retrieve the UWF_Filter object
    $objUWFInstance = Get-WmiObject -Namespace $NAMESPACE -Class UWF_Filter;

    if(!$objUWFInstance) {
        "Unable to retrieve Unified Write Filter settings."
        return;
    }

# Check the CurrentEnabled property to see if UWF is enabled in the current session.
    if($objUWFInstance.CurrentEnabled) {
        $CurrentStatus = "enabled";
    } else {
        $CurrentStatus = "disabled";
    }

# Check the NextEnabled property to see if UWF is enabled or disabled after the next system restart.
    if($objUWFInstance.NextEnabled) {
        $NextStatus = "enabled";
    } else {
        $NextStatus = "disabled";
    }
}

# Some examples of how to call the functions

Display-UWFState

"Enabling Unified Write Filter"
Enable-UWF

Display-UWFState

"Disabling Unified Write Filter"
Disable-UWF

Display-UWFState
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

- [Unified Write Filter WMI provider reference](uwf-wmi-provider-reference.md)
- [Unified Write Filter](unified-write-filter.md)
