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
This feature is supported on Windows 10 IoT Enterprise LTSC 2021 (build 19044.1741) or later

> [!Note]
>
> To use this feature with Windows 10 IoT Enterprise LTSC 2021, you must first install a servicing update.  
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
Dism.exe /Online /LogPath:%WINDIR%/Temp/remove_win32calc.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-win32calc /PackageName:@Package
````
### Offline Servicing
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Image:<image path>``` command-line parameter to remove a single package via offline servicing.

```powershell
Dism.exe /Image:<image path> /LogPath:<logfile> /NoRestart /Disable-Feature /FeatureName:<package name> /PackageName:@Package
```

Example: Use DISM.exe to remove Windows calculator using offline servicing.
```powershell
Dism.exe /Image:c:/offline /LogPath:%WINDIR%/Temp/remove_win32calc.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-win32calc /PackageName:@Package
````

## Package Reference

The following packages can be removed from Windows IoT Enterprise LTSC 2021.  Click on each package name to see more details about the package payload.


| Removable Package  | Description |
|:-------------------|-------------|
| [LanguageFeatures-Workbreaking-Common-legacy](/windows/iot/iot-enterprise/Removable-Packages/Removable-Packages-Details/LanguageFeatures-Workbreaking-Common-legacy) | Legacy neutral word breaker, should only be needed in very rare app compat scenarios |
| [Microsoft-Media-Foundation](/windows/iot/iot-enterprise/Removable-Packages/Removable-Packages-Details/Microsoft-Media-Foundation)                                     | Component of the [Media Feature Pack](https://learn.microsoft.com/en-us/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk) enables the development of applications and components for using digital media. [Supported Media Formats in Media Foundation](/windows/win32/medfound/supported-media-formats-in-media-foundation). |
| [Microsoft-OneCore-Fonts-DesktopFonts-NonLeanSupplement](/windows/iot/iot-enterprise/Removable-Packages/Removable-Packages-Details/Microsoft-OneCore-Fonts-DesktopFonts-NonLeanSupplement) | Fonts: [Malgun Gothic](/typography/font-list/malgun-gothic), [Microsoft JhengHei](/typography/font-list/microsoft-jhenghei), [Microsoft YaHei](/typography/font-list/microsoft-yahei), [Yu Gothic](/typography/font-list/yu-gothic) |
| [Microsoft-Windows-AppManagement-UEV](/windows/iot/iot-enterprise/Removable-Packages/Removable-Packages-Details/Microsoft-Windows-AppManagement-UEV)                   | [User Experience Virtualization](/windows/configuration/ue-v/uev-for-windows) |
| [Microsoft-Windows-BioEnrollment-UX](/windows/iot/iot-enterprise/Removable-Packages/Removable-Packages-Details/Microsoft-Windows-BioEnrollment-UX)                     | [Windows Hello](/windows-hardware/design/device-experiences/windows-hello) |
| [Microsoft-Windows-BootEnvironment-Dvd](/windows/iot/iot-enterprise/Removable-Packages/Removable-Packages-Details/Microsoft-Windows-BootEnvironment-Dvd)               | Boot from DVD |
| [Microsoft-Windows-Media-Format](/windows/iot/iot-enterprise/Removable-Packages/Removable-Packages-Details/Microsoft-Windows-Media-Format)                             | Component of the [Media Feature Pack](https://learn.microsoft.com/en-us/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of support for [Windows Media Device Manager](/windows/win32/wmdm/,windows-media-device-manager-architecture),  [Advanced Systems Format](/windows/win32/wmformat/overview-of-the-asf-format) (ASF) file container, the Windows Media audio and video codecs, basic network streaming capability, and [Digital Rights Management](/windows/win32/wmformat/overview-of-windows-media-drm). |
| [Microsoft-Windows-MediaPlayback-OC](/windows/iot/iot-enterprise/Removable-Packages/Removable-Packages-Details/Microsoft-Windows-MediaPlayback-OC)                     | Component of the [Media Feature Pack](https://learn.microsoft.com/en-us/windows/win32/wmdm/windows-media-device-manager-architecture) supporting Windows Media Player |
| [Microsoft-Windows-Media-Streaming](/windows/iot/iot-enterprise/Removable-Packages/Removable-Packages-Details/Microsoft-Windows-Media-Streaming)                       | Component of the [Media Feature Pack](https://learn.microsoft.com/en-us/windows/win32/wmdm/windows-media-device-manager-architecture) providing support for [Windows Media Streaming](/windows/win32/mediastreaming/media-streaming-api-portal). |
| [Microsoft-Windows-Portable-Devices](/windows/iot/iot-enterprise/Removable-Packages/Removable-Packages-Details/Microsoft-Windows-Portable-Devices)                     | Component of the [Media Feature Pack](https://learn.microsoft.com/en-us/windows/win32/wmdm/windows-media-device-manager-architecture) Supporting connectivity to portable devices for [Windows Media Device Manager](/windows/win32/wmdm/,windows-media-device-manager-architecture). |
| [Microsoft-Windows-Printer-Drivers](/windows/iot/iot-enterprise/Removable-Packages/Removable-Packages-Details/Microsoft-Windows-Printer-Drivers)                       | Generic / Text Only, Generic IBM Graphics 9pin, Generic IBM Graphics 9pin wide, MS Publisher Color Printer, MS Publisher Imagesetter, Microsoft Shared Fax Driver |
| [Microsoft-Windows-Printing-PremiumTools](/windows/iot/iot-enterprise/Removable-Packages/Removable-Packages-Details/Microsoft-Windows-Printing-PremiumTools)           | Print services migration command-line tool printbrm.exe |
| [Microsoft-Windows-RecoveryDrive](/windows/iot/iot-enterprise/Removable-Packages/Removable-Packages-Details/Microsoft-Windows-RecoveryDrive)                           | Create a recovery drive user experience invoked from Control Panel - Recovery |
| [Microsoft-Windows-ScreenSavers-3D](/windows/iot/iot-enterprise/Removable-Packages/Removable-Packages-Details/Microsoft-Windows-ScreenSavers-3D.md)                    | Screensavers: 3D Text, Bubbles, Mystify and Ribbons |
| [Microsoft-Windows-SensorDataService](/windows/iot/iot-enterprise/Removable-Packages/Removable-Packages-Details/Microsoft-Windows-SensorDataService.md)                | Component of the [Media Feature Pack](https://learn.microsoft.com/en-us/windows/win32/wmdm/windows-media-device-manager-architecture) supporting data acquision from  a variety of sensors.  Supports Windows Hello.  |
| [Microsoft-Windows-ShellOptions](/windows/iot/iot-enterprise/Removable-Packages/Removable-Packages-Details/Microsoft-Windows-ShellOptions.md)                          | Modern Calculator, Character Map, More Icons DLL |
| [Microsoft-Windows-Shell-Wallpaper-Common](/windows/iot/iot-enterprise/Removable-Packages/Removable-Packages-Details/Microsoft-Windows-Shell-Wallpaper-Common.md)      | Wallpaper images |
| [Microsoft-Windows-WebcamExperience](/windows/iot/iot-enterprise/Removable-Packages/Removable-Packages-Details/Microsoft-Windows-WebcamExperience.md)                  | Component of the [Media Feature Pack](https://learn.microsoft.com/en-us/windows/win32/wmdm/windows-media-device-manager-architecture) providing WebCam User Experience |
| [Microsoft-Windows-win32calc](/windows/iot/iot-enterprise/Removable-Packages/Removable-Packages-Details/Microsoft-Windows-win32calc.md)                                | Legacy Calculator Application|
| [Microsoft-Windows-WinSATMediaFiles](/windows/iot/iot-enterprise/Removable-Packages/Removable-Packages-Details/Microsoft-Windows-WinSATMediaFiles.md)                  | Component of the [Media Feature Pack](https://learn.microsoft.com/en-us/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of media files for Windows System Assessment Tool |

## Additional Resources
* [Removable Packages Blog](https://aka.ms/RemovablePackagesBlog)
* [Removable Packages Script](https://aka.ms/RemovablePackagesScript)
* [Reduce Disk Footprint](/windows/iot/iot-enterprise/optimize-your-device/reduce-disk-footprint)
