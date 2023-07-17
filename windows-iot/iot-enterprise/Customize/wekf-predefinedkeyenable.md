---
title: WEKF_PredefinedKey.Enable
description: WEKF_PredefinedKey.Enable
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 4ea8c6c4-3bf6-475f-b9e1-38e1a971eda5
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# WEKF_PredefinedKey.Enable

This method blocks the specified predefined key combination.

## Syntax

```powershell
[Static] uint32 Enable(
    [In] string PredefinedKey
);
```

## Parameters

**PredefinedKey**</br>The predefined key combination to block. For a list of predefined keys, see [Predefined key combinations](predefined-key-combinations.md).

## Return Value

Returns an HRESULT value that indicates [WMI non-error constant](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error constant](/windows/win32/wmisdk/wmi-error-constants).

## Requirements

| Windows Edition       | Supported |
|:----------------------|:----------|
| Windows 10 Home       | No        |
| Windows 10 Pro        | No        |
| Windows 10 Enterprise | Yes       |
| Windows 10 Education  | Yes       |

## Related topics

- [WEKF_PredefinedKey](wekf-predefinedkey.md)
- [Keyboard Filter](keyboardfilter.md)
