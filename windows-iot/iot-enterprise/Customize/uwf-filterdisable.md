---
title: UWF\_Filter.Disable
description: UWF\_Filter.Disable
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 8f5a9ac7-5dd1-4eec-985c-7d06961e35df


ms.date: 05/02/2017
ms.topic: article


---
# UWF\_Filter.Disable

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
| Windows 10 Home       | No        |
| Windows 10 Pro        | No        |
| Windows 10 Enterprise | Yes       |
| Windows 10 Education  | Yes       |

## Related topics

[UWF\_Filter](uwf-filter.md)

[Unified Write Filter](unified-write-filter.md)