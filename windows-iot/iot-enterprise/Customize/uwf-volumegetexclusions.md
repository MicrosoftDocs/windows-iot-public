---
title: UWF_Volume.GetExclusions
description: UWF_Volume.GetExclusions
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: a4d4e7fd-04f3-4348-986a-ad37de8b62fb
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# UWF_Volume.GetExclusions

Gets a list of all file exclusions for a Unified Write Filter (UWF) protected volume.

## Syntax

```powershell
UInt32 GetExclusions(
    [out, EmbeddedInstance("UWF_ExcludedFile")] string ExcludedFiles[]
);
```

## Parameters

**ExcludedFiles**</br>\[out\] An array of [UWF_ExcludedFile](uwf-excludedfile.md) objects that represent the files and folders that are excluded from UWF filtering for a volume.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error constant](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

If **GetExclusions** does not find any files or folders in the file exclusion list for the volume, **GetExclusions** sets the *ExcludedFiles* parameter to null.

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
