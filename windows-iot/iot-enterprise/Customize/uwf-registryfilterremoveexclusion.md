---
title: UWF\_RegistryFilter.RemoveExclusion
description: UWF\_RegistryFilter.RemoveExclusion
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: c65b231b-988b-47fa-9b87-06a0d5d29c0f


ms.date: 05/02/2017
ms.topic: article


---
# UWF\_RegistryFilter.RemoveExclusion

Removes a registry key from the registry exclusion list for Unified Write Filter (UWF).

## Syntax

```powershell
UInt32 RemoveExclusion(
    string RegistryKey
);
```

## Parameters

<a href="" id="registrykey"></a>*RegistryKey*
A string that contains the full path of the registry key.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

You must restart the device before the registry key is excluded from UWF filtering.

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