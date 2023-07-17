---
title: UWF_Overlay.SetWarningThreshold
description: UWF_Overlay.SetWarningThreshold
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 34ae3ad9-1f2c-4ad5-b68a-6b9c21f3b160
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# UWF_Overlay.SetWarningThreshold

Sets the warning threshold for monitoring the size of the Unified Write Filter (UWF) overlay.

## Syntax

```powershell
UInt32 SetWarningThreshold(
    UInt32 size
);
```

## Parameters

**size**</br>An integer that represents the size, in megabytes, of the warning threshold level for the overlay. If *size* is set to 0 (zero), UWF does not raise warning threshold events.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

When the size of the overlay reaches or exceeds the *size* threshold value, UWF writes the following notification event to the event log.

| Message ID | Event code | Message text |
|------------|------------|--------------|
|UWF_OVERLAY_REACHED_WARNING_LEVEL | 0x80010001L | The UWF overlay size has reached WARNING level. |

The warning threshold must be lower than the critical threshold.

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
