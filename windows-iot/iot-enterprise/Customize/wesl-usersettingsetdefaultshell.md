---
title: WESL_UserSetting.SetDefaultShell
description: WESL_UserSetting.SetDefaultShell
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: fb4040bb-7cf2-4644-bf0f-d7d0274dd080
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
ms.date: 05/20/2024
ms.topic: article


---
# WESL_UserSetting.SetDefaultShell

This method sets the default Shell Launcher configuration.

## Syntax

```powershell
[Static] uint32 SetDefaultShell (
    [In, Required] string Shell,
    [In, Required] sint32 DefaultAction
);
```

## Parameters

**Shell**</br>\[in, required\] The application or executable that Shell Launcher starts as the shell.

**DefaultAction**</br>\[in, required\] The default action that Shell Launcher takes when the *Shell* application exits.

The possible actions are defined in the following table:

| Value | Description |
|:-------:|-------------|
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
