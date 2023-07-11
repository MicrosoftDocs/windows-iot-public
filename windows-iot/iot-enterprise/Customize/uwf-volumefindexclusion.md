---
title: UWF\_Volume.FindExclusion
description: UWF\_Volume.FindExclusion
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: d0d593d8-9133-474e-a0e3-0d669a6cfe49


ms.date: 05/02/2017
ms.topic: article


---
# UWF\_Volume.FindExclusion

Checks if a specific file or folder is in the exclusion list for a volume protected by Unified Write Filter (UWF).

## Syntax

```powershell
UInt32 FindExclusion (
    [in] string FileName,
    [out] boolean bFound 
);
```

## Parameters

<a href="" id="filename"></a>*FileName*
\[in\] A string that contains the full path of the file or folder relative to the volume.

<a href="" id="bfound"></a>*bFound*
\[out\] Indicates if *FileName* is in the file exclusion list for the volume.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error constant](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

**FindExclusion** sets *bFound* to **true** only for file and folder exclusions that have been explicitly added to the exclusion list. Files and subfolders that are in an excluded folder are not identified as excluded by **FindExclusion**, unless they have been explicitly excluded.

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