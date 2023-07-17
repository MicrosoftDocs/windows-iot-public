---
title: UWF_RegistryFilter.FindExclusion
description: UWF_RegistryFilter.FindExclusion
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 2d966fba-a834-4356-97bc-8efbf3a97add
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# UWF_RegistryFilter.FindExclusion

Checks if a specific registry key is excluded from being filtered by Unified Write Filter (UWF).

## Syntax

```powershell
UInt32 FindExclusion(
    [in] string RegistryKey,
    [out] boolean bFound
);
```

## Parameters

**RegistryKey**</br>\[in\] A string that contains the full path of the registry key.

**bFound**</br>\[out\] Indicates if the *RegistryKey* is in the exclusion list of registry keys.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

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
