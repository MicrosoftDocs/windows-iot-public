---
title: WEKF\_Scancode.Add
description: WEKF\_Scancode.Add
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: cb5ea693-e871-4338-957a-f78f87a932ba
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# WEKF\_Scancode.Add

This method adds a new custom scan code combination and enables Keyboard Filter to block the new combination.

## Syntax

```powershell
[Static] uint32 Add(
    [In] string Modifiers, 
    [In] uint16 Scancode
);
```

## Parameters

<a href="" id="modifers"></a>*Modifers*
The modifier keys that are part of the key combination to block.

<a href="" id="scancode"></a>*Scancode*
The hardware scan code of the key to block.

## Return Value

Returns an HRESULT value that indicates [WMI non-error constant](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error constant](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

**WEKF\_Scancode.Add** creates a new **WEKF\_Scancode** object and sets the **Enabled** property of the new object to **true**.

If a **WEKF\_Scancode** object already exists with same *Modifiers* and *Scancode* properties, then **WEKF\_Scancode.Add** returns an error code and does not create a new object or modify any properties of the existing object. If the existing **WEKF\_Scancode** object has the **Enabled** property set to **false**, Keyboard Filter does not block the scan code.

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