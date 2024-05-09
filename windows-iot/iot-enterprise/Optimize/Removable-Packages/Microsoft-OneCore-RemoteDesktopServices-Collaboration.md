---
title: Package - Remote Desktop Services
titleSuffix: Windows IoT Enterprise
author: TerryWarwick
ms.author: twarwick
ms.date: 05/22/2024
ms.topic: reference
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Remote Desktop Services
keywords: IoT Enterprise, removable packages, storage
---

# Remote Desktop Services

Applies to:  
✅ Windows 11 IoT Enterprise LTSC 2024  
⛔ Windows 10 IoT Enterprise LTSC 2021

## Package Description

Package: **[Microsoft-OneCore-RemoteDesktopServices-Collaboration** </br>  Terminal Services Collaboration feature and sharer APIs.

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-OneCore-RemoteDesktopServices-Collaboration /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-OneCore-RemoteDesktopServices-Collaboration /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-OneCore-RemoteDesktopServices-Collaboration /PackageName:@Package
   ````

## Package Details

### Package Size

| Release                             |   x64     |    ARM64    |
|-------------------------------------|:---------:|:-----------:|
| Windows 11 IoT Enterprise LTSC 2024 | 1,460 KB  | 2,526 KB    |

### File List

| File Name | Installed Location |
|-----------|--------------------|
| rdpsharercom.dll | %windir%\system32\rdpsharercom.dll |

## Related Content

- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview)
