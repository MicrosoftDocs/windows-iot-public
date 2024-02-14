---
title: Package - SD Port
titleSuffix: Windows IoT Enterprise
author: twarwick
ms.author: twarwick
ms.date: 03/30/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for SD
keywords: IoT Enterprise, removable packages, storage
---

# SD

> [!WARNING]
> THIS IS AN IN-PROGRESS ROUGH DRAFT. The wording and feature list may change before publishing.

Applies to:  
✅ Windows 11 IoT Enterprise LTSC 2024  
⛔ Windows 10 IoT Enterprise LTSC 2021

## Package Description

Package: **Microsoft-OneCore-SD** </br> SD Port and Dump SD Port.

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-OneCore-SD /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-OneCore-SD /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-OneCore-SD /PackageName:@Package
   ````

## Package Details

### Package Size

| Release                             |   x64     |    ARM64    |
|-------------------------------------|:---------:|:-----------:|
| Windows 11 IoT Enterprise LTSC 2024 | 928 KB    | 764 KB      |

### File List

| File Name | Installed Location |
|-----------|--------------------|
| sdbus.inf | %windir%\system32\driverstore\filerepository\sdbus.inf_amd64_3ef198d9aa8cd1aa\sdbus.inf |
| sdstor.inf | %windir%\system32\driverstore\filerepository\sdstor.inf_amd64_37a216051ca61bf2\sdstor.inf |
| dumpsd.sys | %windir%\system32\drivers\dumpsd.sys |
| dumpsdport.sys | %windir%\system32\drivers\dumpsdport.sys |
| sdbus.sys | %windir%\system32\drivers\sdbus.sys |
| sdport.sys | %windir%\system32\drivers\sdport.sys |
| sdstor.sys | %windir%\system32\drivers\sdstor.sys |

## More Resources

- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview)
