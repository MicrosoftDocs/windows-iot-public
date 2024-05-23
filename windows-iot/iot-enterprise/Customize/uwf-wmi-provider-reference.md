---
title: Unified Write Filter WMI provider reference
description: Unified Write Filter WMI provider reference
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: c214944f-637e-436c-96f9-6bc1bcd78602
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
ms.date: 05/20/2024
ms.topic: article


---
# Unified Write Filter WMI provider reference

To help protect physical storage media, you can use the WMI providers for Unified Write Filter (UWF) to configure UWF.

This section describes the WMI provider classes for UWF.

## In this section

| Classes | Description |
|---------|-------------|
| [UWF_ExcludedFile](uwf-excludedfile.md) | A container class that contains the files and folders that are currently in the file exclusion list for a volume protected by UWF.|
| [UWF_ExcludedRegistryKey](uwf-excludedregistrykey.md) | A container class that contains the registry keys that are currently in the registry key exclusion list for UWF. |
| [UWF_Filter](uwf-filter.md) | Enables or disables Unified Write Filter (UWF), resets configuration settings for UWF, and shuts down or restarts your device. |
| [UWF_Overlay](uwf-overlay.md) | Contains the current size of the UWF overlay and manages the critical and warning thresholds for the overlay size. |
| [UWF_OverlayConfig](uwf-overlayconfig.md) | Manages the configuration of the UWF overlay. |
| [UWF_OverlayFile](uwf-overlayfile.md) | Displays and configures global settings for the UWF overlay. You can modify the maximum size and the type of the UWF overlay. |
| [UWF_RegistryFilter](uwf-registryfilter.md) | Adds or removes registry exclusions from UWF filtering. |
| [UWF_Servicing](uwf-servicing.md) | Contains properties and methods that enable you to query and control UWF servicing mode. |
| [UWF_Volume](uwf-volume.md) | Manages a volume protected by UWF. |

> [!NOTE]
> We recommend setting the authentication level to PacketIntegrity or PacketPrivacy for remote clients when you connect to WMI providers under root\\standardcimv2\\embedded when using WMI scripts or applications. For more information about how to use authentication with WMI providers, see this [WMI Enhancements in Windows PowerShell 2.0 CTP](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730973(v=technet.10)) on TechNet.

## Requirements

| Windows Edition        | Supported |
|:-----------------------|:---------:|
| Windows Home           | No        |
| Windows Pro            | No        |
| Windows Enterprise     | Yes       |
| Windows Education      | Yes       |
| Windows IoT Enterprise | Yes       |

## Related topics

- [uwfmgr.exe](uwfmgrexe.md)
