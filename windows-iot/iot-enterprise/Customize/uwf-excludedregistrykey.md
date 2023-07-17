---
title: UWF_ExcludedRegistryKey
description: UWF_ExcludedRegistryKey
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: dbac2371-1236-476c-bd97-b00abf7def85
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# UWF_ExcludedRegistryKey

Contains the registry keys that are currently in the registry key exclusion list for Unified Write Filter (UWF).

## Syntax

```powershell
class UWF_ExcludedRegistryKey {
    [Read] string RegistryKey;
};
```

## Members

The following tables list any methods and properties that belong to this class.

### Properties

| Property    | Data&nbsp;type | Qualifier | Description |
|-------------|----------------|-----------|-------------|
| RegistryKey | string         | [read]    | The full path of the registry key in the registry key exclusion list. |

### Remarks

UWF_ExcludedRegistryKeydoes not represent an actual WMI object, and you cannot use this class to get or set registry key exclusions.

You can use the [UWF_RegistryFilter.GetExclusions](uwf-registryfiltergetexclusions.md) or [UWF_RegistryFilter.FindExclusion](uwf-registryfilterfindexclusion.md) methods to retrieve UWF_ExcludedRegistryKey objects.

You can use the [UWF_Volume.AddExclusion](uwf-volumeaddexclusion.md) and [UWF_Volume.RemoveExclusion](uwf-volumeremoveexclusion.md) methods to add or remove registry keys to the UWF registry key exclusion list.

## Requirements

| Windows Edition              | Supported |
|:-----------------------------|:---------:|
| Windows 10/11 Home           | No        |
| Windows 10/11 Pro            | No        |
| Windows 10/11 Enterprise     | Yes       |
| Windows 10/11 Education      | Yes       |
| Windows 10/11 IoT Enterprise | Yes       |

## Related topics

- [Unified Write Filter WMI provider reference](uwf-wmi-provider-reference.md)
- [Unified Write Filter](unified-write-filter.md)
