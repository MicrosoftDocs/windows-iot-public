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

### Online Servicing (audit mode)
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Online``` command-line parammeter to remove a single package via online servicing (audit mode).

```powershell
Dism.exe /Online /LogPath:<logfile> /NoRestart /Disable-Feature /FeatureName:<package name> /PackageName:@Package
```

Example: Use DISM.exe to remove Windows calculator using online servicing (audit mode).
```powershell
Dism.exe /Online /LogPath:.\remove_win32calc.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-win32calc /PackageName:@Package
````
### Offline Servicing
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Image:<image path>``` command-line parameter to remove a single package via offline servicing.

```powershell
Dism.exe /Image:<image path> /LogPath:<logfile> /NoRestart /Disable-Feature /FeatureName:<package name> /PackageName:@Package
```

Example: Use DISM.exe to remove Windows calculator using offline servicing.
```powershell
Dism.exe /Image:c:\offline /LogPath:.\remove_win32calc.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-win32calc /PackageName:@Package
````
## Package Reference

Below is a list of all packages that can be removed from Windows IoT Enterprise LTSC removable components along with the specific LTSC version that supports their removal.   

>[!Note]
> 
>¹ Next to the number index in the table below denotes a rollup package that is collection of other packages.  This simplifies the removal of the collection as a whole as opposed to removing each package individually.

