---
title: UWF_RegistryFilter.CommitRegistryDeletion
description: UWF_RegistryFilter.CommitRegistryDeletion
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: fe299a59-76e6-4b13-9e58-787eaf2e44d4
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# UWF_RegistryFilter.CommitRegistryDeletion

Deletes the specified registry key or registry value and commits the deletion.

## Syntax

```powershell
UInt32 CommitRegistryDeletion(
    string Registrykey,
    string ValueName
);
```

## Parameters

**RegistryKey**</br>A string that contains the full path of the registry key that contains the value to be deleted. If *ValueName* is empty, the entire registry key is deleted.

**ValueName**</br>A string that contains the name of the value to be deleted.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

If *ValueName* is specified, this method will delete only the value specified by *ValueName* that is contained by *RegistryKey*. If *ValueName* is empty, the entire *RegistryKey* and all its sub keys are deleted.

This method deletes the registry key or registry value from both the overlay and the persistent storage.

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
