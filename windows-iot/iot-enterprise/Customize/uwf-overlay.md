---
title: UWF_Overlay
description: UWF_Overlay
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 3f58bd9d-73e8-4684-baa1-690b739dc226
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
ms.date: 05/20/2024
ms.topic: article


---
# UWF_Overlay

Contains the current size of the Unified Write Filter (UWF) overlay and manages the critical and warning thresholds for the overlay size.

## Syntax

```powershell
class UWF_Overlay {
    [key]  string Id;
    [read] UInt32 OverlayConsumption;
    [read] UInt32 AvailableSpace;
    [read] UInt32 CriticalOverlayThreshold;
    [read] UInt32 WarningOverlayThreshold;

    UInt32 GetOverlayFiles(
        [in] string Volume,
        [out, EmbeddedInstance("UWF_OverlayFile")] string OverlayFiles[]
    );
    UInt32 SetWarningThreshold(
        UInt32 size
    );
    UInt32 SetCriticalThreshold(
        UInt32 size
    );
};
```

## Members

The following tables list any methods and properties that belong to this class.

| Methods | Description |
|---------|-------------|
| [UWF_Overlay.GetOverlayFiles](uwf-overlaygetoverlayfiles.md) | Returns a list of files of a volume that were cached in the UWF overlay. |
| [UWF_Overlay.SetWarningThreshold](uwf-overlaysetwarningthreshold.md) | Sets the warning threshold for monitoring the size of the UWF overlay. |
| [UWF_Overlay.SetCriticalThreshold](uwf-overlaysetcriticalthreshold.md) | Sets the critical warning threshold for monitoring the size of the UWF overlay. |

### Properties

| Property | Data&nbsp;type | Qualifiers | Description |
|----------|----------------|------------|-------------|
| Id       | string         | [key]      | A unique ID. This is always set to **UWF_Overlay**. |
| OverlayConsumption | UInt32 | [read] | The current size, in megabytes, of the UWF overlay. |
| AvailableSpace | UInt32 | [read] | The amount of free space, in megabytes, available to the UWF overlay. |
| CriticalOverlayThreshold | UInt32 | [read] | The critical threshold size, in megabytes. UWF sends a critical threshold notification event when the UWF overlay size reaches or exceeds this value. |
| WarningOverlayThreshold | UInt32 | [read] | The warning threshold size, in megabytes. UWF sends a warning threshold notification event when the UWF overlay size reaches or exceeds this value. |

### Examples

The following example demonstrates how to use the UWF overlay by using the WMI provider in a PowerShell script.

```powershell
$COMPUTER = "localhost"
$NAMESPACE = "root\standardcimv2\embedded"

# Function to set the Unified Write Filter overlay warning threshold

function Set-OverlayWarningThreshold($ThresholdSize) {

# Retrieve the overlay WMI object

    $OverlayInstance = Get-WMIObject -namespace $NAMESPACE -class UWF_Overlay;

    if(!$OverlayInstance) {
        "Unable to get handle to an instance of the UWF_Overlay class"
        return;
    }

# Call the instance method to set the warning threshold value

    $retval = $OverlayInstance.SetWarningThreshold($ThresholdSize);

# Check the return value to verify that setting the warning threshold is successful

    if ($retval.ReturnValue -eq 0) {
        "Overlay warning threshold has been set to " + $ThresholdSize + " MB"
    } else {
        "Unknown Error: " + "{0:x0}" -f $retval.ReturnValue
    }
}

# Function to set the Unified Write Filter overlay critical threshold

function Set-OverlayCriticalThreshold($ThresholdSize) {

# Retrieve the overlay WMI object

    $OverlayInstance = Get-WMIObject -namespace $NAMESPACE -class UWF_Overlay;

    if(!$OverlayInstance) {
        "Unable to get handle to an instance of the UWF_Overlay class"
        return;
    }

# Call the instance method to set the warning threshold value

    $retval = $OverlayInstance.SetCriticalThreshold($ThresholdSize);

# Check the return value to verify that setting the critical threshold is successful

    if ($retval.ReturnValue -eq 0) {
        "Overlay critical threshold has been set to " + $ThresholdSize + " MB"
    } else {
        "Unknown Error: " + "{0:x0}" -f $retval.ReturnValue
    }
}

# Function to print the current overlay information

function Get-OverlayInformation() {

# Retrieve the Overlay WMI object

    $OverlayInstance = Get-WMIObject -namespace $NAMESPACE -class UWF_Overlay;

    if(!$OverlayInstance) {
        "Unable to get handle to an instance of the UWF_Overlay class"
        return;
    }

# Display the current values of the overlay properties

    "`nOverlay Consumption: " + $OverlayInstance.OverlayConsumption
    "Available Space: " + $OverlayInstance.AvailableSpace
    "Critical Overlay Threshold: " + $OverlayInstance.CriticalOverlayThreshold
    "Warning Overlay Threshold: " + $OverlayInstance.WarningOverlayThreshold
}

# Examples of using these functions

"`nSetting the warning threshold to 768 MB."
Set-OverlayWarningThreshold( 768 )

"`nSetting the critical threshold to 896 MB."
Set-OverlayCriticalThreshold( 896 )

"`nDisplaying the current state of the overlay."
Get-OverlayInformation
```

### Remarks

Only one **UFW\_Overlay** instance exists for a system protected with UWF.

## Requirements

| Windows Edition        | Supported |
|:-----------------------|:---------:|
| Windows Home           | No        |
| Windows Pro            | No        |
| Windows Enterprise     | Yes       |
| Windows Education      | Yes       |
| Windows IoT Enterprise | Yes       |

## Related topics

- [Unified Write Filter](unified-write-filter.md)
