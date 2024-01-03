---
title: Removable Packages Overview
titleSuffix: Windows IoT Enterprise
author: twarwick
ms.author: twarwick
ms.date: 01/03/2024
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Windows IoT Enterprise feature to assist with reducing disk footprint
keywords: IoT Enterprise, removable packages, storage
---

# Removable Packages

| Applies to                          |  Version            |
|:------------------------------------|:--------------------|
| Windows 10 IoT Enterprise LTSC 2021 | 19044.1741 or later |

## Overview

In addition to the image customizing provided by '[Enable or Disable Windows Features using DISM](/windows-hardware/manufacture/desktop/enable-or-disable-windows-features-using-dism)' and '[Features on Demand](/windows-hardware/manufacture/desktop/features-on-demand-v2--capabilities)', a device builder can remove extra packages from Windows IoT Enterprise LTSC using the methods described in this article.

Using the desktop manufacturing process to '[Modify a Windows image](/windows-hardware/manufacture/desktop/modify-an-image)', a device maker may use either '[Online servicing](/windows-hardware/manufacture/desktop/audit-mode-overview)' or '[Offline Servicing](/windows-hardware/manufacture/desktop/mount-and-modify-a-windows-image-using-dism)' methods to completely remove packages in the list below from the '[Windows Component Store](/windows-hardware/manufacture/desktop/manage-the-component-store)'. Once packages are removed from the Windows Component Store, they can't be added back to the operating system. Restoring removed packages requires a reinstallation of the operating system.

> [!IMPORTANT]
>
>If you choose to remove any of these packages from Windows IoT Enterprise, you must ensure that your  solution does not rely on functionality of the removed package(s). You cannot restore the package without a full reinstall of Windows IoT Enterprise LTSC.

## System Requirements

This feature is supported on Windows 10 IoT Enterprise LTSC 2021 (build 19044.1741) or later

> [!NOTE]
>
> To use this feature with Windows 10 IoT Enterprise LTSC 2021, you must first install a servicing update.  
>
> - Option 1: Go to Start > Settings > Windows Update then check for and apply all available updates before proceeding.
> - Option 2: Manually download and install  [KB5014023](https://support.microsoft.com/topic/june-2-2022-kb5014023-os-builds-19042-1741-19043-1741-and-19044-1741-preview-65ac6a5d-439a-4e88-b431-a5e2d4e2516a) or any of its successors.

## Package Removal

1. To remove a specific package from the image, for example Windows calculator, type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-win32calc /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline`, for  example Windows calculator, type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-Windows-win32calc /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package, for example Windows calculator, type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Windows-win32calc /PackageName:@Package
   ````

## Package Reference

The following packages can be removed from Windows IoT Enterprise LTSC 2021.  Click on each package name to see more details about the package payload.

| Removable Package  | Description | Size |
|:-------------------|-------------|-----:|
| [Language Word Breaking Legacy](removable-packages/LanguageFeatures-Wordbreaking-Common-legacy.md) | Legacy neutral word breaker, should only be needed in occasional application compatibility scenarios. | 1,542 KB |
| [Media Foundation](removable-packages/Microsoft-Media-Foundation.md)                                     | Component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk) enables the development of applications and components for using digital media. [Supported Media Formats in Media Foundation](/windows/win32/medfound/supported-media-formats-in-media-foundation).   | 63,747 KB |
| [Supplemental Fonts](removable-packages/Microsoft-OneCore-Fonts-DesktopFonts-NonLeanSupplement.md) | Fonts: [Malgun Gothic](/typography/font-list/malgun-gothic), [Microsoft JhengHei](/typography/font-list/microsoft-jhenghei), [Microsoft YaHei](/typography/font-list/microsoft-yahei), [Yu Gothic](/typography/font-list/yu-gothic) | 113,251 KB |
| [User Experience Virtualization](removable-packages/Microsoft-Windows-AppManagement-UEV.md)                   | [User Experience Virtualization](/windows/configuration/ue-v/uev-for-windows) | 13,752 KB |
| [Bio Enrollment Experience](removable-packages/Microsoft-Windows-BioEnrollment-UX.md)                     | [Windows Hello](/windows-hardware/design/device-experiences/windows-hello) | 3,589 KB |
| [Boot Environment DVD](removable-packages/Microsoft-Windows-BootEnvironment-Dvd.md)               | Boot from DVD | 9,108 KB |
| [Windows Media Format](removable-packages/Microsoft-Windows-Media-Format.md)                             | A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of support for [Windows Media Device Manager](/windows/win32/wmdm/windows-media-device-manager-architecture),  [Advanced Systems Format](/windows/win32/wmformat/overview-of-the-asf-format) (ASF) file container, Windows Media audio and video codecs, basic network streaming, and [Digital Rights Management](/windows/win32/wmformat/overview-of-windows-media-drm). | 5,559 KB |
| [Media Features Optional Component](removable-packages/Microsoft-Windows-MediaPlayback-OC.md)                     | Controls availability of the "Media Features" and "Windows Media Player" options for the *Turn Windows features on or off* user experience in Control Panel. | 0 KB |
| [Windows Media Streaming](removable-packages/Microsoft-Windows-Media-Streaming.md)                       | A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing support for [Windows Media Streaming](/windows/win32/mediastreaming/media-streaming-api-portal). | 6,644 KB |
| [Windows Portable Devices](removable-packages/Microsoft-Windows-Portable-Devices.md)                     | A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing connectivity to portable devices for [Windows Media Device Manager](/windows/win32/wmdm/windows-media-device-manager-architecture). | 6,405 KB |
| [Printer Drivers](removable-packages/Microsoft-Windows-Printer-Drivers.md)                       | Generic / Text Only, Generic IBM Graphics 9pin, Generic IBM Graphics 9-pin wide, MS Publisher Color Printer, MS Publisher Imagesetter, Microsoft Shared Fax Driver | 8,200 KB |
| [PrintBrm Command-Line Tool](removable-packages/Microsoft-Windows-Printing-PremiumTools.md)           | Print services migration command-line tool printbrm.exe | 381 KB |
| [Recovery Drive](removable-packages/Microsoft-Windows-RecoveryDrive.md)                           | Create a recovery drive user experience invoked from Control Panel - Recovery | 1.041 KB |
| [3D Screensavers](removable-packages/Microsoft-Windows-ScreenSavers-3D.md)                    | Screensavers: 3D Text, Bubbles, Mystify and Ribbons | 1,312 KB |
| [Sensor Data Service](removable-packages/Microsoft-Windows-SensorDataService.md)                | Component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) supporting data acquisition from  various sensors.  Supports Windows Hello.  | 1,367 KB |
| [Shell Accessories](removable-packages/Microsoft-Windows-ShellOptions.md)                          | Modern Calculator, Character Map, More Icons DLL | 657 KB |
| [Desktop Wallpaper](removable-packages/Microsoft-Windows-Shell-Wallpaper-Common.md)      | Wallpaper images |  8,538 KB |
| [Webcam Experience](removable-packages/Microsoft-Windows-WebcamExperience.md)                  | A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing webcam user experience. | 1,394 KB |
| [Legacy Calculator App](removable-packages/Microsoft-Windows-win32calc.md)                                | Legacy Calculator Application | 1,394 KB |
| [WinSAT Media Files](removable-packages/Microsoft-Windows-WinSATMediaFiles.md)                  | A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of media files for Windows System Assessment Tool. | TBD |

## More Resources

- [Device Optimization Overview](Overview.md)
- [Removable Packages Blog](https://aka.ms/RemovablePackagesBlog)
- [Removable Packages Script](https://aka.ms/RemovablePackagesScript)
