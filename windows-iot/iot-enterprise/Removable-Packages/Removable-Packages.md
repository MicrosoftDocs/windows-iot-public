---
title: Removable Packages
author: twarwick
ms.author: twarwick
ms.date: 12/7/2022
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Windows IoT Enterprise feature to assist with reducing disk footprint
keywords: IoT Enterprise, removable packages, storage
---

# Removable Packages
## Overview
In addition to the image customizability provided by [Enable or Disable Windows Features using DISM](https://learn.microsoft.com/windows-hardware/manufacture/desktop/enable-or-disable-windows-features-using-dism) and [Features on Demand](https://learn.microsoft.com/windows-hardware/manufacture/desktop/features-on-demand-v2--capabilities), Windows IoT Enterprise LTSC allows a device builder to remove additional packages from the [Windows Component Store](https://learn.microsoft.com/windows-hardware/manufacture/desktop/manage-the-component-store) using the desktop manufacturing process to [Modify a Windows image](/windows-hardware/manufacture/desktop/modify-an-image).  A device maker may use either [Online servicing (audit mode)](/windows-hardware/manufacture/desktop/audit-mode-overview) or [Offline Servicing](/windows-hardware/manufacture/desktop/mount-and-modify-a-windows-image-using-dism) methods to remove packages from Windows IoT Enterprise LTSC using the command line instuctions below..
> [!Important]
>
>If you choose to remove any of these packages from Windows IoT Enterprise, you must ensure that your  solution does not rely on functionality of the removed package(s). You cannot restore the package without a full reinstall of Windows IoT Enteprise LTSC.

## System Requirements
This feature is supported on:
- Windows 10 IoT Enterprise LTSC 2021 (build 19044.1741) or later

> [!Note]
>
> To use this feature with Windows 10 IoT Enterprise LTSC 2021, you must first install an servicing update.  
> - Option 1: Go to Start > Settings > Windows Update then check for and apply all available updates before proceeding.
> - Option 2: Manually download and install  [KB5014023](https://support.microsoft.com/topic/june-2-2022-kb5014023-os-builds-19042-1741-19043-1741-and-19044-1741-preview-65ac6a5d-439a-4e88-b431-a5e2d4e2516a) or any of its successors.
 
 ## Removing Packages

Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) to remove a single package from your Windows image.

```powershell
Dism.exe [/Online | /Image:<image path>] /LogPath:<logfile> /NoRestart /Disable-Feature /FeatureName:<package name> /PackageName:@Package
```

Example: Use DISM.exe to remove Windows calculator  
```powershell
Dism.exe /Online /LogPath:.\remove_win32calc.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-win32calc /PackageName:@Package
````

Example: Use DISM.exe to remove Windows calculator from an **Offline image**  
```powershell
Dism.exe /Image:c:\offline /LogPath:.\remove_win32calc.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-win32calc /PackageName:@Package
````
 
## Package Reference

Below is a list of all packages that can be removed from Windows IoT Enterprise LTSC removable components along with the specific LTSC version that supports their removal. 

| #| Package Name  | Description  |
|--:|:-------------|--------------|
|  1 |[Microsoft-Windows-AppManagement-UEV](./Removable-Packages-Details/Removable-Package-AppManagement_UEV.md) | [User Experience Virtualization](https://learn.microsoft.com/windows/configuration/ue-v/uev-for-windows) |
|  2 |[Microsoft-Windows-BootEnvironment-Dvd](./Removable-Packages-Details/Removable-Package-BootEnvironment_Dvd.md) | Boot from DVD |
|  3 |[Microsoft-Windows-Printing-PremiumTools](./Removable-Packages-Details/Removable-Package-Printing_PremiumTools.md) | <span style="color:red"> Need to author a description. </span> |
|  4 |[Microsoft-Windows-Shell-Wallpaper-Common](./Removable-Packages-Details/Removable-Package-Shell_Wallpaper.md) | In-box wallpaper images | 
|  5 |[Microsoft-Windows-win32calc](./Removable-Packages-Details/Removable-Package-win32calc.md) | Calculator app |

| #| Package Name  | Description  |
|--:|:-------------|--------------|
| **Rollup** |**[Microsoft-Windows-Desktop-Shared-Removable](./Removable-Packages-Details/Removable-Package-Desktop_SharedPackages.md)** | <span style="color:red"> Need to author a description. </span> |
|  1 | - [LanguageFeatures-WordBreaking-Common-legacy](./Removable-Packages-Details/Removable-Package-LanguageFeatures_WordBreaking_Common_Legacy.md) | <span style="color:red"> Need to author a description. </span>  |
|  2 | - [Microsoft-OneCore-Fonts-DesktopFonts-NonLeanSupplement](./Removable-Packages-Details/Removable-Package-Fonts_DesktopFonts_NonLeanSupplement.md) | <span style="color:red"> Need to author a description. </span> |
|  3 | - [Microsoft-Windows-BioEnrollment-UX](./Removable-Packages-Details/Removable-Package-BioEnrollment_UX.md) | [Windows Hello](https://learn.microsoft.com/windows-hardware/design/device-experiences/windows-hello) |
|  4 | - [Microsoft-Windows-Printer-Drivers](./Removable-Packages-Details/Removable-Package-Printer_Drivers.md) | In-box printer drivers  |
|  5 | - [Microsoft-Windows-RecoveryDrive](./Removable-Packages-Details/Removable-Package-RecoveryDrive.md) | <span style="color:red"> Need to author a description. </span> |
|  6 | - [Microsoft-Windows-ScreenSavers-3D](./Removable-Packages-Details/Removable-Package-ScreenSavers.md) | In-box screensavers  |
|  7 | - [Microsoft-Windows-SensorDataService](./Removable-Packages-Details/Removable-Package-SensorDataService.md) | <span style="color:red"> Need to author a description. </span> |
|  8 | - [Microsoft-Windows-ShellOptions](./Removable-Packages-Details/Removable-Package-ShellOptions.md) | <span style="color:red"> Need to author a description. </span> 

| #| Package Name  | Description  |
|--:|:-------------|--------------|
|  **Rollup** |**[Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md)** |  <span style="color:red"> Need to author a description. </span> |
|  1 | - [Microsoft-Media-Foundation]() | |
|  2 | - [Microsoft-OneCore-Multimedia-CastingCommon]() | |
|  3 | - [Microsoft-OneCore-Multimedia-CastingReceiver-Media]() | |
|  4 | - [Microsoft-OneCore-Multimedia-CastingTransmitter-Media]() | |
|  5 | - [Microsoft-OneCore-Multimedia-MFPMP]() | |
|  6 | - [Microsoft-Windows-Media-Format]() | |
|  7 | - [Microsoft-Windows-Media-Format-merged]() | |
|  8 | - [Microsoft-Windows-MediaPlayback-OC]() | |
|  9 | - [Microsoft-Windows-Media-Streaming]() | |
| 10 | - [Microsoft-Windows-Media-Streaming-merged]() | |
| 11 | - [Microsoft-Windows-Multimedia-MF]() | |
| 12 | - [Microsoft-Windows-Multimedia-MF-merged]() | |
| 13 | - [Microsoft-Windows-Multimedia-RestrictedCodecs]() | |
| 14 | - [Microsoft-Windows-Multimedia-RestrictedCodecs-merged]() | |
| 15 | - [Microsoft-Windows-Multimedia-WMPDMC]() | |
| 16 | - [Microsoft-Windows-Portable-Devices]() | |
| 17 | - [Microsoft-Windows-Portable-Devices-merged]() | |
| 18 | - [Microsoft-Windows-WebcamExperience]() | |
| 19 | - [Microsoft-Windows-WinSATMediaFiles]() | |
| 20 | - [Microsoft-Windows-WPD-LegacyWmdmFeature-Feature]() | |
| 21 | - [Microsoft-Windows-WPD-UltimatePortableDeviceFeature-Feature]() | |
| 22 | - [Multimedia-MFCore]() | |
| 23 | - [Multimedia-MFCore-WCOSHeadless]() | |
| 24 | - [Multimedia-MFCore-WCOSMinusHeadless]() | |
| 25 | - [Multimedia-RestrictedCodecsCore]() | |
| 26 | - [Multimedia-RestrictedCodecsCore-Full]() | |
| 27 | - [Multimedia-RestrictedCodecsCore-WCOSHeadless]() | |
| 28 | - [Multimedia-RestrictedCodecsCore-WCOSMinusHeadless]() | |
| 29 | - [Multimedia-RestrictedCodecsExt]() | |
| 30 | - [Multimedia-RestrictedCodecsExt-WCOSHeadless]() | |
| 31 | - [Multimedia-RestrictedCodecsExt-WCOSMinusHeadless]() | |


## Additional Resources
* [Removable Packages Blog](https://aka.ms/RemovablePackagesBlog)
* [Removable Packages Script](https://aka.ms/RemovablePackagesScript)
* [Reduce Disk Footprint](/windows/iot/iot-enterprise/optimize-your-device/reduce-disk-footprint)
