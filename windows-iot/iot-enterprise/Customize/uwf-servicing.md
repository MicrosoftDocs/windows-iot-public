---
title: UWF\_Servicing
description: UWF\_Servicing
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: a6eec8a2-1360-413d-af83-ffc63f47c08c


ms.date: 05/02/2017
ms.topic: article


---
# UWF\_Servicing

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
<td><p><a href="uwf-servicingdisable.md" data-raw-source="[UWF_Servicing.Disable](uwf-servicingdisable.md)">UWF_Servicing.Disable</a></p></td>
<td><p>Disables Unified Write Filter (UWF) servicing mode.</p>
<p>The system leaves servicing mode in the next session that follows a restart.</p></td>
</tr>
<tr class="even">
<td><p><a href="uwf-servicingenable.md" data-raw-source="[UWF_Servicing.Enable](uwf-servicingenable.md)">UWF_Servicing.Enable</a></p></td>
<td><p>Enables Unified Write Filter (UWF) servicing mode.</p>
<p>The system enters servicing mode in the next session that follows a restart.</p></td>
</tr>
<tr class="odd">
<td><p><a href="uwf-servicingupdatewindows.md" data-raw-source="[UWF_Servicing.UpdateWindows](uwf-servicingupdatewindows.md)">UWF_Servicing.UpdateWindows</a></p></td>
<td><p>Calls Windows Update to download and install critical and security updates for your device running Windows 10 Enterprise.</p></td>
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
<td><p><strong>CurrentSession</strong></p></td>
<td><p>Boolean</p></td>
<td><p>[key, read]</p></td>
<td><p>Indicates when to enable servicing.</p>
<p><strong>True</strong> if servicing is enabled in the current session; <strong>False</strong> if servicing will be enabled in the session that follows a restart.</p></td>
</tr>
<tr class="even">
<td><p><strong>ServiceEnabled</strong></p></td>
<td><p>Boolean</p></td>
<td><p>[read]</p></td>
<td><p>Indicates if the system is in servicing mode in the current session, or will be in servicing mode in the next session that follows a restart.</p>
<p><strong>True</strong> if servicing is enabled; otherwise, <strong>False</strong>.</p></td>
</tr>
</tbody>
</table>

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

| Windows Edition       | Supported |
|:----------------------|:----------|
| Windows 10 Home       | No        |
| Windows 10 Pro        | No        |
| Windows 10 Enterprise | Yes       |
| Windows 10 Education  | Yes       |

## Related topics

[Unified Write Filter](unified-write-filter.md)
