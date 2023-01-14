---
title: Removable Packages Overview
author: twarwick
ms.author: twarwick
ms.date: 1/12/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Windows IoT Enterprise feature to assist with reducing disk footprint
keywords: IoT Enterprise, removable packages, storage
---

# Removable Packages Overview

In addition to the image customizability provided by '[Enable or Disable Windows Features using DISM](/windows-hardware/manufacture/desktop/enable-or-disable-windows-features-using-dism)' and '[Features on Demand](/windows-hardware/manufacture/desktop/features-on-demand-v2--capabilities)', a device builder can remove extra packages from Windows IoT Enterprise LTSC using the methods described in this article.

Using the desktop manufacturing process to '[Modify a Windows image](/windows-hardware/manufacture/desktop/modify-an-image)', a device maker may use either '[Online servicing ](/windows-hardware/manufacture/desktop/audit-mode-overview)' or '[Offline Servicing](/windows-hardware/manufacture/desktop/mount-and-modify-a-windows-image-using-dism)' methods to completely remove packages in the list below from the '[Windows Component Store](/windows-hardware/manufacture/desktop/manage-the-component-store)'. Once packages are removed from the Windows Component Store, they can't be added back to the operating system. Restoring removed packages requires a reinstallation of the operating system.

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

### Online Servicing 
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Online``` command-line parameter to remove a single package via online servicing.

```powershell
Dism.exe /Online /LogPath:<logfile> /NoRestart /Disable-Feature /FeatureName:<package name> /PackageName:@Package
```

Example: Use DISM.exe to remove Windows calculator using online servicing.
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


| Removable Package  | Description | Size |
|:-------------------|-------------|-----:|
| [Language Word Breaking Legacy](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/LanguageFeatures-Wordbreaking-Common-legacy)   | Legacy neutral word breaker, should only be needed in occasional application compatibility scenarios. | 1,542 KB |
| [Media Foundation](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Media-Foundation)                                     | Component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk) enables the development of applications and components for using digital media. [Supported Media Formats in Media Foundation](/windows/win32/medfound/supported-media-formats-in-media-foundation).   | 63,747 KB |
| [Supplemental Fonts](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-OneCore-Fonts-DesktopFonts-NonLeanSupplement) | Fonts: [Malgun Gothic](/typography/font-list/malgun-gothic), [Microsoft JhengHei](/typography/font-list/microsoft-jhenghei), [Microsoft YaHei](/typography/font-list/microsoft-yahei), [Yu Gothic](/typography/font-list/yu-gothic) | 113,251 KB |
| [User Experience Virtualization](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-AppManagement-UEV)                   | [User Experience Virtualization](/windows/configuration/ue-v/uev-for-windows) | 13,752 KB |
| [Bio Enrollment Experience](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-BioEnrollment-UX)                     | [Windows Hello](/windows-hardware/design/device-experiences/windows-hello) | 3,589 KB |
| [Boot Environment DVD](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-BootEnvironment-Dvd)               | Boot from DVD | 9,108 KB |
| [Windows Media Format](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-Media-Format)                             | A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of support for [Windows Media Device Manager](/windows/win32/wmdm/windows-media-device-manager-architecture),  [Advanced Systems Format](/windows/win32/wmformat/overview-of-the-asf-format) (ASF) file container, Windows Media audio and video codecs, basic network streaming, and [Digital Rights Management](/windows/win32/wmformat/overview-of-windows-media-drm). | 5,559 KB |
| [Media Features Optional Component](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-MediaPlayback-OC)                     | Controls availability of the *Media Features" and "Windows Media Player" options for the *Turn Windows features on or off* user experience in Control Panel. | 0 KB 
| [Windows Media Streaming](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-Media-Streaming)                       | A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing support for [Windows Media Streaming](/windows/win32/mediastreaming/media-streaming-api-portal). | 6,644 KB |
| [Windows Portable Devices](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-Portable-Devices)                     | A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing connectivity to portable devices for [Windows Media Device Manager](/windows/win32/wmdm/,windows-media-device-manager-architecture). | 6,405 KB |
| [Printer Drivers](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-Printer-Drivers)                       | Generic / Text Only, Generic IBM Graphics 9pin, Generic IBM Graphics 9-pin wide, MS Publisher Color Printer, MS Publisher Imagesetter, Microsoft Shared Fax Driver | 8,200 KB |
| [PrintBrm Command-Line Tool](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-Printing-PremiumTools)           | Print services migration command-line tool printbrm.exe | 381 KB |
| [Recovery Drive](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-RecoveryDrive)                           | Create a recovery drive user experience invoked from Control Panel - Recovery | 1.041 KB |
| [3D Screensavers](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-ScreenSavers-3D)                    | Screensavers: 3D Text, Bubbles, Mystify and Ribbons | 1,312 KB |
| [Sensor Data Service](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-SensorDataService)                | Component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) supporting data acquisition from  various sensors.  Supports Windows Hello.  | 1,367 KB |
| [Shell Accessoriess](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-ShellOptions)                          | Modern Calculator, Character Map, More Icons DLL | 657 KB |
| [Desktop Wallpaper](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-Shell-Wallpaper-Common)      | Wallpaper images |  8,538 KB |
| [Webcam Experience](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-WebcamExperience)                  | A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing webcam user experience. | 1,394 KB |
| [Legacy Calculator App](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-win32calc)                                | Legacy Calculator Application | 1,394 KB |
| [WinSAT Media Files](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-WinSATMediaFiles)                  | A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of media files for Windows System Assessment Tool. | TBD |

## More Resources
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview)
- [Removable Packages Blog](https://aka.ms/RemovablePackagesBlog)
- [Removable Packages Script](https://aka.ms/RemovablePackagesScript)
