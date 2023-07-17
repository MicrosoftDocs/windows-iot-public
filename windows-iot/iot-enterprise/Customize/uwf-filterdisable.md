---
title: UWF_Filter.Disable
description: UWF_Filter.Disable
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 8f5a9ac7-5dd1-4eec-985c-7d06961e35df
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# UWF_Filter.Disable

Disables Unified Write Filter (UWF) on the next restart.

## Syntax

```powershell
UInt32 Disable();
```

## Parameters

None.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

You must use an administrator account to disable UWF.

## Requirements

| Windows Edition       | Supported |
|:----------------------|:----------|
| Windows 10/11 Home       | No        |
| Windows 10/11 Pro        | No        |
| Windows 10/11 Enterprise | Yes       |
| Windows 10/11 Education  | Yes       |
| Windows 10/11 IoT Enterprise | Yes   |

## Related topics

- [UWF_Filter](uwf-filter.md)
- [Unified Write Filter](unified-write-filter.md)
