---
title: UWF\_Volume.CommitFile
description: UWF\_Volume.CommitFile
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 816f2a96-bcad-4fbf-ac68-606d5e36b89e
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# UWF\_Volume.CommitFile

Commits changes from the overlay to the physical volume for a specified file on a volume protected by Unified Write Filter (UWF).

## Syntax

```powershell
UInt32 CommitFile(
    [in] string FileName
);
```

## Parameters

<a href="" id="filename"></a>*FileName*
\[in\] A string that contains the path of the file to commit on the overlay, but does not include the drive letter or volume name. For example, “\\users\\test.dat”.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error constant](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

The *FileName* must contain the name of a file that exists. The **CommitFile** method cannot commit a file that does not exist.

You must use an administrator account to change any properties or call any methods that change the configuration settings.

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