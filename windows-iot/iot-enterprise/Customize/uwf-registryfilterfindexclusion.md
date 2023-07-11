---
title: UWF\_RegistryFilter.FindExclusion
description: UWF\_RegistryFilter.FindExclusion
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 2d966fba-a834-4356-97bc-8efbf3a97add


ms.date: 05/02/2017
ms.topic: article


---
# UWF\_RegistryFilter.FindExclusion

Checks if a specific registry key is excluded from being filtered by Unified Write Filter (UWF).

## Syntax

```powershell
UInt32 FindExclusion(
    [in] string RegistryKey,
    [out] boolean bFound
);
```

## Parameters

<a href="" id="registrykey"></a>*RegistryKey*
\[in\] A string that contains the full path of the registry key.

<a href="" id="bfound"></a>*bFound*
\[out\] Indicates if the *RegistryKey* is in the exclusion list of registry keys.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

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