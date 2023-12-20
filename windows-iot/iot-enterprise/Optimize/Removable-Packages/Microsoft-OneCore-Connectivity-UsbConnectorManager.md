---
title: Package - USB Connector Manager
author: twarwick
ms.author: twarwick
ms.date: 03/30/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for USB Connector Manager
keywords: IoT Enterprise, removable packages, storage
---

# USB Connector Manager

> [!WARNING]
> THIS IS AN IN-PROGRESS ROUGH DRAFT. The wording and feature list may change before publishing.

Applies to:  
✅ Windows 11 IoT Enterprise LTSC 2024  
⛔ Windows 10 IoT Enterprise LTSC 2021

## Package Description

Package: **Microsoft-OneCore-Connectivity-UsbConnectorManager** </br> `Add Description Here`

| Release                             |   x64     |    ARM64    |
|-------------------------------------|:---------:|:-----------:|
| Windows 11 IoT Enterprise LTSC 2024 | 1,111 KB  | 853 KB      |


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

## File List

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

## More Resources

- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview)
