---
title: Package - Media Features Optional Component
titleSuffix: Windows IoT Enterprise
author: TerryWarwick
ms.author: twarwick
ms.date: 04/29/2024
ms.topic: reference
ms.service: windows-iot
ms.subservice: iot
description: Removable Package Details for Microsoft-Winodws-MediaPlayback-OC
keywords: IoT Enterprise, removable packages, storage
---

# Media Features Optional Component

Applies to:  
✅ Windows 11 IoT Enterprise LTSC 2024  
✅ Windows 10 IoT Enterprise LTSC 2021 (19044.1741 or later)  

## Package Description

Package: **Microsoft-Windows-MediaPlayback-OC** </br> Controls availability of the "Media Features" and "Windows Media Player" options for the *Turn Windows features on or off* user experience in Control Panel.

> [!IMPORTANT]
>
> This feature is only supported on the Windows IoT Entrprise LTSC edition. If you choose to remove any of this package from Windows IoT Enterprise, you must ensure that your solution does not rely on functionality of the removed package. You cannot restore the package without a full reinstall of Windows IoT Enterprise LTSC.  
> For more information, see [Removable Packages System Requirements](../Removable-Packages.md#system-requirements).

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

These packages collectively provide the functionality represented by the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture). There are dependencies between each of these packages. If you elect to remove a subset of these packages, you must thoroughly test your scenarios to ensure that your customers don't encounter an issue with missing dependencies.

- [Microsoft-Media-Foundation](Microsoft-Media-Foundation.md)
- [Microsoft-Windows-Media-Format](Microsoft-Windows-Media-Format.md)
- [Microsoft-Windows-Media-Streaming](Microsoft-Windows-Media-Streaming.md)
- [Microsoft-Windows-MediaPlayback-OC](Microsoft-Windows-MediaPlayback-OC.md)
- [Microsoft-Windows-Portable-Devices](Microsoft-Windows-Portable-Devices.md)
- [Microsoft-Windows-WebcamExperience](Microsoft-Windows-WebcamExperience.md)
- [Microsoft-Windows-WinSATMediaFiles](Microsoft-Windows-WinSATMediaFiles.md)

## Package Details

### Package Size

| Release                             |   x64     |    ARM64    |
|-------------------------------------|:---------:|:-----------:|
| Windows 11 IoT Enterprise LTSC 2024 | 0 KB      | 0 KB        |
| Windows 10 IoT Enterprise LTSC 2021 | 0 KB      | 0 KB        |

### File List

| File Name | Installed Location |
|-----------|--------------------|
|    N/A    |  No files associated with this package   |

## More Resources

- [Removable Packages](../Removable-Packages.md)
- [Device Optimization Overview](../Overview.md)
