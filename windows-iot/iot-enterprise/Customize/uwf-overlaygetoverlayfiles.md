---
title: UWF_Overlay.GetOverlayFiles
description: UWF_Overlay.GetOverlayFiles
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 6f8f544d-0f97-47ca-8ab4-f452e457e788
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# UWF_Overlay.GetOverlayFiles

Returns a list of files of a volume that were cached in the Unified Write Filter (UWF) overlay.

## Syntax

```powershell
UInt32 GetOverlayFiles(
    [in] string Volume,
    [out, EmbeddedInstance("UWF_OverlayFile")] string OverlayFiles[]
);
```

## Parameters

**Volume**</br>A string that specifies the drive letter or volume name.

**OverlayFiles**</br>An array of **UWF_OverlayFiles** objects embedded as strings.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

You must use an administrator account to access this method.

The **GetOverlayFiles** method is intended to be used as a diagnostic tool.

Do not base decisions about what to commit based on this method’s output.

You should be aware of the following limitations:

- This method is only supported on the NTFS file system.
- This method requires a significant amount of free system memory to succeed (in a linear relationship to overlay usage). The method call fails when there is insufficient memory available to complete the call.
- This method requires significant time to complete (in an exponential relationship to overlay usage).
- This method may show files that are affected by seemingly unrelated operations to both registry and file exclusions and commits.

You should also be aware of the following items when you use the **GetOverlayFiles** method:

- Files that were committed with the `uwfmgr.exe file commit` command are also contained in the overlay files list.
- Excluded files may be contained in the overlay files list.
- Files that are smaller than the cluster size (for example, 4 KB in most cases) will not be listed even if they are cached in overlay.
- Changes and deletions in excluded directories, excluded files, or excluded registry items add to overlay usage.
- File and registry commits add to overlay usage.

## Requirements

| Windows Edition       | Supported |
|:----------------------|:----------|
| Windows 10/11 Home       | No        |
| Windows 10/11 Pro        | No        |
| Windows 10/11 Enterprise | Yes       |
| Windows 10/11 Education  | Yes       |
| Windows 10/11 IoT Enterprise | Yes |

## Related topics

- [UWF_Overlay](uwf-overlay.md)
- [Unified Write Filter](unified-write-filter.md)
