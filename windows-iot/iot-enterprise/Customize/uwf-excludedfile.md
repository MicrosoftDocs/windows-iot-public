---
title: UWF\_ExcludedFile
description: UWF\_ExcludedFile
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: a63710d5-2135-4a52-a891-ea2c370ca593


ms.date: 05/02/2017
ms.topic: article


---
# UWF\_ExcludedFile

Contains the files and folders that are currently in the file exclusion list for a volume protected by Unified Write Filter (UWF).

## Syntax

```powershell
class UWF_ExcludedFile {
    [Read] string FileName;
};
```

## Members

The following tables list any methods and properties that belong to this class.

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
<td><p>FileName</p></td>
<td><p>string</p></td>
<td><p>[read]</p></td>
<td><p>The name of the file or folder path in the file exclusion list, including the full path relative to the volume.</p></td>
</tr>
</tbody>
</table>

### Remarks

UWF\_ExcludedFile does not represent an actual WMI object, and you cannot use this class to get or set file exclusions.

You must use the [UWF\_Volume.GetExclusions](uwf-volumegetexclusions.md) method to retrieve UWF\_ExcludedFile objects.

You can use the [UWF\_Volume.AddExclusion](uwf-volumeaddexclusion.md) and [UWF\_Volume.RemoveExclusion](uwf-volumeremoveexclusion.md) methods to add or remove file and folder exclusions to a volume.

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
