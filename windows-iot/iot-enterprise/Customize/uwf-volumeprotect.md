---
title: UWF_Volume.Protect
description: UWF_Volume.Protect
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 4008d339-ec6f-43b5-b21b-b6923e2f40aa
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
ms.date: 05/20/2024
ms.topic: article


---
# UWF_Volume.Protect

Enables Unified Write Filter (UWF) to protect the volume after the next system restart, if UWF is enabled after the restart.

## Syntax

```powershell
UInt32 Protect();
```

## Parameters

None.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error constant](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

UWF starts protecting the volume after the next device restart in which UWF is enabled.

This method does not enable UWF if it is disabled; you must explicitly enable UWF for the next session to start volume protection.

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
