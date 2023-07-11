---
title: UWF\_ExcludedRegistryKey
description: UWF\_ExcludedRegistryKey
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: dbac2371-1236-476c-bd97-b00abf7def85


ms.date: 05/02/2017
ms.topic: article


---
# UWF\_ExcludedRegistryKey

Contains the registry keys that are currently in the registry key exclusion list for Unified Write Filter (UWF).

## Syntax

```powershell
class UWF_ExcludedRegistryKey {
    [Read] string RegistryKey;
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
<td><p>RegistryKey</p></td>
<td><p>string</p></td>
<td><p>[read]</p></td>
<td><p>The full path of the registry key in the registry key exclusion list.</p></td>
</tr>
</tbody>
</table>

### Remarks

UWF\_ExcludedRegistryKeydoes not represent an actual WMI object, and you cannot use this class to get or set registry key exclusions.

You can use the [UWF\_RegistryFilter.GetExclusions](uwf-registryfiltergetexclusions.md) or [UWF\_RegistryFilter.FindExclusion](uwf-registryfilterfindexclusion.md) methods to retrieve UWF\_ExcludedRegistryKey objects.

You can use the [UWF\_Volume.AddExclusion](uwf-volumeaddexclusion.md) and [UWF\_Volume.RemoveExclusion](uwf-volumeremoveexclusion.md) methods to add or remove registry keys to the UWF registry key exclusion list.

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