| Package Collection | Package Members  | Description  |
|:------------|:-|--------------|
| Individual | [Microsoft-Windows-AppManagement-UEV](./Removable-Packages-Details/Removable-Package-AppManagement_UEV.md) | [User Experience Virtualization](https://learn.microsoft.com/windows/configuration/ue-v/uev-for-windows) |
| Individual | [Microsoft-Windows-BootEnvironment-Dvd](./Removable-Packages-Details/Removable-Package-BootEnvironment_Dvd.md) | Boot from DVD |
| Individual | [Microsoft-Windows-Printing-PremiumTools](./Removable-Packages-Details/Removable-Package-Printing_PremiumTools.md) | Print services migration command-line tool printbrm.exe |
| Individual | [Microsoft-Windows-Shell-Wallpaper-Common](./Removable-Packages-Details/Removable-Package-Shell_Wallpaper.md) | Desktop wallpaper images | 
| Individual | [Microsoft-Windows-win32calc](./Removable-Packages-Details/Removable-Package-win32calc.md) | Calculator app |
| [Microsoft-Windows-Desktop-Shared-Removable](./Removable-Packages-Details/Removable-Package-Desktop_SharedPackages.md) | [LanguageFeatures-WordBreaking-Common-legacy](./Removable-Packages-Details/Removable-Package-LanguageFeatures_WordBreaking_Common_Legacy.md) | Legacy neutral word breaker, should only be needed in very rare app compat scenarios |
| [Microsoft-Windows-Desktop-Shared-Removable](./Removable-Packages-Details/Removable-Package-Desktop_SharedPackages.md) | [Microsoft-OneCore-Fonts-DesktopFonts-NonLeanSupplement](./Removable-Packages-Details/Removable-Package-Fonts_DesktopFonts_NonLeanSupplement.md) | Fonts: [Malgun Gothic](/typography/font-list/malgun-gothic), [Microsoft JhengHei](/typography/font-list/microsoft-jhenghei), [Microsoft YaHei](/typography/font-list/microsoft-yahei), [Yu Gothic](/typography/font-list/yu-gothic)   |
| [Microsoft-Windows-Desktop-Shared-Removable](./Removable-Packages-Details/Removable-Package-Desktop_SharedPackages.md) | [Microsoft-Windows-BioEnrollment-UX](./Removable-Packages-Details/Removable-Package-BioEnrollment_UX.md) | [Windows Hello](https://learn.microsoft.com/windows-hardware/design/device-experiences/windows-hello) |
| [Microsoft-Windows-Desktop-Shared-Removable](./Removable-Packages-Details/Removable-Package-Desktop_SharedPackages.md) | [Microsoft-Windows-Printer-Drivers](./Removable-Packages-Details/Removable-Package-Printer_Drivers.md) | Generic / Text Only, Generic IBM Graphics 9pin, Generic IBM Graphics 9pin wide, MS Publisher Color Printer, MS Publisher Imagesetter, Microsoft Shared Fax Driver  |
| [Microsoft-Windows-Desktop-Shared-Removable](./Removable-Packages-Details/Removable-Package-Desktop_SharedPackages.md) | [Microsoft-Windows-RecoveryDrive](./Removable-Packages-Details/Removable-Package-RecoveryDrive.md) |  |
| [Microsoft-Windows-Desktop-Shared-Removable](./Removable-Packages-Details/Removable-Package-Desktop_SharedPackages.md) | [Microsoft-Windows-ScreenSavers-3D](./Removable-Packages-Details/Removable-Package-ScreenSavers.md) | Screensavers  |
| [Microsoft-Windows-Desktop-Shared-Removable](./Removable-Packages-Details/Removable-Package-Desktop_SharedPackages.md) | [Microsoft-Windows-SensorDataService](./Removable-Packages-Details/Removable-Package-SensorDataService.md) | Legacy camera and image integration service to support Windows Hello for devices using old IR cameras |
| [Microsoft-Windows-Desktop-Shared-Removable](./Removable-Packages-Details/Removable-Package-Desktop_SharedPackages.md) | [Microsoft-Windows-ShellOptions](./Removable-Packages-Details/Removable-Package-ShellOptions.md) |  |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Microsoft-Media-Foundation]() | |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Microsoft-OneCore-Multimedia-CastingCommon]() | |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Microsoft-OneCore-Multimedia-CastingReceiver-Media]() | |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Microsoft-OneCore-Multimedia-CastingTransmitter-Media]() | |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Microsoft-OneCore-Multimedia-MFPMP]() | |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Microsoft-Windows-Media-Format]() | |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Microsoft-Windows-Media-Format-merged]() | |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Microsoft-Windows-MediaPlayback-OC]() | |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Microsoft-Windows-Media-Streaming]() | |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Microsoft-Windows-Media-Streaming-merged]() | |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Microsoft-Windows-Multimedia-MF]() | |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Microsoft-Windows-Multimedia-MF-merged]() | |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Microsoft-Windows-Multimedia-RestrictedCodecs]() | |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Microsoft-Windows-Multimedia-RestrictedCodecs-merged]() | |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Microsoft-Windows-Multimedia-WMPDMC]() | |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Microsoft-Windows-Portable-Devices]() | Media Transfer Protocol (MTP) |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Microsoft-Windows-Portable-Devices-merged]() | Media Transfer Protocol (MTP) |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Microsoft-Windows-WebcamExperience]() | |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Microsoft-Windows-WinSATMediaFiles]() | |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Microsoft-Windows-WPD-LegacyWmdmFeature-Feature]() | Windows Portable Devices|
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Microsoft-Windows-WPD-UltimatePortableDeviceFeature-Feature]() | Windows Portable Devices |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Multimedia-MFCore]() | |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Multimedia-MFCore-WCOSHeadless]() | |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Multimedia-MFCore-WCOSMinusHeadless]() | |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Multimedia-RestrictedCodecsCore]() | |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Multimedia-RestrictedCodecsCore-Full]() | |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Multimedia-RestrictedCodecsCore-WCOSHeadless]() | |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Multimedia-RestrictedCodecsCore-WCOSMinusHeadless]() | |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Multimedia-RestrictedCodecsExt]() | |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Multimedia-RestrictedCodecsExt-WCOSHeadless]() | |
| [Microsoft-Windows-Common-RegulatedPackages](./Removable-Packages-Details/Removable-Package-Common_RegulatedPackages.md) | [Multimedia-RestrictedCodecsExt-WCOSMinusHeadless]() | |

## Additional Resources
* [Removable Packages Blog](https://aka.ms/RemovablePackagesBlog)
* [Removable Packages Script](https://aka.ms/RemovablePackagesScript)
* [Reduce Disk Footprint](/windows/iot/iot-enterprise/optimize-your-device/reduce-disk-footprint)
