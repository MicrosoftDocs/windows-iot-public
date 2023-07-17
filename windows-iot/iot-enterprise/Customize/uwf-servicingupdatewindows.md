---
title: UWF_Servicing.UpdateWindows
description: UWF_Servicing.UpdateWindows
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 578ee0ac-fcc9-4021-9967-7b3f20eaadee
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# UWF_Servicing.UpdateWindows

Calls Windows Update to download and install critical and security updates for your device running Windows 10 Enterprise.

## Syntax

```powershell
UInt32 UpdateWindows(
    [out] UInt32 UpdateStatus
);
```

## Parameters

**UpdateStatus**</br>\[out\] An integer that contains the status of the Windows Update operation, according to the following table:

| UpdateStatus     | Description       |
|:----------------:|-------------------|
| 0                | Success.          |
| 3010             | Restart required. |
| Any other value. | Generic error.    |

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

This method is meant to be used as part of a servicing script. For more information, see [Service UWF-protected devices](service-uwf-protected-devices.md).

This method does not disable or enable Unified Write Filter (UWF). If you call this method while UWF is enabled, updates may be lost when the device restarts.

## Requirements

| Windows Edition       | Supported |
|:----------------------|:----------|
| Windows 10/11 Home       | No        |
| Windows 10/11 Pro        | No        |
| Windows 10/11 Enterprise | Yes       |
| Windows 10/11 Education  | Yes       |
| Windows 10/11 IoT Enterprise | Yes |

## Related topics

- [UWF_Servicing](uwf-servicing.md)
- [Unified Write Filter](unified-write-filter.md)
