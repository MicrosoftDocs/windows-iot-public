---
title: Package - USB Function Driver
author: twarwick
ms.author: twarwick
ms.date: 03/30/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for USB Function Driver
keywords: IoT Enterprise, removable packages, storage
---

# USB Function Driver

> [!WARNING]
> THIS IS AN IN-PROGRESS ROUGH DRAFT. The wording and feature list may change before publishing.

Applies to:  
✅ Windows 11 IoT Enterprise LTSC 2024  
⛔ Windows 10 IoT Enterprise LTSC 2021

## Package Description

Package: **Microsoft-OneCore-Connectivity-UsbFunction** </br>  `Add Description Here`

| Release                             |   x64     |    ARM64    |
|-------------------------------------|:---------:|:-----------:|
| Windows 11 IoT Enterprise LTSC 2024 | 747 KB    | 622 KB      |

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-OneCore-Connectivity-UsbFunction /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-OneCore-Connectivity-UsbFunction /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-OneCore-Connectivity-UsbFunction /PackageName:@Package
   ````

## File List

| File Name | Installed Location |
|-----------|--------------------|
| genericusbfn.inf | %windir%\system32\driverstore\filerepository\genericusbfn.inf_amd64_253b6957ba775622\genericusbfn.inf |
| ufxchipidea.inf | %windir%\system32\driverstore\filerepository\ufxchipidea.inf_amd64_1a8f9d49db4bf636\ufxchipidea.inf |
| ufxsynopsys.inf | %windir%\system32\driverstore\filerepository\ufxsynopsys.inf_amd64_4ed1fada2f2925e8\ufxsynopsys.inf |
| genericusbfn.sys | %windir%\system32\driverstore\filerepository\genericusbfn.inf_amd64_253b6957ba775622\genericusbfn.sys |
| ufx01000.sys | %windir%\system32\drivers\ufx01000.sys |
| ufxchipidea.sys | %windir%\system32\driverstore\filerepository\ufxchipidea.inf_amd64_1a8f9d49db4bf636\ufxchipidea.sys |
| ufxsynopsys.sys | %windir%\system32\drivers\ufxsynopsys.sys |


## More Resources

- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview)
