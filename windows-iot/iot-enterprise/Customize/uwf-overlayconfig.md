---
title: UWF\_OverlayConfig
description: UWF\_OverlayConfig
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: a1cde09f-08ef-41a6-94a4-808e163a2b69


ms.date: 05/02/2017
ms.topic: article


---
# UWF\_OverlayConfig

Displays and configures global settings for the Unified Write Filter (UWF) overlay. You can modify the maximum size and the type of the UWF overlay.

## Syntax

```powershell
class UWF_OverlayConfig{
    [key, Read] boolean CurrentSession;
    [read] UInt32 Type;
    [read] SInt32 MaximumSize;

    UInt32 SetType(
        UInt32 type
    );
    UInt32 SetMaximumSize(
        UInt32 size
    );
};
```

## Members

The following tables list the methods and properties that belong to this class.

### <a href="" id="mth"></a>Methods

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Method</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="uwf-overlayconfigsetmaximumsize.md" data-raw-source="[UWF_OverlayConfig.SetMaximumSize](uwf-overlayconfigsetmaximumsize.md)">UWF_OverlayConfig.SetMaximumSize</a></p></td>
<td><p>Sets the maximum cache size, in megabytes, of the overlay.</p></td>
</tr>
<tr class="even">
<td><p><a href="uwf-overlayconfigsettype.md" data-raw-source="[UWF_OverlayConfig.SetType](uwf-overlayconfigsettype.md)">UWF_OverlayConfig.SetType</a></p></td>
<td><p>Sets the type of the UWF overlay to either RAM-based or disk-based.</p></td>
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
<td><p><strong>CurrentSessoin</strong></p></td>
<td><p>Boolean</p></td>
<td><p>[key, read]</p></td>
<td><p>Indicates which session the object contains settings for.</p>
<p>Set to <strong>True</strong> for the current session; set to <strong>False</strong> for the next session that begins after a restart.</p></td>
</tr>
<tr class="even">
<td><p><strong>Type</strong></p></td>
<td><p>UInt32</p></td>
<td><p>[read]</p></td>
<td><p>Indicates the type of overlay.</p>
<p>Set to <strong>0</strong> for a RAM-based overlay; set to <strong>1</strong> for a disk-based overlay.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MaximumSize</strong></p></td>
<td><p>SInt32</p></td>
<td><p>[read]</p></td>
<td><p>Indicates the maximum cache size, in megabytes, of the overlay.</p></td>
</tr>
</tbody>
</table>

### Remarks

Changes to the overlay configuration take effect on the next restart in which UWF is enabled.

Before you can change the **Type** or **MaximumSize** properties, UWF must be disabled in the current session.

### Example

The following example demonstrates how to change the maximum size or the storage type of the overlay in UWF by using the Windows Management Instrumentation (WMI) provider in a PowerShell script.

The PowerShell script creates two functions to modify the overlay configuration. It then demonstrates how to use the functions. The first function, **Set-OverlaySize**, sets the maximum size of the overlay. The second function, **Set-OverlayType**, sets the type of the overlay to RAM-based or disk-based.

```powershell
$COMPUTER = "localhost"
$NAMESPACE = "root\standardcimv2\embedded"

# Define common parameters

$CommonParams = @{"namespace"=$NAMESPACE; "computer"=$COMPUTER}

function Set-OverlaySize([UInt32] $size) {

# This function sets the size of the overlay to which file and registry changes are redirected
# Changes take effect after the next restart

# $size is the maximum size in MB of the overlay

# Make sure that UWF is currently disabled

    $UWFFilter = Get-WmiObject -class UWF_Filter @commonParams

    if ($UWFFilter.CurrentEnabled -eq $false) {

# Get the configuration for the next session after a restart

        $nextConfig = Get-WMIObject -class UWF_OverlayConfig -Filter "CurrentSession = false" @CommonParams;

        if ($nextConfig) {

# Set the maximum size of the overlay

        $nextConfig.SetMaximumSize($size);
            write-host "Set overlay max size to $size MB."
        }
    } else {
        write-host "UWF must be disabled in the current session before you can change the overlay size."
    }
}

function Set-OverlayType([UInt32] $overlayType) {

# This function sets the type of the overlay to which file and registry changes are redirected
# Changes take effect after the next restart

# $overlayType is the type of storage that UWF uses to maintain the overlay. 0 = RAM-based; 1 = disk-based.

    $overlayTypeText = @("RAM-based", "disk-based")

# Make sure that the overlay type is a valid value

    if ($overlayType -eq 0 -or $overlayType -eq 1) {

# Make sure that UWF is currently disabled

        $UWFFilter = Get-WmiObject -class UWF_Filter @commonParams

        if ($UWFFilter.CurrentEnabled -eq $false) {

# Get the configuration for the next session after a restart

            $nextConfig = Get-WMIObject -class UWF_OverlayConfig -Filter "CurrentSession = false" @CommonParams;

            if ($nextConfig) {

# Set the type of the overlay

        $nextConfig.SetType($overlayType);
                write-host "Set overlay type to $overlayTypeText[$overlayType]."
            }
        } else {
            write-host "UWF must be disabled in the current session before you can change the overlay type."
        }
    } else {
        write-host "Invalid value for overlay type.  Valid values are 0 (RAM-based) or 1 (disk-based)."
    }
}

# The following sample commands demonstrate how to use the functions to change the overlay configuration

$RAMMode = 0
$DiskMode = 1

Set-OverlaySize 2048

Set-OverlayType $DiskMode
```

## Requirements

| Windows Edition       | Supported |
|:----------------------|:----------|
| Windows 10 Home       | No        |
| Windows 10 Pro        | No        |
| Windows 10 Enterprise | Yes       |
| Windows 10 Education  | Yes       |

## Related topics

[Unified Write Filter WMI provider reference](uwf-wmi-provider-reference.md)

[Unified Write Filter](unified-write-filter.md)
