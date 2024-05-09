---
title: Package - USB Connector Manager
titleSuffix: Windows IoT Enterprise
author: TerryWarwick
ms.author: twarwick
ms.date: 04/29/2024
ms.topic: reference
ms.service: windows-iot
ms.subservice: iot
description: Removable Package Details for USB Connector Manager
keywords: IoT Enterprise, removable packages, storage
---

# USB Connector Manager

Applies to:  
✅ Windows 11 IoT Enterprise LTSC 2024  
⛔ Windows 10 IoT Enterprise LTSC 2021

## Package Description

Package: **Microsoft-OneCore-Connectivity-UsbConnectorManager** </br> USB Connection Manager (UCM), USB Type-C port controller interface (TCPCI), and USB Type-C connector system software interface (UCSI) class extensions,  USB Connector, and USB Policy Manager APIs. For more information, see [USB Type-C connector system software interface (UCSI) driver](/windows-hardware/drivers/usbcon/ucsi), [Write a USB Type-C port controller driver](/windows-hardware/drivers/usbcon/write-a-usb-type-c-port-controller-driver) and [Write a USB Type-connector driver](/windows-hardware/drivers/usbcon/bring-up-a-usb-type-c-connector-on-a-windows-system).

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-OneCore-Connectivity-UsbConnectorManager /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-OneCore-Connectivity-UsbConnectorManager /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-OneCore-Connectivity-UsbConnectorManager /PackageName:@Package
   ````

## Package Details

### Package Size

| Release                             |   x64     |    ARM64    |
|-------------------------------------|:---------:|:-----------:|
| Windows 11 IoT Enterprise LTSC 2024 | 1,103 KB  | 863 KB      |

### File List

| File Name | Installed Location |
|-----------|--------------------|
| ucmucsiacpiclient.inf | %windir%\system32\driverstore\filerepository\ucmucsiacpiclient.inf_amd64_ec9b4186b56641aa\ucmucsiacpiclient.inf |
| ucmcx.dll | %windir%\system32\drivers\umdf\ucmcx.dll |
| ucmcx.sys | %windir%\system32\drivers\ucmcx.sys |
| usbcapi.dll | %windir%\system32\usbcapi.dll |
| usbpmapi.dll | %windir%\system32\usbpmapi.dll |
| usbpmapi.sys | %windir%\system32\drivers\usbpmapi.sys |
| ucmtcpcicx.sys | %windir%\system32\drivers\ucmtcpcicx.sys |
| ucmucsiacpiclient.sys | %windir%\system32\drivers\ucmucsiacpiclient.sys |
| ucmucsicx.sys | %windir%\system32\drivers\ucmucsicx.sys |

## Related Content

- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview)
