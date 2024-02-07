---
title: Package - MobilePC Client
author: twarwick
ms.author: twarwick
ms.date: 12/20/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for MobilePC Client
keywords: IoT Enterprise, removable packages, storage
---

# MobilePC Client

> [!WARNING]
> THIS IS AN IN-PROGRESS ROUGH DRAFT. The wording and feature list may change before publishing.

Applies to:  
✅ Windows 11 IoT Enterprise LTSC 2024  
⛔ Windows 10 IoT Enterprise LTSC 2021

## Package Description

Package: **Microsoft-Windows-MobilePC-Client-Basic** </br>  `Add Description Here`

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-MobilePC-Client-Basic /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-Windows-MobilePC-Client-Basic /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Windows-MobilePC-Client-Basic /PackageName:@Package
   ````

## Package Details

### Package Size

| Release                             |   x64     |    ARM64    |
|-------------------------------------|:---------:|:-----------:|
| Windows 11 IoT Enterprise LTSC 2024 | 823 KB    | 797 KB      |

### File List

| File Name | Installed Location |
|-----------|--------------------|
| mblctr.exe | %windir%\system32\mblctr.exe |
| mblctr.mof | %windir%\system32\wbem\mblctr.mof |

## More Resources

- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview)
