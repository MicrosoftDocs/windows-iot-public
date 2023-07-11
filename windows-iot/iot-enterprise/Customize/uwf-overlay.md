---
title: UWF\_Overlay
description: UWF\_Overlay
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 3f58bd9d-73e8-4684-baa1-690b739dc226


ms.date: 05/02/2017
ms.topic: article


---
# UWF\_Overlay

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
<td><p><a href="uwf-overlaygetoverlayfiles.md" data-raw-source="[UWF_Overlay.GetOverlayFiles](uwf-overlaygetoverlayfiles.md)">UWF_Overlay.GetOverlayFiles</a></p></td>
<td><p>Returns a list of files of a volume that were cached in the UWF overlay.</p></td>
</tr>
<tr class="even">
<td><p><a href="uwf-overlaysetwarningthreshold.md" data-raw-source="[UWF_Overlay.SetWarningThreshold](uwf-overlaysetwarningthreshold.md)">UWF_Overlay.SetWarningThreshold</a></p></td>
<td><p>Sets the warning threshold for monitoring the size of the UWF overlay.</p></td>
</tr>
<tr class="odd">
<td><p><a href="uwf-overlaysetcriticalthreshold.md" data-raw-source="[UWF_Overlay.SetCriticalThreshold](uwf-overlaysetcriticalthreshold.md)">UWF_Overlay.SetCriticalThreshold</a></p></td>
<td><p>Sets the critical warning threshold for monitoring the size of the UWF overlay.</p></td>
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
<td><p><strong>Id</strong></p></td>
<td><p>string</p></td>
<td><p>[key]</p></td>
<td><p>A unique ID. This is always set to <strong>UWF_Overlay</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>OverlayConsumption</strong></p></td>
<td><p>UInt32</p></td>
<td><p>[read]</p></td>
<td><p>The current size, in megabytes, of the UWF overlay.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AvailableSpace</strong></p></td>
<td><p>UInt32</p></td>
<td><p>[read]</p></td>
<td><p>The amount of free space, in megabytes, available to the UWF overlay.</p></td>
</tr>
<tr class="even">
<td><p><strong>CriticalOverlayThreshold</strong></p></td>
<td><p>UInt32</p></td>
<td><p>[read]</p></td>
<td><p>The critical threshold size, in megabytes. UWF sends a critical threshold notification event when the UWF overlay size reaches or exceeds this value.</p></td>
</tr>
<tr class="odd">
<td><p><strong>WarningOverlayThreshold</strong></p></td>
<td><p>UInt32</p></td>
<td><p>[read]</p></td>
<td><p>The warning threshold size, in megabytes. UWF sends a warning threshold notification event when the UWF overlay size reaches or exceeds this value.</p></td>
</tr>
</tbody>
</table>

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

| Windows Edition       | Supported |
|:----------------------|:----------|
| Windows 10 Home       | No        |
| Windows 10 Pro        | No        |
| Windows 10 Enterprise | Yes       |
| Windows 10 Education  | Yes       |

## Related topics

[Unified Write Filter](unified-write-filter.md)
