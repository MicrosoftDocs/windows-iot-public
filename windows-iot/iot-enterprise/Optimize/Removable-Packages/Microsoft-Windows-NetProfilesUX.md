---
title: Package - Net Profiles UX
titleSuffix: Windows IoT Enterprise
author: TerryWarwick
ms.author: twarwick
ms.date: 02/12/2024
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Removable Package Details for Net Orifukes UX
keywords: IoT Enterprise, removable packages, storage
---

# Net Profiles UX

> [!WARNING]
> THIS IS AN IN-PROGRESS ROUGH DRAFT. The wording and feature list may change before publishing.

Applies to:  
✅ Windows 11 IoT Enterprise LTSC 2024  
⛔ Windows 10 IoT Enterprise LTSC 2021

## Package Description

Package: **Microsoft-Windows-NetProfilesUX** </br>  Network and Sharing Center Contol Panel application.

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-NetProfilesUX /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-Windows-NetProfilesUX /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Windows-NetProfilesUX /PackageName:@Package
   ````

## Package Details

### Package Size

| Release                             |   x64     |    ARM64    |
|-------------------------------------|:---------:|:-----------:|
| Windows 11 IoT Enterprise LTSC 2024 | 899 KB    | 1,106 KB    |

### File List

| File Name | Installed Location |
|-----------|--------------------|
| netcenter.dll | %windir%\system32\netcenter.dll |
| netcenter.dll.mun | %windir%\systemresources\netcenter.dll.mun |

## More Resources

- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview)
