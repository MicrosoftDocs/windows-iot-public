---
title: WESL_UserSetting.IsEnabled
description: WESL_UserSetting.IsEnabled
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 567f57b5-f9c8-4129-8279-dd351028df5d
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# WESL_UserSetting.IsEnabled

This method retrieves a value that indicates if Shell Launcher is enabled or disabled.

## Syntax

```powershell
[Static] uint32 IsEnabled(
    [Out, Required] boolean Enabled
);
```

## Parameters

**Enabled**</br>\[out, required\] A Boolean value that indicates if Shell Launcher is enabled.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Requirements

| Windows Edition       | Supported |
|:----------------------|:----------|
| Windows 10 Home       | No        |
| Windows 10 Pro        | No        |
| Windows 10 Enterprise | Yes       |
| Windows 10 Education  | Yes       |

## Related topics

[WESL_UserSetting](wesl-usersetting.md)

[Shell Launcher](shell-launcher.md)