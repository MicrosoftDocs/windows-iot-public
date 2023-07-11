---
title: UWF\_RegistryFilter.CommitRegistry
description: UWF\_RegistryFilter.CommitRegistry
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: d7f96658-7895-43d2-9e26-47a82b164094
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# UWF\_RegistryFilter.CommitRegistry

Commits changes to the specified registry key and value.

## Syntax

```powershell
UInt32 CommitRegistry(
    [in] string RegistryKey,
    [in] string ValueName
);
```

## Parameters

<a href="" id="registrykey"></a>*RegistryKey*
A string that contains the full path of the registry key to be committed.

<a href="" id="valuename"></a>*ValueName*
A string that contains the name of the value to be committed.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

This method will commit only the value specified by *ValueName* under *RegistryKey* if *ValueName* is specified.

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