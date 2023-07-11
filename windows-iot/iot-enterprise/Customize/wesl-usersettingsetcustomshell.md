---
title: WESL\_UserSetting.SetCustomShell
description: WESL\_UserSetting.SetCustomShell
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 09fa040b-0fa1-4886-bfdd-8614eead0da8
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# WESL\_UserSetting.SetCustomShell

This method configures Shell Launcher for a specific user or group, based on the security identifier (SID).

## Syntax

```powershell
[Static] uint32 SetCustomShell (
    [In, Required] string Sid,
    [In, Required] string Shell,
    [In] sint32 CustomReturnCodes[],
    [In] sint32 CustomReturnCodesAction[],
    [In] sint32 DefaultAction
);
```

## Parameters

<a href="" id="sid"></a>*Sid*
\[in, required\] A string containing the security identifier (SID) of the user or group that Shell Launcher is being configured for.

<a href="" id="shell"></a>*Shell*
\[in, required\] The application or executable that Shell Launcher starts as the shell.

<a href="" id="customreturncodes"></a>*CustomReturnCodes*
\[in\] An array of custom return codes that can be returned by the shell application.

<a href="" id="customreturncodesaction"></a>*CustomReturnCodesAction*
\[in\] An array of custom return code actions that determine the action that Shell Launcher takes when the shell application exits. The custom actions map to the array of *CustomReturnCodes*.

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

<a href="" id="defaultaction"></a>DefaultAction
\[In\] The default action that Shell Launcher takes when the shell application exits.

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

Shell Launcher uses the *CustomReturnCodes* and *CustomReturnCodesAction* arrays to determine the system behavior when the shell application exits, based on the return value of the shell application.

If the return value does not exist in *CustomReturnCodes*, or if the corresponding action defined in *CustomReturnCodesAction* is not a valid value, Shell Launcher uses *DefaultAction* to determine system behavior. If *DefaultAction* is not defined, or is not a valid value, Shell Launcher restarts the shell application.

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