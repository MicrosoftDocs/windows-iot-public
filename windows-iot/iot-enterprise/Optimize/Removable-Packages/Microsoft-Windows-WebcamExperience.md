---
title: Package - Webcam Experience
author: twarwick
ms.author: twarwick
ms.date: 03/30/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Windows-WebCamExperiece
keywords: IoT Enterprise, removable packages, storage
---

# Webcam Experience

| Applies to                          |  Version            |
|:------------------------------------|:--------------------|
| Windows 10 IoT Enterprise LTSC 2021 | 19044.1741 or later |

## Description

A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing webcam user experience.

**Package Name:** Microsoft-Windows-WebCamExperience

**Size:** Approximately 1,394 KB

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-WebCamExperience /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-Windows-WebCamExperience /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Windows-WebCamExperience /PackageName:@Package
   ````

## Related Packages

These packages collectively provide the functionality represented by the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture).  There are dependencies between each of these packages.  If you elect to remove a subset of these packages, it is recommended that you thoroughly test your scenarios to ensure that your customers do not encounter the interaction between the packages you retain and the packages that you remove.

- [Microsoft-Media-Foundation](Microsoft-Media-Foundation.md)
- [Microsoft-Windows-Media-Format](Microsoft-Windows-Media-Format.md)
- [Microsoft-Windows-Media-Streaming](Microsoft-Windows-Media-Streaming.md)
- [Microsoft-Windows-MediaPlayback-OC](Microsoft-Windows-MediaPlayback-OC.md)
- [Microsoft-Windows-Portable-Devices](Microsoft-Windows-Portable-Devices.md)
- [Microsoft-Windows-WebcamExperience](Microsoft-Windows-WebcamExperience.md)
- [Microsoft-Windows-WinSATMediaFiles](Microsoft-Windows-WinSATMediaFiles.md)

## File List

| File Name | Installed Location |
|-----------|--------------------|
| camerasettingsuihost.exe    | %windir%\system32\camerasettingsuihost.exe |
| webcamui.dll                | %windir%\system32\webcamui.dll

## More Resources

- [Removable Packages]../Removable-Packages.md)
- [Reduce Disk Footprint]../Reduce-Disk-Footprint.md)
- [Device Optimization Overview]../Overview.md)
