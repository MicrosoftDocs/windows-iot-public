---
title: Package - Media Features Optional Component
author: twarwick
ms.author: twarwick
ms.date: 03/30/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Winodws-MediaPlayback-OC
keywords: IoT Enterprise, removable packages, storage
---

# Media Features Optional Component

| Applies to                          |  Version            |
|:------------------------------------|:--------------------|
| Windows 10 IoT Enterprise LTSC 2021 | 19044.1741 or later |

## Description

Controls availability of the "Media Features" and "Windows Media Player" options for the *Turn Windows features on or off* user experience in Control Panel.  Removing this package will remove these options from *Turn Windows features on or off*.

**Package Name:** Microsoft-Windows-MediaPlayback-OC

**Size:** Approximately 0 KB

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-MediaPlayback-OC /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-Windows-MediaPlayback-OC /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Windows-MediaPlayback-OC /PackageName:@Package
   ````

## Related Packages

These packages collectively provide the functionality represented by the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture).  There are dependencies between each of these packages.  If you elect to remove a subset of these packages, it is recommended that you thoroughly test your scenarios to ensure that your customers do not encounter the interaction between the packages you retain and the packages that you remove.

- [Microsoft-Media-Foundation](/windows/iot/iot-enterprise/optimize/removable-packages/Microsoft-Media-Foundation)
- [Microsoft-Windows-Media-Format](/windows/iot/iot-enterprise/optimize/removable-packages/Microsoft-Windows-Media-Format)
- [Microsoft-Windows-Media-Streaming](/windows/iot/iot-enterprise/optimize/removable-packages/Microsoft-Windows-Media-Streaming)
- [Microsoft-Windows-MediaPlayback-OC](/windows/iot/iot-enterprise/optimize/removable-packages/Microsoft-Windows-MediaPlayback-OC)
- [Microsoft-Windows-Portable-Devices](/windows/iot/iot-enterprise/optimize/removable-packages/Microsoft-Windows-Portable-Devices)
- [Microsoft-Windows-WebcamExperience](/windows/iot/iot-enterprise/optimize/removable-packages/Microsoft-Windows-WebcamExperience)
- [Microsoft-Windows-WinSATMediaFiles](/windows/iot/iot-enterprise/optimize/removable-packages/Microsoft-Windows-WinSATMediaFiles)

## File List

| File Name | Installed Location |
|-----------|--------------------|
|    N/A    |  No files associated with this package   |

## More Resources

- [Removable Packages](/windows/iot/iot-enterprise/optimize/Removable-Packages)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/optimize/Reduce-Disk-Footprint)
- [Device Optimization Overview](/windows/iot/iot-enterprise/optimize/Overview)
