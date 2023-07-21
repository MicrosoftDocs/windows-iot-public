---
title: UWF_RegistryFilter.AddExclusion
description: UWF_RegistryFilter.AddExclusion
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 65eba07c-1ef4-426c-8741-b9ec31817768
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# UWF_RegistryFilter.AddExclusion

Adds a registry key to the registry exclusion list for Unified Write Filter (UWF).

> [!IMPORTANT]
> Only registry subkeys under the following registry keys can be added to the exclusion list.
>
> - HKEY_LOCAL_MACHINE\BCD00000000
> - HKEY_LOCAL_MACHINE\SYSTEM
> - HKEY_LOCAL_MACHINE\SOFTWARE
> - HKEY_LOCAL_MACHINE\SAM
> - HKEY_LOCAL_MACHINE\SECURITY
> - HKEY_LOCAL_MACHINE\COMPONENTS

> [!IMPORTANT]
> Excluding a registry key from filtering also excludes all subkeys from filtering.

## Syntax

```powershell
UInt32 AddExclusion(
    string RegistryKey
);
```

## Parameters

**RegistryKey**</br>A string that contains the full path of the registry key.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

You must restart the device before the registry key is excluded from UWF filtering.

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
