---
title: UWF_RegistryFilter.GetExclusions
description: UWF_RegistryFilter.GetExclusions
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 6e2e8c67-bbb6-4296-93b7-1e95c851ae1b
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
ms.date: 05/02/2017
ms.topic: article


---
# UWF_RegistryFilter.GetExclusions

Retrieves all registry key exclusions from a device that is protected by Unified Write Filter (UWF).

## Syntax

```powershell
UInt32 GetExclusions(
    [out, EmbeddedInstance("UWF_ExcludedRegistryKey")] string ExcludedKeys[]
);
```

## Parameters

**ExcludedKeys**</br>\[out\] An array of [UWF_ExcludedRegistryKey](uwf-excludedregistrykey.md) objects that represent the registry keys excluded from UWF filtering.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

If this method does not find any registry keys in the registry key exclusion list, it sets the *ExcludedKeys* parameter to null.

## Requirements

| Windows Edition        | Supported |
|:-----------------------|:---------:|
| Windows Home           | No        |
| Windows Pro            | No        |
| Windows Enterprise     | Yes       |
| Windows Education      | Yes       |
| Windows IoT Enterprise | Yea       |

## Related topics

- [UWF_RegistryFilter](uwf-registryfilter.md)
- [Unified Write Filter](unified-write-filter.md)
