---
title: WESL_UserSetting.GetDefaultShell
description: WESL_UserSetting.GetDefaultShell
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 26dc7e10-6e89-44e0-aec2-322676e8b2d1
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
ms.date: 05/20/2024
ms.topic: article


---
# WESL_UserSetting.GetDefaultShell

This method retrieves the default Shell Launcher configuration.

## Syntax

```powershell
[Static] uint32 GetDefaultShell (
    [Out, Required] string Shell,
    [Out, Required] sint32 DefaultAction
);
```

## Parameters

**Shell**</br>\[out, required\] The application or executable that Shell Launcher starts as the shell.

**DefaultAction**</br>\[out, required\] The default action Shell Launcher takes when the shell application exits.

The possible actions are defined in the following table:

| Value | Description |
|:-----:|-------------|
| 0 | Restart the shell. |
| 1 | Restart the device. |
| 2 | Shut down the device. |
| 3 | Do nothing. |

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

Shell Launcher uses the default configuration when the security identifier (SID) of the user who is currently signed in does not match any custom defined Shell Launcher configurations.

## Requirements

| Windows Edition        | Supported |
|:-----------------------|:---------:|
| Windows Home           | No        |
| Windows Pro            | No        |
| Windows Enterprise     | Yes       |
| Windows Education      | Yes       |
| Windows IoT Enterprise | Yes       |

## Related topics

- [WESL_UserSetting](wesl-usersetting.md)
- [Shell Launcher](shell-launcher.md)
