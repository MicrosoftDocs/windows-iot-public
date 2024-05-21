---
title: UWF_Volume.AddExclusion
description: UWF_Volume.AddExclusion
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 75c1cd6c-2101-499a-856e-66eadb43ec05
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
ms.date: 05/20/2024
ms.topic: article


---
# UWF_Volume.AddExclusion

Adds a file or folder to the file exclusion list for a volume protected by Unified Write Filter (UWF).

## Syntax

```powershell
UInt32 AddExclusion(
    string FileName
);
```

## Parameters

**FileName**</br>A string that contains the full path of the file or folder relative to the volume.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

You must use an administrator account to add or remove file or folder exclusions during run time, and you must restart the device for new exclusions to take effect.

> [!IMPORTANT]
> You can’t add exclusions for the following items:
>
> - The volume root. For example, C: or D:.
> - The \Windows folder on the system volume.
> - The \Windows\System32 folder on the system volume.
> - The \Windows\system32\drivers folder on the system volume.
> - Paging files.

However, you can exclude subdirectories and files under these items.

## Requirements

| Windows Edition        | Supported |
|:-----------------------|:---------:|
| Windows Home           | No        |
| Windows Pro            | No        |
| Windows Enterprise     | Yes       |
| Windows Education      | Yes       |
| Windows IoT Enterprise | Yes       |

## Related topics

- [UWF_Volume](uwf-volume.md)
- [Unified Write Filter](unified-write-filter.md)
