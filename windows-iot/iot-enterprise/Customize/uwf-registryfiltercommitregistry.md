---
title: UWF_RegistryFilter.CommitRegistry
description: UWF_RegistryFilter.CommitRegistry
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: d7f96658-7895-43d2-9e26-47a82b164094
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
ms.date: 05/02/2017
ms.topic: article


---
# UWF_RegistryFilter.CommitRegistry

Commits changes to the specified registry key and value.

## Syntax

```powershell
UInt32 CommitRegistry(
    [in] string RegistryKey,
    [in] string ValueName
);
```

## Parameters

**RegistryKey**</br>A string that contains the full path of the registry key to be committed.

**ValueName**</br>A string that contains the name of the value to be committed.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

This method will commit only the value specified by *ValueName* under *RegistryKey* if *ValueName* is specified.

You must use an administrator account to change any properties or call any methods that change the configuration settings.

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
