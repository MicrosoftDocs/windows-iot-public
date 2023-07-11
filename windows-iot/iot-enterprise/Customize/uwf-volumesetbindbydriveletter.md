---
title: UWF\_Volume.SetBindByDriveLetter
description: UWF\_Volume.SetBindByDriveLetter
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: f30cf3fd-eff3-41ad-b9ba-c1ccba7fd43b


ms.date: 05/02/2017
ms.topic: article


---
# UWF\_Volume.SetBindByDriveLetter

Sets the **BindByDriveLetter** property, which indicates if the Unified Write Filter (UWF) volume is bound to the physical volume by drive letter or volume name.

## Syntax

```powereshell
UInt32 SetBindByDriveLetter(
    boolean bBindByDriveLetter
);
```

## Parameters

<a href="" id="bbindbydriveletter"></a>*bBindByDriveLetter*
A Boolean value that indicates the type of binding to use. The **BindByDriveLetter** property is set to this value.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>true</strong></p></td>
<td><p>Binds the UWF volume by the drive letter (<em>loose binding</em>).</p></td>
</tr>
<tr class="even">
<td><p><strong>false</strong></p></td>
<td><p>Binds the UWF volume by the volume name (<em>tight binding</em>).</p></td>
</tr>
</tbody>
</table>

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

Binding by volume name is considered more reliable than binding by drive letter, since drive letters can change for a volume if devices are added or removed.

## Requirements

| Windows Edition       | Supported |
|:----------------------|:----------|
| Windows 10 Home       | No        |
| Windows 10 Pro        | No        |
| Windows 10 Enterprise | Yes       |
| Windows 10 Education  | Yes       |

## Related topics

[UWF\_Volume](uwf-volume.md)

[Unified Write Filter](unified-write-filter.md)