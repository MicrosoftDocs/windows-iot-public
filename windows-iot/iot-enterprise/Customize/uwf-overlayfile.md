---
title: UWF_OverlayFile
description: UWF_OverlayFile
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 8b258f33-2cf9-46c8-8a66-efa567d63899
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# UWF_OverlayFile

Contains a file that is currently in the overlay for a volume protected by Unified Write Filter (UWF).

## Syntax

```powershell
class UWF_OverlayFile {
    [read] string FileName;
    [read] UInt64 FileSize;
};
```

## Members

The following table lists any properties that belong to this class.

### Properties

| Property | Data&nbsp;type | Qualifier | Description |
|----------|----------------|-----------|-------------|
| FileName | string | [read] | The name of the file in the file overlay. |
| FileSize | UInt64 | [read] | The size of the file in the file overlay. |

### Remarks

You cannot use the **UWF_ OverlayFile** class directly to get overlay files. You must use the **UWF_Overlay.GetOverlayFiles** method to retrieve **UWF_ OverlayFile** objects.

For more information about specific limitations and conditions when using the **GetOverlayFiles** method, see the **Remarks** section in the [UWF_Overlay.GetOverlayFiles](uwf-overlaygetoverlayfiles.md) topic in the UWF WMI provider technical reference.

## Requirements

| Windows Edition       | Supported |
|:----------------------|:----------|
| Windows 10/11 Home       | No        |
| Windows 10/11 Pro        | No        |
| Windows 10/11 Enterprise | Yes       |
| Windows 10/11 Education  | Yes       |
| Windows 10/11 IoT Enterprise | Yes |

## Related topics

- [Unified Write Filter WMI provider reference](uwf-wmi-provider-reference.md)
- [Unified Write Filter](unified-write-filter.md)
