---
title: UWF\_Servicing.UpdateWindows
description: UWF\_Servicing.UpdateWindows
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 578ee0ac-fcc9-4021-9967-7b3f20eaadee
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# UWF\_Servicing.UpdateWindows

Calls Windows Update to download and install critical and security updates for your device running Windows 10 Enterprise.

## Syntax

```powershell
UInt32 UpdateWindows(
    [out] UInt32 UpdateStatus
);
```

## Parameters

<a href="" id="updatestatus"></a>*UpdateStatus*
\[out\] An integer that contains the status of the Windows Update operation, according to the following table:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>UpdateStatus</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>0</p></td>
<td><p>Success.</p></td>
</tr>
<tr class="even">
<td><p>3010</p></td>
<td><p>Restart required.</p></td>
</tr>
<tr class="odd">
<td><p>Any other value.</p></td>
<td><p>Generic error.</p></td>
</tr>
</tbody>
</table>

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

This method is meant to be used as part of a servicing script. For more information, see [Service UWF-protected devices](service-uwf-protected-devices.md).

This method does not disable or enable Unified Write Filter (UWF). If you call this method while UWF is enabled, updates may be lost when the device restarts.

## Requirements

| Windows Edition       | Supported |
|:----------------------|:----------|
| Windows 10 Home       | No        |
| Windows 10 Pro        | No        |
| Windows 10 Enterprise | Yes       |
| Windows 10 Education  | Yes       |

## Related topics

[UWF\_Servicing](uwf-servicing.md)

[Unified Write Filter](unified-write-filter.md)