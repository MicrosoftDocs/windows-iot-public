---
title: UWF_Volume.RemoveAllExclusions
description: UWF_Volume.RemoveAllExclusions
MS-HAID:
- 'p\_embedded.UWF_volumeremoveallexclusions\_blue'
- 'p\_enterprise\_customizations.UWF_volumeremoveallexclusions'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: b947563a-7dca-45e0-a30f-b5c0729856ef
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
ms.date: 05/02/2017
ms.topic: article


---
# UWF_Volume.RemoveAllExclusions

Removes all files and folders from the file exclusion list for a volume protected by Unified Write Filter (UWF).

## Syntax

```powershell
UInt32 RemoveAllExclusions();
```

## Parameters

None.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI errorj constant](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

This command does not remove registry exclusions.

You must use an administrator account to remove file or folder exclusions, and you must restart the device for this change to take effect.

## Requirements

| Windows Edition        | Supported |
|:-----------------------|:---------:|
| Windows Home           | No        |
| Windows Pro            | No        |
| Windows Enterprise     | Yes       |
| Windows Education      | Yes       |
| Windows IoT Enterprise | Yea       |

## Related topics

- [UWF_Volume](uwf-volume.md)
- [Unified Write Filter](unified-write-filter.md)
