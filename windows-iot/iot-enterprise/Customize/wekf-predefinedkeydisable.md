---
title: WEKF\_PredefinedKey.Disable
description: WEKF\_PredefinedKey.Disable
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 81a040b3-b845-4cb2-872f-68082b048316


ms.date: 05/02/2017
ms.topic: article


---
# WEKF\_PredefinedKey.Disable

Unblocks the specified predefined key combination.

## Syntax

```powershell
[Static] uint32 Disable(
    [In] string PredefinedKey
);
```

## Parameters

<a href="" id="predefinedkey"></a>*PredefinedKey*
\[in\] The predefined key combination to unblock. For a list of predefined keys, see [Predefined key combinations](predefined-key-combinations.md).

## Return Value

Returns an HRESULT value that indicates [WMI Non-error constant](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error constant](/windows/win32/wmisdk/wmi-error-constants).

## Requirements

| Windows Edition       | Supported |
|:----------------------|:----------|
| Windows 10 Home       | No        |
| Windows 10 Pro        | No        |
| Windows 10 Enterprise | Yes       |
| Windows 10 Education  | Yes       |

## Related topics

[WEKF\_PredefinedKey](wekf-predefinedkey.md)

[Keyboard Filter](keyboardfilter.md)