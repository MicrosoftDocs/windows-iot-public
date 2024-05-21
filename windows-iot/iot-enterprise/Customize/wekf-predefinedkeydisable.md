---
title: WEKF_PredefinedKey.Disable
description: WEKF_PredefinedKey.Disable
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 81a040b3-b845-4cb2-872f-68082b048316
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
ms.date: 05/20/2024
ms.topic: article


---
# WEKF_PredefinedKey.Disable

Unblocks the specified predefined key combination.

## Syntax

```powershell
[Static] uint32 Disable(
    [In] string PredefinedKey
);
```

## Parameters

**PredefinedKey**</br>\[in\] The predefined key combination to unblock. For a list of predefined keys, see [Predefined key combinations](predefined-key-combinations.md).

## Return Value

Returns an HRESULT value that indicates [WMI Non-error constant](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error constant](/windows/win32/wmisdk/wmi-error-constants).

## Requirements

| Windows Edition        | Supported |
|:-----------------------|:---------:|
| Windows Home           | No        |
| Windows Pro            | No        |
| Windows Enterprise     | Yes       |
| Windows Education      | Yes       |
| Windows IoT Enterprise | Yes       |

## Related topics

- [WEKF_PredefinedKey](wekf-predefinedkey.md)
- [Keyboard Filter](keyboardfilter.md)
