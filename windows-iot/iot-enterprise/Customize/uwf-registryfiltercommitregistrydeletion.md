---
title: UWF\_RegistryFilter.CommitRegistryDeletion
description: UWF\_RegistryFilter.CommitRegistryDeletion
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: fe299a59-76e6-4b13-9e58-787eaf2e44d4


ms.date: 05/02/2017
ms.topic: article


---
# UWF\_RegistryFilter.CommitRegistryDeletion

Deletes the specified registry key or registry value and commits the deletion.

## Syntax

```powershell
UInt32 CommitRegistryDeletion(
    string Registrykey,
    string ValueName
);
```

## Parameters

<a href="" id="registrykey"></a>*RegistryKey*
A string that contains the full path of the registry key that contains the value to be deleted. If *ValueName* is empty, the entire registry key is deleted.

<a href="" id="valuename"></a>*ValueName*
A string that contains the name of the value to be deleted.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

If *ValueName* is specified, this method will delete only the value specified by *ValueName* that is contained by *RegistryKey*. If *ValueName* is empty, the entire *RegistryKey* and all its sub keys are deleted.

This method deletes the registry key or registry value from both the overlay and the persistent storage.

You must use an administrator account to change any properties or call any methods that change the configuration settings.

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