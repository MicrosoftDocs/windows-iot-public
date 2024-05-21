---
title: UWF_Servicing.Enable
description: UWF_Servicing.Enable
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: c93b858c-dcb4-4563-80f5-aac3909aae31
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
ms.date: 05/20/2024
ms.topic: article


---
# UWF_Servicing.Enable

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

| Windows Edition        | Supported |
|:-----------------------|:---------:|
| Windows Home           | No        |
| Windows Pro            | No        |
| Windows Enterprise     | Yes       |
| Windows Education      | Yes       |
| Windows IoT Enterprise | Yes       |

## Related topics

- [UWF_Servicing](uwf-servicing.md)
- [Unified Write Filter](unified-write-filter.md)
