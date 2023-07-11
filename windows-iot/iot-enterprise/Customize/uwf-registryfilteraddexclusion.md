---
title: UWF\_RegistryFilter.AddExclusion
description: UWF\_RegistryFilter.AddExclusion
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 65eba07c-1ef4-426c-8741-b9ec31817768


ms.date: 05/02/2017
ms.topic: article


---
# UWF\_RegistryFilter.AddExclusion

Adds a registry key to the registry exclusion list for Unified Write Filter (UWF).

> [!Important]
> Only registry subkeys under the following registry keys can be added to the exclusion list.
>
> * HKEY\_LOCAL\_MACHINE\\BCD00000000
> * HKEY\_LOCAL\_MACHINE\\SYSTEM
> * HKEY\_LOCAL\_MACHINE\\SOFTWARE
> * HKEY\_LOCAL\_MACHINE\\SAM
> * HKEY\_LOCAL\_MACHINE\\SECURITY
> * HKEY\_LOCAL\_MACHINE\\COMPONENTS

> [!Important]
> Excluding a registry key from filtering also excludes all subkeys from filtering.

## Syntax

```powershell
UInt32 AddExclusion(
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