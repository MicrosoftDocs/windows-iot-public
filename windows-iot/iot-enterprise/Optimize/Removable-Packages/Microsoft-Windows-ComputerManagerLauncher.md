---
title: Package - Computer Manager Launcher
titleSuffix: Windows IoT Enterprise
author: TerryWarwick
ms.author: twarwick
ms.date: 04/29/2024
ms.topic: reference
ms.service: windows-iot
ms.subservice: iot
description: Removable Package Details for Computer Manager Launcher
keywords: IoT Enterprise, removable packages, storage
---

# Computer Manager Launcher

Applies to:  
✅ Windows 11 IoT Enterprise LTSC 2024  
⛔ Windows 10 IoT Enterprise LTSC 2021

## Package Description

Package: **Microsoft-Windows-ComputerManagerLauncher** </br>  Computer Management App and Computer Management Snap-in for the Microsoft Management Console (MMC). For more information, see [What is Microsoft Management Console?](/troubleshoot/windows-server/system-management-components/what-is-microsoft-management-console).

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-ComputerManagerLauncher /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-Windows-ComputerManagerLauncher /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Windows-ComputerManagerLauncher /PackageName:@Package
   ````

## Package Details

### Package Size

| Release                             |   x64     |    ARM64    |
|-------------------------------------|:---------:|:-----------:|
| Windows 11 IoT Enterprise LTSC 2024 | 483 KB    | 610 KB      |

### File List

| File Name | Installed Location |
|-----------|--------------------|
| compmgmt.msc | %windir%\system32\compmgmt.msc |
| mycomput.dll | %windir%\system32\mycomput.dll |
| mycomput.dll.mun | %windir%\systemresources\mycomput.dll.mun |
| compmgmtlauncher.exe | %windir%\system32\compmgmtlauncher.exe |
| computer&nbsp;management.lnk | %programdata%\microsoft\windows\start menu\programs\administrative tools\computer management.lnk |

## More Resources

- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview)
