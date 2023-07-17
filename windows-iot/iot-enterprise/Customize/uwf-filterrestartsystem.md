---
title: UWF_Filter.RestartSystem
description: UWF_Filter.RestartSystem
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 330a9b84-87e9-4091-b92d-d731cee32bff
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# UWF_Filter.RestartSystem

Safely restarts a system protected by UWF, even if the overlay is full.

## Syntax

```powershell
UInt32 RestartSystem();
```

## Parameters

None.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

You must use an administrator account to call this method.
You cannot run on WMI providers; it is only available from Intune/CSP.

If the overlay is full, or near full, shutting down or restarting the system normally can cause the system to take an extremely long time to shut down. This occurs when the system repeatedly tries to write files during shutdown, which constantly fail due to the overlay being full. You can call this method to safely restart a system by avoiding this scenario.

If the overlay becomes full while the system is performing a large amount of writes, such as copying a large group of files, calling this method can still result in a long shutdown time.

## Requirements

| Windows Edition        | Supported |
|:-----------------------|:---------:|
| Windows Home           | No        |
| Windows Pro            | No        |
| Windows Enterprise     | Yes       |
| Windows Education      | Yes       |
| Windows IoT Enterprise | Yea       |

## Related topics

- [UWF_Filter](uwf-filter.md)
- [Unified Write Filter](unified-write-filter.md)
