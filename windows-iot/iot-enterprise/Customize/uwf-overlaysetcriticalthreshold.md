---
title: UWF_Overlay.SetCriticalThreshold
description: UWF_Overlay.SetCriticalThreshold
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 970dd0a5-ce9c-40d1-b6f5-772c9992f62a
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# UWF_Overlay.SetCriticalThreshold

Sets the critical threshold for monitoring the size of the Unified Write Filter (UWF) overlay.

## Syntax

```powershell
UInt32 SetCriticalThreshold(
    UInt32 size
);
```

## Parameters

**size**</br>An integer that represents the size, in megabytes, of the critical threshold level for the overlay. If *size* is 0 (zero), UWF does not raise critical threshold events.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

When the size of the overlay reaches or exceeds the *size* threshold value, UWF writes the following notification event to the event log.

| Message ID | Event code | Message text |
|------------|------------|--------------|
| UWF_OVERLAY_REACHED_CRITICAL_LEVEL | 0x80010002L | The UWF overlay size has reached CRITICAL level. |

The critical threshold must be higher than the warning threshold.

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
