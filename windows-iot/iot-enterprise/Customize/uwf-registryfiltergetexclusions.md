---
title: UWF\_RegistryFilter.GetExclusions
description: UWF\_RegistryFilter.GetExclusions
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 6e2e8c67-bbb6-4296-93b7-1e95c851ae1b


ms.date: 05/02/2017
ms.topic: article


---
# UWF\_RegistryFilter.GetExclusions

Retrieves all registry key exclusions from a device that is protected by Unified Write Filter (UWF).

## Syntax

```powershell
UInt32 GetExclusions(
    [out, EmbeddedInstance("UWF_ExcludedRegistryKey")] string ExcludedKeys[]
);
```

## Parameters

<a href="" id="excludedkeys"></a>*ExcludedKeys*
\[out\] An array of [UWF\_ExcludedRegistryKey](uwf-excludedregistrykey.md) objects that represent the registry keys excluded from UWF filtering.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

If this method does not find any registry keys in the registry key exclusion list, it sets the *ExcludedKeys* parameter to null.

## Requirements

| Windows Edition       | Supported |
|:----------------------|:----------|
| Windows 10 Home       | No        |
| Windows 10 Pro        | No        |
| Windows 10 Enterprise | Yes       |
| Windows 10 Education  | Yes       |

## Related topics

[UWF\_RegistryFilter](uwf-registryfilter.md)

[Unified Write Filter](unified-write-filter.md)