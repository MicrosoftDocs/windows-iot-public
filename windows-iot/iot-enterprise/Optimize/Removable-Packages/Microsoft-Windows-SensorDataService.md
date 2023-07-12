---
title: Package - Sensor Data Service
author: twarwick
ms.author: twarwick
ms.date: 03/30/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Windows-SensorDataService
keywords: IoT Enterprise, removable packages, storage
---

# Sensor Data Service

| Applies to                          |  Version            |
|:------------------------------------|:--------------------|
| Windows 10 IoT Enterprise LTSC 2021 | 19044.1741 or later |

## Description

A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) supporting data acquisition from various sensors.  Supports Windows Hello.

**Package Name:** Microsoft-Windows-SensorDataService

**Size:** Approximately 1,367 KB

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-SensorDataService /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-Windows-SensorDataService /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Windows-SensorDataService /PackageName:@Package
   ````

## File List

| File Name | Installed Location |
|-----------|--------------------|
| mediafoundation.defaultperceptionprovider.dll | %windir%\system32\mediafoundation.defaultperceptionprovider.dll |
| sensordataservice.exe                         | %windir%\system32\sensordataservice.exe |

## More Resources

- [Removable Packages](/windows/iot/iot-enterprise/optimize/Removable-Packages.md)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/optimize/Reduce-Disk-Footprint.md)
- [Device Optimization Overview](/windows/iot/iot-enterprise/optimize/Overview.md)
