---
title: WEKF_Scancode.Add
description: WEKF_Scancode.Add
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: cb5ea693-e871-4338-957a-f78f87a932ba
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
ms.date: 05/20/2024
ms.topic: article


---
# WEKF_Scancode.Add

This method adds a new custom scan code combination and enables Keyboard Filter to block the new combination.

## Syntax

```powershell
[Static] uint32 Add(
    [In] string Modifiers, 
    [In] uint16 Scancode
);
```

## Parameters

**Modifers**</br>The modifier keys that are part of the key combination to block.

**Scancode**</br>The hardware scan code of the key to block.

## Return Value

Returns an HRESULT value that indicates [WMI non-error constant](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error constant](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

**WEKF_Scancode.Add** creates a new **WEKF_Scancode** object and sets the **Enabled** property of the new object to **true**.

If a **WEKF_Scancode** object already exists with same *Modifiers* and *Scancode* properties, then **WEKF_Scancode.Add** returns an error code and does not create a new object or modify any properties of the existing object. If the existing **WEKF_Scancode** object has the **Enabled** property set to **false**, Keyboard Filter does not block the scan code.

## Requirements

| Windows Edition        | Supported |
|:-----------------------|:---------:|
| Windows Home           | No        |
| Windows Pro            | No        |
| Windows Enterprise     | Yes       |
| Windows Education      | Yes       |
| Windows IoT Enterprise | Yes       |

## Related topics

- [WEKF_Scancode](wekf-scancode.md)
- [Keyboard Filter](keyboardfilter.md)
