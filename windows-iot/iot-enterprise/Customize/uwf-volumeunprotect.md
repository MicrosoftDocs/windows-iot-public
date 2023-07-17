---
title: UWF_Volume.Unprotect
description: UWF_Volume.Unprotect
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 958533dd-ee96-498d-aed8-d4e019e8da64
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# UWF_Volume.Unprotect

Disables UWF protection of the volume after the next system restart.

## Syntax

```powershell
UInt32 Unprotect();
```

## Parameters

None.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error constant](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

Unprotecting the volume does not remove the [UWF_Volume](uwf-volume.md) entry or any configuration settings from the UWF configuration registry. This means that you can unprotect a volume, and then protect it again later, while keeping any file exclusions or volume configurations that you have defined.

## Requirements

| Windows Edition       | Supported |
|:----------------------|:----------|
| Windows 10/11 Home       | No        |
| Windows 10/11 Pro        | No        |
| Windows 10/11 Enterprise | Yes       |
| Windows 10/11 Education  | Yes       |
| Windows 10/11 IoT Enterprise | Yes |

## Related topics

- [UWF_Volume](uwf-volume.md)
- [Unified Write Filter](unified-write-filter.md)
