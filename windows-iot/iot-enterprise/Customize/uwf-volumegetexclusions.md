---
title: UWF\_Volume.GetExclusions
description: UWF\_Volume.GetExclusions
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: a4d4e7fd-04f3-4348-986a-ad37de8b62fb


ms.date: 05/02/2017
ms.topic: article


---
# UWF\_Volume.GetExclusions

Gets a list of all file exclusions for a Unified Write Filter (UWF) protected volume.

## Syntax

```powershell
UInt32 GetExclusions(
    [out, EmbeddedInstance("UWF_ExcludedFile")] string ExcludedFiles[]
);
```

## Parameters

<a href="" id="excludedfiles"></a>*ExcludedFiles*  
\[out\] An array of [UWF\_ExcludedFile](uwf-excludedfile.md) objects that represent the files and folders that are excluded from UWF filtering for a volume.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error constant](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

If **GetExclusions** does not find any files or folders in the file exclusion list for the volume, **GetExclusions** sets the *ExcludedFiles* parameter to null.

## Requirements

| Windows Edition       | Supported |
|:----------------------|:----------|
| Windows 10 Home       | No        |
| Windows 10 Pro        | No        |
| Windows 10 Enterprise | Yes       |
| Windows 10 Education  | Yes       |

## Related topics

[UWF\_Volume](uwf-volume.md)

[Unified Write Filter](unified-write-filter.md)