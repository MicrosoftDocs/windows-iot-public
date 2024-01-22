---
title: UWF_OverlayConfig
description: UWF_OverlayConfig
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: a1cde09f-08ef-41a6-94a4-808e163a2b69
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
ms.date: 05/02/2017
ms.topic: article


---
# UWF_OverlayConfig

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

### Methods

| Method | Description |
|--------|-------------|
| [UWF_OverlayConfig.SetMaximumSize](uwf-overlayconfigsetmaximumsize.md) | Sets the maximum cache size, in megabytes, of the overlay. |
| [UWF_OverlayConfig.SetType](uwf-overlayconfigsettype.md) | Sets the type of the UWF overlay to either RAM-based or disk-based. |

### Properties

| Property | Data&nbsp;type | Qualifiers | Description |
|----------|----------------|------------|-------------|
| CurrentSession | Boolean | [key, read] | Indicates which session the object contains settings for. </br>- **True** for the current session </br>- **False** for the next session that begins after a restart. |
| Type | UInt32 | [read] | Indicates the type of overlay. </br>- **0** for a RAM-based overlay</br>- **1** for a disk-based overlay. |
| MaximumSize | SInt32 | [read] | Indicates the maximum cache size, in megabytes, of the overlay. |

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

| Windows Edition        | Supported |
|:-----------------------|:---------:|
| Windows Home           | No        |
| Windows Pro            | No        |
| Windows Enterprise     | Yes       |
| Windows Education      | Yes       |
| Windows IoT Enterprise | Yea       |

## Related topics

[Unified Write Filter WMI provider reference](uwf-wmi-provider-reference.md)

[Unified Write Filter](unified-write-filter.md)
