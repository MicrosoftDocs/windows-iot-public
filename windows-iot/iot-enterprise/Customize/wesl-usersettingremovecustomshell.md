---
title: WESL\_UserSetting.RemoveCustomShell
description: WESL\_UserSetting.RemoveCustomShell
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 161eb289-e3b5-4d16-b367-f79f2b90f291
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# WESL\_UserSetting.RemoveCustomShell

This method removes a Shell Launcher configuration for a specific user or group, based on the security identifier (SID).

## Syntax

```powershell
[Static] uint32 RemoveCustomShell (
    [In, Required] string Sid
);
```

## Parameters

<a href="" id="sid"></a>Sid  
\[in, required\] A string containing the security identifier (SID) of the user or group that Shell Launcher is configured for.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

You must restart your device for the changes to take effect.

## Requirements

| Windows Edition       | Supported |
|:----------------------|:----------|
| Windows 10 Home       | No        |
| Windows 10 Pro        | No        |
| Windows 10 Enterprise | Yes       |
| Windows 10 Education  | Yes       |

## Related topics

[WESL\_UserSetting](wesl-usersetting.md)

[Shell Launcher](shell-launcher.md)