---
title: WESL_UserSetting.GetCustomShell
description: WESL_UserSetting.GetCustomShell
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 7bd2b50c-d566-4688-8fbd-1ea0197c1cde
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# WESL_UserSetting.GetCustomShell

This method retrieves the Shell Launcher configuration for a specific user or group, based on the security identifier (SID).

## Syntax

```powershell
[Static] uint32 GetCustomShell (
    [In, Required] string Sid,
    [Out, Required] string Shell,
    [Out, Required] sint32 CustomReturnCodes[],
    [Out, Required] sint32 CustomReturnCodesAction[],
    [Out, Required] sint32 DefaultAction
);
```

## Parameters

**Sid**</br>\[in, required\] A string containing the security identifier (SID) of the user or group that Shell Launcher is configured for.

**Shell**</br>\[out, required\] The application or executable that Shell Launcher starts as the shell.

**CustomReturnCodes**</br>\[out, required\] An array of custom return codes returned by the shell application.

**CustomReturnCodesAction**</br>\[out, required\] An array of custom return code actions that determine the action that Shell Launcher takes when the shell application exits. The custom actions map to the array of *CustomReturnCodes*.

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
\[out, required\] The default action that Shell Launcher takes when the shell application exits.

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

Shell Launcher uses the *CustomReturnCodes* and *CustomReturnCodesAction* arrays to determine the system behavior when the shell application exits, based on the return value of the application.

If the return value does not exist in *CustomReturnCodes*, or if the corresponding action defined in *CustomReturnCodesAction* is not a valid value, Shell Launcher uses *DefaultAction* to determine system behavior. If *DefaultAction* is not defined, or is not a valid value, Shell Launcher restarts the shell application.

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