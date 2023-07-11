---
title: WESL\_UserSetting.SetDefaultShell
description: WESL\_UserSetting.SetDefaultShell
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: fb4040bb-7cf2-4644-bf0f-d7d0274dd080


ms.date: 05/02/2017
ms.topic: article


---
# WESL\_UserSetting.SetDefaultShell

This method sets the default Shell Launcher configuration.

## Syntax

```powershell
[Static] uint32 SetDefaultShell (
    [In, Required] string Shell,
    [In, Required] sint32 DefaultAction
);
```

## Parameters

<a href="" id="shell"></a>*Shell*
\[in, required\] The application or executable that Shell Launcher starts as the shell.

<a href="" id="defaultaction"></a>*DefaultAction*
\[in, required\] The default action that Shell Launcher takes when the *Shell* application exits.

The possible actions are defined in the following table:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>0</p></td>
<td><p>Restart the shell.</p></td>
</tr>
<tr class="even">
<td><p>1</p></td>
<td><p>Restart the device.</p></td>
</tr>
<tr class="odd">
<td><p>2</p></td>
<td><p>Shut down the device.</p></td>
</tr>
<tr class="even">
<td><p>3</p></td>
<td><p>Do nothing.</p></td>
</tr>
</tbody>
</table>

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

Shell Launcher uses the default configuration when the security identifier (SID) of the user who is currently signed in does not match any custom defined Shell Launcher configurations.

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