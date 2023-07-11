---
title: WEKF\_Scancode.Remove
description: WEKF\_Scancode.Remove
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 86185501-edc3-4c1d-be0b-5621c64f9540
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# WEKF\_Scancode.Remove

This method removes a custom scan code key combination, causing Keyboard Filter to stop blocking the removed combination.

## Syntax

```powershell
[Static] uint32 Remove(
    [In] string Modifiers,
    [In] uint16 Scancode
);
```

## Parameters

<a href="" id="modifiers"></a>*Modifiers*
The modifier keys of the combination to remove.

<a href="" id="scancode"></a>*Scancode*
The scan code of the combination to remove.

## Return Value

Returns an HRESULT value that indicates [WMI non-error constant](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error constant](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

**WEKF\_Scancode.Remove** removes an existing **WEKF\_Scancode** object. If the object does not exist, **WEKF\_Scancode.Remove** returns an error with the value 0x8007007B.

Because this method is static, you cannot call it on an object instance, but must instead call it at the class level.

## Requirements

| Windows Edition       | Supported |
|:----------------------|:----------|
| Windows 10 Home       | No        |
| Windows 10 Pro        | No        |
| Windows 10 Enterprise | Yes       |
| Windows 10 Education  | Yes       |

## Related topics

[WEKF\_Scancode](wekf-scancode.md)

[Keyboard Filter](keyboardfilter.md)