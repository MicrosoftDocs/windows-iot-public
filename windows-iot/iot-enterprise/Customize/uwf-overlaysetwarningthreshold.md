---
title: UWF\_Overlay.SetWarningThreshold
description: UWF\_Overlay.SetWarningThreshold
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 34ae3ad9-1f2c-4ad5-b68a-6b9c21f3b160


ms.date: 05/02/2017
ms.topic: article


---
# UWF\_Overlay.SetWarningThreshold

Sets the warning threshold for monitoring the size of the Unified Write Filter (UWF) overlay.

## Syntax

```powershell
UInt32 SetWarningThreshold(
    UInt32 size
);
```

## Parameters

<a href="" id="size"></a>*size*
An integer that represents the size, in megabytes, of the warning threshold level for the overlay. If *size* is set to 0 (zero), UWF does not raise warning threshold events.

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
<td><p>UWF_OVERLAY_REACHED_WARNING_LEVEL</p></td>
<td><p>0x80010001L</p></td>
<td><p>The UWF overlay size has reached WARNING level.</p></td>
</tr>
</tbody>
</table>

The warning threshold must be lower than the critical threshold.

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