---
title: UWF\_Servicing.Enable
description: UWF\_Servicing.Enable
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: c93b858c-dcb4-4563-80f5-aac3909aae31
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# UWF\_Servicing.Enable

Enables Unified Write Filter (UWF) servicing mode.

## Syntax

```powershell
UInt32 Enable();
```

## Parameters

None.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

When this method is called, the system will enter servicing mode in the next session after a restart.

## Requirements

| Windows Edition       | Supported |
|:----------------------|:----------|
| Windows 10 Home       | No        |
| Windows 10 Pro        | No        |
| Windows 10 Enterprise | Yes       |
| Windows 10 Education  | Yes       |

## Related topics

[UWF\_Servicing](uwf-servicing.md)

[Unified Write Filter](unified-write-filter.md)