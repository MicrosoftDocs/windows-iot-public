---
title: WEKF_Scancode.Remove
description: WEKF_Scancode.Remove
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
# WEKF_Scancode.Remove

This method removes a custom scan code key combination, causing Keyboard Filter to stop blocking the removed combination.

## Syntax

```powershell
[Static] uint32 Remove(
    [In] string Modifiers,
    [In] uint16 Scancode
);
```

## Parameters

**Modifiers**</br>The modifier keys of the combination to remove.

**Scancode**</br>The scan code of the combination to remove.

## Return Value

Returns an HRESULT value that indicates [WMI non-error constant](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error constant](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

**WEKF_Scancode.Remove** removes an existing **WEKF_Scancode** object. If the object does not exist, **WEKF_Scancode.Remove** returns an error with the value 0x8007007B.

Because this method is static, you cannot call it on an object instance, but must instead call it at the class level.

## Requirements

| Windows Edition        | Supported |
|:-----------------------|:---------:|
| Windows Home           | No        |
| Windows Pro            | No        |
| Windows Enterprise     | Yes       |
| Windows Education      | Yes       |
| Windows IoT Enterprise | Yea       |

## Related topics

- [WEKF_Scancode](wekf-scancode.md)
- [Keyboard Filter](keyboardfilter.md)
