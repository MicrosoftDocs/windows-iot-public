---
title: UWF\_Volume.CommitFileDeletion
description: UWF\_Volume.CommitFileDeletion
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 0a5d9361-d5a5-48db-8035-127f54c79b04
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# UWF\_Volume.CommitFileDeletion

Deletes the specified file and commits the deletion to the physical volume.

## Syntax

```powershell
UInt32 CommitFileDeletion(
    string FileName
);
```

## Parameters

<a href="" id="filename"></a>*FileName*
\[in\] A string that contains the path of the file to delete, but does not include the drive letter or volume name. For example: “\\users\\test.dat”.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error constant](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

The *FileName* must contain the name of a file that exists on the physical volume. The **CommitFileDeletion** method cannot delete a file that does not exist.

You must use an administrator account to call this method.

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