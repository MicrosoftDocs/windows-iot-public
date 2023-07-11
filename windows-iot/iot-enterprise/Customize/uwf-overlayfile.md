---
title: UWF\_OverlayFile
description: UWF\_OverlayFile
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 8b258f33-2cf9-46c8-8a66-efa567d63899


ms.date: 05/02/2017
ms.topic: article


---
# UWF\_OverlayFile

Contains a file that is currently in the overlay for a volume protected by Unified Write Filter (UWF).

## Syntax

```powershell
class UWF_OverlayFile {
    [read] string FileName;
    [read] UInt64 FileSize;
};
```

## Members

The following table lists any properties that belong to this class.

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
<th>Qualifier</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>FileName</strong></p></td>
<td><p>string</p></td>
<td><p>[read]</p></td>
<td><p>The name of the file in the file overlay.</p></td>
</tr>
<tr class="even">
<td><p><strong>FileSize</strong></p></td>
<td><p>UInt64</p></td>
<td><p>[read]</p></td>
<td><p>The size of the file in the file overlay.</p></td>
</tr>
</tbody>
</table>

### Remarks

You cannot use the **UWF\_ OverlayFile** class directly to get overlay files. You must use the **UWF\_Overlay.GetOverlayFiles** method to retrieve **UWF\_ OverlayFile** objects.

For more information about specific limitations and conditions when using the **GetOverlayFiles** method, see the **Remarks** section in the [UWF\_Overlay.GetOverlayFiles](uwf-overlaygetoverlayfiles.md) topic in the UWF WMI provider technical reference.

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
