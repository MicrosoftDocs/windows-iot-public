---
title: UWF_Servicing
description: UWF_Servicing
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: a6eec8a2-1360-413d-af83-ffc63f47c08c
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
ms.date: 05/20/2024
ms.topic: article


---
# UWF_Servicing

This class contains properties and methods that enable you to query and control Unified Write Filter (UWF) servicing mode.

## Syntax

```powershell
class UWF_Servicing {
    [key, read] boolean CurrentSession;
    [read] boolean ServicingEnabled;

    UInt32 Enable();
    UInt32 Disable();
    UInt32 UpdateWindows(
        [out] UInt32 UpdateStatus
    );
};
```

## Members

The following tables list the methods and properties that belong to this class.

### Methods

| Method | Description&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |
|--------|-------------|
|[UWF_Servicing.Disable](uwf-servicingdisable.md) | Disables Unified Write Filter (UWF) servicing mode.</br>The system leaves servicing mode in the next session that follows a restart. |
| [UWF_Servicing.Enable](uwf-servicingenable.md) | Enables Unified Write Filter (UWF) servicing mode.</br>The system enters servicing mode in the next session that follows a restart. |
| [UWF_Servicing.UpdateWindows](uwf-servicingupdatewindows.md) | Calls Windows Update to download and install critical and security updates for your device running Windows 10 Enterprise. |

### Properties

| Property | Data&nbsp;type | Qualifiers | Description&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;& |
|----------|----------------|------------|-------------|
| CurrentSession | Boolean | [key, read] | Indicates when to enable servicing.</br>- **True** if servicing is enabled in the current session</br>- **False** if servicing will be enabled in the session that follows a restart. |
| ServiceEnabled | Boolean | [read] | Indicates if the system is in servicing mode in the current session, or will be in servicing mode in the next session that follows a restart.</br>- **True** if servicing is enabled</br>- otherwise, **False**. |

### Remarks

This class only has two instances, one for the current session, and another for the next session that follows a restart.

### Example

The following example shows how to enable and disable UWF servicing mode on a device by using the Windows Management Instrumentation (WMI) provider in a PowerShell script.

```powershell
$COMPUTER = "localhost"
$NAMESPACE = "root\standardcimv2\embedded"

# Define common parameters

$CommonParams = @{"namespace"=$NAMESPACE; "computer"=$COMPUTER}

# Enable UWF servicing

$nextSession = Get-WmiObject -class UWF_Servicing @CommonParams | where {
    $_.CurrentSession -eq $false
}

if ($nextSession) {

    $nextSession.Enable() | Out-Null;
    Write-Host "This device is enabled for servicing mode after the next restart."
}

# Disable UWF servicing

$nextSession = Get-WmiObject -class UWF_Servicing @CommonParams | where {
    $_.CurrentSession -eq $false
}

if ($nextSession) {

    $nextSession.Disable() | Out-Null;
    Write-Host "Servicing mode is now disabled for this device."
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

## Related topics

- [Unified Write Filter](unified-write-filter.md)
