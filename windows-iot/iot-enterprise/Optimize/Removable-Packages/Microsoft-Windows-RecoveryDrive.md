---
title: Package - Recovery Drive
author: twarwick
ms.author: twarwick
ms.date: 03/30/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Windows-RecoveryDrive
keywords: IoT Enterprise, removable packages, storage
---

# Recovery Drive

| Applies to                          |  Version            |
|:------------------------------------|:--------------------|
| Windows 10 IoT Enterprise LTSC 2021 | 19044.1741 or later |

## Description

Create a recovery drive user experience invoked from Control Panel - Recovery

**Package Name:** Microsoft-Windows-RecoveryDrive

**Size:** Approximately 1,041 KB

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-RecoveryDrive /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-Windows-RecoveryDrive /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Windows-RecoveryDrive /PackageName:@Package
   ````

## File List

| File Name | Installed Location |
|-----------|--------------------|
| recoverydrive.lnk | %programdata%\microsoft\windows\start menu\programs\administrative tools\recoverydrive.lnk |
| recovery.dll      | %windir%\system32\recovery.dll |
| recoverydrive.exe | %windir%\system32\recoverydrive.exe |

## More Resources

- [Removable Packages](/windows/iot/iot-enterprise/optimize/Removable-Packages.md)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/optimize/Reduce-Disk-Footprint.md)
- [Device Optimization Overview](/windows/iot/iot-enterprise/optimize/Overview.md)
