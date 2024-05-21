---
title: UWF_Filter.ShutdownSystem
description: UWF_Filter.ShutdownSystem
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 82bb40de-a8c1-4989-82e6-1f314ed699db
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
ms.date: 05/20/2024
ms.topic: article


---
# UWF_Filter.ShutdownSystem

Safely shuts down a system protected by UWF, even if the overlay is full.

## Syntax

```powershell
UInt32 ShutdownSystem();
```

## Parameters

None.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

You must use an administrator account to call this method.

If the overlay is full, or near full, shutting down or restarting the system normally can cause the system to take an extremely long time to shut down. This occurs when the system repeatedly tries to write files during shutdown, which constantly fail due to the overlay being full. You can call this method to safely shutdown a system by avoiding this scenario.

If the overlay becomes full while the system is performing a large amount of writes, such as copying a large group of files, calling this method can still result in a long shutdown time.

## Requirements

| Windows Edition        | Supported |
|:-----------------------|:---------:|
| Windows Home           | No        |
| Windows Pro            | No        |
| Windows Enterprise     | Yes       |
| Windows Education      | Yes       |
| Windows IoT Enterprise | Yes       |

## Related topics

- [UWF_Filter](uwf-filter.md)
- [Unified Write Filter](unified-write-filter.md)
