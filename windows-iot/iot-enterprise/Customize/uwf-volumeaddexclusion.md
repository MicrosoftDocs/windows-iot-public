---
title: UWF\_Volume.AddExclusion
description: UWF\_Volume.AddExclusion
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 75c1cd6c-2101-499a-856e-66eadb43ec05


ms.date: 05/02/2017
ms.topic: article


---
# UWF\_Volume.AddExclusion

Adds a file or folder to the file exclusion list for a volume protected by Unified Write Filter (UWF).

## Syntax

```powershell
UInt32 AddExclusion(
    string FileName
);
```

## Parameters

<a href="" id="filename"></a>*FileName*
A string that contains the full path of the file or folder relative to the volume.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

You must use an administrator account to add or remove file or folder exclusions during run time, and you must restart the device for new exclusions to take effect.

> [!Important]
> You can’t add exclusions for the following items:
>
> * The volume root. For example, C: or D:.
> * The \\Windows folder on the system volume.
> * The \\Windows\\System32 folder on the system volume.
> * The \\Windows\\system32\\drivers folder on the system volume.
> * Paging files.

However, you can exclude subdirectories and files under these items.

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

 

