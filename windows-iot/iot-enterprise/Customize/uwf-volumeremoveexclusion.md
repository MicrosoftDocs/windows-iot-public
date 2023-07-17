---
title: UWF_Volume.RemoveExclusion
description: UWF_Volume.RemoveExclusion
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: e1888142-98a9-4d7a-a94d-3bf188afd44e
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# UWF_Volume.RemoveExclusion

Removes a specific file or folder from the file exclusion list for a volume protected by Unified Write Filter (UWF).

## Syntax

```powershell
UInt32 RemoveExclusion(
    string FileName
);
```

## Parameters

**FileName**</br>A string that contains the full path of the file or folder relative to the volume.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error constant](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

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
