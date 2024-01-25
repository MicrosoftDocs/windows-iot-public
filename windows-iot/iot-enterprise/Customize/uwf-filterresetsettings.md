---
title: UWF_Filter.ResetSettings
description: UWF_Filter.ResetSettings
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: dd7fe440-a108-46dd-b1db-09f5176f0b6f
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
ms.date: 05/02/2017
ms.topic: article


---
# UWF_Filter.ResetSettings

Restores UWF settings to the original configuration settings.

## Syntax

```powershell
UInt32 ResetSettings();
```

## Parameters

None.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

You must use an administrator account to reset UWF settings.

The original configuration settings are captured the first time that you enable UWF after you add UWF to your device by using **Turn Windows features on or off**. You can change the original configuration settings by using **Turn Windows features on or off** to remove and then add UWF, and then modifying the configuration to the desired state before you enable UWF.

If you added UWF to your device by using SMI settings in an unattend.xml file, the original configuration settings are captured when Windows 10 Enterpriseis installed on your device.

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
