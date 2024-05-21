---
title: UWF_Volume.SetBindByDriveLetter
description: UWF_Volume.SetBindByDriveLetter
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: f30cf3fd-eff3-41ad-b9ba-c1ccba7fd43b
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
ms.date: 05/20/2024
ms.topic: article


---
# UWF_Volume.SetBindByDriveLetter

Sets the **BindByDriveLetter** property, which indicates if the Unified Write Filter (UWF) volume is bound to the physical volume by drive letter or volume name.

## Syntax

```powereshell
UInt32 SetBindByDriveLetter(
    boolean bBindByDriveLetter
);
```

## Parameters

**bBindByDriveLetter**</br>A Boolean value that indicates the type of binding to use. The **BindByDriveLetter** property is set to this value.

| Value  | Description  |
|:------:|--------------|
| **true**  | Binds the UWF volume by the drive letter (*loose binding*). |
| **false** | Binds the UWF volume by the volume name (*tight binding*). |

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

Binding by volume name is considered more reliable than binding by drive letter, since drive letters can change for a volume if devices are added or removed.

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
