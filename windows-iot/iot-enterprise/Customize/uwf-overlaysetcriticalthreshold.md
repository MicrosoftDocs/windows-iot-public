---
title: UWF\_Overlay.SetCriticalThreshold
description: UWF\_Overlay.SetCriticalThreshold
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 970dd0a5-ce9c-40d1-b6f5-772c9992f62a
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# UWF\_Overlay.SetCriticalThreshold

Sets the critical threshold for monitoring the size of the Unified Write Filter (UWF) overlay.

## Syntax

```powershell
UInt32 SetCriticalThreshold(
    UInt32 size
);
```

## Parameters

<a href="" id="size"></a>*size*
An integer that represents the size, in megabytes, of the critical threshold level for the overlay. If *size* is 0 (zero), UWF does not raise critical threshold events.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

When the size of the overlay reaches or exceeds the *size* threshold value, UWF writes the following notification event to the event log.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Message ID</th>
<th>Event code</th>
<th>Message text</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>UWF_OVERLAY_REACHED_CRITICAL_LEVEL</p></td>
<td><p>0x80010002L</p></td>
<td><p>The UWF overlay size has reached CRITICAL level.</p></td>
</tr>
</tbody>
</table>

The critical threshold must be higher than the warning threshold.

## Requirements

| Windows Edition       | Supported |
|:----------------------|:----------|
| Windows 10 Home       | No        |
| Windows 10 Pro        | No        |
| Windows 10 Enterprise | Yes       |
| Windows 10 Education  | Yes       |

## Related topics

[UWF\_Overlay](uwf-overlay.md)

[Unified Write Filter](unified-write-filter.md)