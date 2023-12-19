---
title: Removable Packages Overview
author: twarwick
ms.author: twarwick
ms.date: 12/19/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Windows IoT Enterprise feature to assist with reducing disk footprint
keywords: IoT Enterprise, removable packages, storage
---

# Removable Packages

> [!WARNING]
> THIS IS AN IN-PROGRESS ROUGH DRAFT. The wording and feature list may change before publishing.

**Applies to:**

- Windows&nbsp;11&nbsp;IoT&nbsp;Enterprise&nbsp;LTSC&nbsp;vNext
- Windows&nbsp;10&nbsp;IoT&nbsp;Enterprise&nbsp;LTSC&nbsp;2021 (19044.1741&nbsp;or&nbsp;later)

## Overview

The methods described in this article allow a device builder to remove specific feature packages from Windows IoT Enterprise LTSC.  These removable packages are in addition to the capabilities provided by '[Enable or Disable Windows Features using DISM](/windows-hardware/manufacture/desktop/enable-or-disable-windows-features-using-dism)' and '[Features on Demand](/windows-hardware/manufacture/desktop/features-on-demand-v2--capabilities)'

Using the desktop manufacturing process to '[Modify a Windows image](/windows-hardware/manufacture/desktop/modify-an-image)', a device maker may use either '[Online servicing](/windows-hardware/manufacture/desktop/audit-mode-overview)' or '[Offline Servicing](/windows-hardware/manufacture/desktop/mount-and-modify-a-windows-image-using-dism)' methods to completely remove packages supported packages from the '[Windows Component Store](/windows-hardware/manufacture/desktop/manage-the-component-store)'. Once packages are removed from the Windows Component Store, they can't be added back to the operating system. Restoring removed packages requires a reinstallation of the operating system.

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

# [Windows 11 IoT Enterprise LTSC 2024-ONE](#tab/LTSC2024_1)

The following packages can be removed from Windows IoT Enterprise LTSC 2024.  Select on each package name to see more details about the package payload.

<!-- Build 26020 -->
| New | x64  | ARM64 | Removable Package  |
|-----|-----:|-----:|:-------------------|
|⬜|   1,568&nbsp;KB |   1,756&nbsp;KB | **[Language Word Breaking Legacy](/Removable-Packages/LanguageFeatures-Wordbreaking-Common-legacy)** </br> Legacy neutral word breaker should only be needed in occasional application compatibility scenarios. |
|⬜|  56,959&nbsp;KB |  99,210&nbsp;KB | **[Media Foundation](/Removable-Packages/Microsoft-Media-Foundation)** </br> Component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk) enables the development of applications and components for using digital media. [Supported Media Formats in Media Foundation](/windows/win32/medfound/supported-media-formats-in-media-foundation).   |
|✅|   1,111&nbsp;KB |     853&nbsp;KB | **[USB Connector Manager](/Removable-Packages/Microsoft-OneCore-Connectivity-UsbConnectorManager.md)** </br> |
|✅|     737&nbsp;KB |     622&nbsp;KB | **[USB Function](/Removable-Packages/Microsoft-OneCore-Connectivity-UsbFunction.md)** </br> |
|⬜|  28,383&nbsp;KB |  28,383&nbsp;KB | **[Supplemental Fonts](/Removable-Packages/Microsoft-OneCore-Fonts-DesktopFonts-NonLeanSupplement)** </br> Fonts: [Malgun Gothic](/typography/font-list/malgun-gothic), [Microsoft JhengHei](/typography/font-list/microsoft-jhenghei), [Microsoft YaHei](/typography/font-list/microsoft-yahei), [Yu Gothic](/typography/font-list/yu-gothic) |
|✅|   4,022&nbsp;KB |   4,661&nbsp;KB | **[Camera Barcode Scanner](/Removable-Packages/Microsoft-OneCore-PointOfService-CameraBarcodeScanner.md)** </br> |
|✅|   1,460&nbsp;KB |   2,517&nbsp;KB | **[Remote Desktop Services](/Removable-Packages/Microsoft-OneCore-RemoteDesktopServices-Collaboration.md)** </br> |
|✅|     928&nbsp;KB |     764&nbsp;KB | **[SD](/Removable-Packages/Microsoft-OneCore-SD.md)** </br> |
|✅|     824&nbsp;KB |     980&nbsp;KB | **[System Settings Devices](/Removable-Packages/Microsoft-OneCore-SystemSettings-Devices.md)** </br> |
|✅|   3,340&nbsp;KB |   3,842&nbsp;KB | **[Network Mobile Handlers]** </br> |
|✅|        &nbsp;KB |   6,171&nbsp;KB | **[3D Audio HRTF Data](/Removable-Packages/Microsoft-Windows-3DAudio-HrtfData.md)** </br> |
|⬜|  13,752&nbsp;KB |   ???  &nbsp;KB | **[User Experience Virtualization](/Removable-Packages/Microsoft-Windows-AppManagement-UEV)** </br> [User Experience Virtualization](/windows/configuration/ue-v/uev-for-windows) |
|⬜|   3,589&nbsp;KB |   4,867&nbsp;KB | **[Bio Enrollment Experience](/Removable-Packages/Microsoft-Windows-BioEnrollment-UX)** </br> [Windows Hello](/windows-hardware/design/device-experiences/windows-hello) |
|⬜|   9,108&nbsp;KB |   3,112&nbsp;KB | **[Boot Environment DVD](/Removable-Packages/Microsoft-Windows-BootEnvironment-Dvd)** </br> Boot from DVD |
|✅|     483&nbsp;KB |     604&nbsp;KB | **[Computer Manager Launcher](/Removable-Packages/Microsoft-Windows-ComputerManagerLauncher.md)** </br> |
|✅|     604&nbsp;KB |     583&nbsp;KB | **[Defrag User Experience](/Removable-Packages/Microsoft-Windows-Defrag-UI.md)** </br> |
|✅|   2,835&nbsp;KB |   3,787&nbsp;KB | **[Desktop File Explorer](/Removable-Packages/Microsoft-Windows-DesktopFileExplorer.md)** </br> |
|⬜|   5,202&nbsp;KB |   8,908&nbsp;KB | **[Windows Media Format](/Removable-Packages/Microsoft-Windows-Media-Format)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of support for [Windows Media Device Manager](/windows/win32/wmdm/windows-media-device-manager-architecture),  [Advanced Systems Format](/windows/win32/wmformat/overview-of-the-asf-format) (ASF) file container, Windows Media audio and video codecs, basic network streaming, and [Digital Rights Management](/windows/win32/wmformat/overview-of-windows-media-drm). |
|⬜|   7,028&nbsp;KB |  10,195&nbsp;KB | **[Windows Media Streaming](/Removable-Packages/Microsoft-Windows-Media-Streaming)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing support for [Windows Media Streaming](/windows/win32/mediastreaming/media-streaming-api-portal). |
|⬜|       0&nbsp;KB |       0&nbsp;KB | **[Media Features Optional Component](/Removable-Packages/Microsoft-Windows-MediaPlayback-OC)** </br> Controls availability of the "Media Features" and "Windows Media Player" options for the *Turn Windows features on or off* user experience in Control Panel. |
|✅|  10,811&nbsp;KB |  10,792&nbsp;KB | **[Microsoft Edge Dev Tools Client](/Removable-Packages/Microsoft-Windows-MicrosoftEdgeDevToolsClient.md)** </br> |
|✅|     823&nbsp;KB |     797&nbsp;KB | **[Mobile PC Client Basic](/Removable-Packages/Microsoft-Windows-MobilePC-Client-Basic.md)** </br> |
|✅|     899&nbsp;KB |   1,106&nbsp;KB | **[NetProfilesUX](/Removable-Packages/Microsoft-Windows-NetProfilesUX.md)** </br> |
|✅|       0&nbsp;KB |       0&nbsp;KB | **[PEAuth](/Removable-Packages/Microsoft-Windows-PEAuth-OneCore.md)** </br> |
|⬜|   6,830&nbsp;KB |   7,979&nbsp;KB | **[Windows Portable Devices](/Removable-Packages/Microsoft-Windows-Portable-Devices)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing connectivity to portable devices for [Windows Media Device Manager](/windows/win32/wmdm/windows-media-device-manager-architecture). |
|⬜|   8,578&nbsp;KB |      94&nbsp;KB | **[Printer Drivers](/Removable-Packages/Microsoft-Windows-Printer-Drivers)** </br> Generic / Text Only, Generic IBM Graphics 9pin, Generic IBM Graphics 9-pin wide, MS Publisher Color Printer, MS Publisher Imagesetter, Microsoft Shared Fax Driver |
|⬜|     460&nbsp;KB |     397&nbsp;KB | **[PrintBrm Command-Line Tool](/Removable-Packages/Microsoft-Windows-Printing-PremiumTools)** </br> Print services migration command-line tool printbrm.exe |
|⬜|     473&nbsp;KB |     451&nbsp;KB | **[Recovery Drive](/Removable-Packages/Microsoft-Windows-RecoveryDrive)** </br> Create a recovery drive user experience invoked from Control Panel - Recovery |
|⬜|   1,591&nbsp;KB |   1,173&nbsp;KB | **[3D Screensavers](/Removable-Packages/Microsoft-Windows-ScreenSavers-3D)** </br> Screensavers: 3D Text, Bubbles, Mystify and Ribbons |
|⬜|        &nbsp;KB |        &nbsp;KB | **[Sensor Data Service](/Removable-Packages/Microsoft-Windows-SensorDataService)** </br> Component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) supporting data acquisition from  various sensors.  Supports Windows Hello.  |
|⬜|        &nbsp;KB |        &nbsp;KB | **[Shell Accessories](/Removable-Packages/Microsoft-Windows-ShellOptions)** </br> Modern Calculator, Character Map, More Icons DLL |
|✅|        &nbsp;KB |        &nbsp;KB | **[Window Tab Manager](/Removable-Packages/Microsoft-Windows-UI-Shell-WindowTabManager.md)** </br> |
|⬜|        &nbsp;KB |        &nbsp;KB | **[Desktop Wallpaper](/Removable-Packages/Microsoft-Windows-Shell-Wallpaper-Common)** </br> Wallpaper images |
|⬜|        &nbsp;KB |        &nbsp;KB | **[Webcam Experience](/Removable-Packages/Microsoft-Windows-WebcamExperience)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing webcam user experience. |
|⬜|        &nbsp;KB |        &nbsp;KB | **[Legacy Calculator App](/Removable-Packages/Microsoft-Windows-win32calc)** </br> Legacy Calculator Application |
|⬜|        &nbsp;KB |        &nbsp;KB | **[WinSAT Media Files](/Removable-Packages/Microsoft-Windows-WinSATMediaFiles)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of media files for Windows System Assessment Tool. |

# [Windows 11 IoT Enterprise LTSC 2024-TWO](#tab/LTSC2024_2)

The following packages can be removed from Windows IoT Enterprise LTSC 2024.  Select on each package name to see more details about the package payload.

<!-- Build 26020 -->
| New | x64  | ARM64 | Removable Package  |
|-----|-----:|-----:|:-------------------|
|⬜| **[Language Word Breaking Legacy](/Removable-Packages/LanguageFeatures-Wordbreaking-Common-legacy)** </br> Legacy neutral word breaker should only be needed in occasional application compatibility scenarios. |   1,568&nbsp;KB |   1,756&nbsp;KB |
|⬜| **[Media Foundation](/Removable-Packages/Microsoft-Media-Foundation)** </br> Component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk) enables the development of applications and components for using digital media. [Supported Media Formats in Media Foundation](/windows/win32/medfound/supported-media-formats-in-media-foundation).   |  56,959&nbsp;KB |  99,210&nbsp;KB |
|✅| **[USB Connector Manager](/Removable-Packages/Microsoft-OneCore-Connectivity-UsbConnectorManager.md)** </br> |   1,111&nbsp;KB |     853&nbsp;KB |
|✅| **[USB Function](/Removable-Packages/Microsoft-OneCore-Connectivity-UsbFunction.md)** </br> |     737&nbsp;KB |     622&nbsp;KB |
|⬜| **[Supplemental Fonts](/Removable-Packages/Microsoft-OneCore-Fonts-DesktopFonts-NonLeanSupplement)** </br> Fonts: [Malgun Gothic](/typography/font-list/malgun-gothic), [Microsoft JhengHei](/typography/font-list/microsoft-jhenghei), [Microsoft YaHei](/typography/font-list/microsoft-yahei), [Yu Gothic](/typography/font-list/yu-gothic) |  28,383&nbsp;KB |  28,383&nbsp;KB |
|✅| **[Camera Barcode Scanner](/Removable-Packages/Microsoft-OneCore-PointOfService-CameraBarcodeScanner.md)** </br> |   4,022&nbsp;KB |   4,661&nbsp;KB |
|✅| **[Remote Desktop Services](/Removable-Packages/Microsoft-OneCore-RemoteDesktopServices-Collaboration.md)** </br> |   1,460&nbsp;KB |   2,517&nbsp;KB |
|✅| **[SD](/Removable-Packages/Microsoft-OneCore-SD.md)** </br> |     928&nbsp;KB |     764&nbsp;KB |
|✅| **[System Settings Devices](/Removable-Packages/Microsoft-OneCore-SystemSettings-Devices.md)** </br> |     824&nbsp;KB |     980&nbsp;KB |
|✅| **[Network Mobile Handlers]** </br> |   3,340&nbsp;KB |   3,842&nbsp;KB |
|✅| **[3D Audio HRTF Data](/Removable-Packages/Microsoft-Windows-3DAudio-HrtfData.md)** </br> |        &nbsp;KB |   6,171&nbsp;KB |
|⬜| **[User Experience Virtualization](/Removable-Packages/Microsoft-Windows-AppManagement-UEV)** </br> [User Experience Virtualization](/windows/configuration/ue-v/uev-for-windows) |  13,752&nbsp;KB |   ???  &nbsp;KB |
|⬜| **[Bio Enrollment Experience](/Removable-Packages/Microsoft-Windows-BioEnrollment-UX)** </br> [Windows Hello](/windows-hardware/design/device-experiences/windows-hello) |   3,589&nbsp;KB |   4,867&nbsp;KB |
|⬜| **[Boot Environment DVD](/Removable-Packages/Microsoft-Windows-BootEnvironment-Dvd)** </br> Boot from DVD |  9,108&nbsp;KB |   3,112&nbsp;KB |
|✅| **[Computer Manager Launcher](/Removable-Packages/Microsoft-Windows-ComputerManagerLauncher.md)** </br> |     483&nbsp;KB |     604&nbsp;KB |
|✅| **[Defrag User Experience](/Removable-Packages/Microsoft-Windows-Defrag-UI.md)** </br> |     604&nbsp;KB |     583&nbsp;KB |
|✅| **[Desktop File Explorer](/Removable-Packages/Microsoft-Windows-DesktopFileExplorer.md)** </br> |   2,835&nbsp;KB |   3,787&nbsp;KB |
|⬜| **[Windows Media Format](/Removable-Packages/Microsoft-Windows-Media-Format)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of support for [Windows Media Device Manager](/windows/win32/wmdm/windows-media-device-manager-architecture),  [Advanced Systems Format](/windows/win32/wmformat/overview-of-the-asf-format) (ASF) file container, Windows Media audio and video codecs, basic network streaming, and [Digital Rights Management](/windows/win32/wmformat/overview-of-windows-media-drm). |   5,202&nbsp;KB |   8,908&nbsp;KB |
|⬜| **[Windows Media Streaming](/Removable-Packages/Microsoft-Windows-Media-Streaming)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing support for [Windows Media Streaming](/windows/win32/mediastreaming/media-streaming-api-portal). |   7,028&nbsp;KB |  10,195&nbsp;KB |
|⬜| **[Media Features Optional Component](/Removable-Packages/Microsoft-Windows-MediaPlayback-OC)** </br> Controls availability of the "Media Features" and "Windows Media Player" options for the *Turn Windows features on or off* user experience in Control Panel. |       0&nbsp;KB |       0&nbsp;KB |
|✅| **[Microsoft Edge Dev Tools Client](/Removable-Packages/Microsoft-Windows-MicrosoftEdgeDevToolsClient.md)** </br> |  10,811&nbsp;KB |  10,792&nbsp;KB |
|✅| **[Mobile PC Client Basic](/Removable-Packages/Microsoft-Windows-MobilePC-Client-Basic.md)** </br> |     823&nbsp;KB |     797&nbsp;KB |
|✅| **[NetProfilesUX](/Removable-Packages/Microsoft-Windows-NetProfilesUX.md)** </br> |     899&nbsp;KB |   1,106&nbsp;KB |
|✅| **[PEAuth](/Removable-Packages/Microsoft-Windows-PEAuth-OneCore.md)** </br> |       0&nbsp;KB |       0&nbsp;KB |
|⬜| **[Windows Portable Devices](/Removable-Packages/Microsoft-Windows-Portable-Devices)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing connectivity to portable devices for [Windows Media Device Manager](/windows/win32/wmdm/windows-media-device-manager-architecture). |   6,830&nbsp;KB |   7,979&nbsp;KB |
|⬜| **[Printer Drivers](/Removable-Packages/Microsoft-Windows-Printer-Drivers)** </br> Generic / Text Only, Generic IBM Graphics 9pin, Generic IBM Graphics 9-pin wide, MS Publisher Color Printer, MS Publisher Imagesetter, Microsoft Shared Fax Driver |   8,578&nbsp;KB |      94&nbsp;KB |
|⬜| **[PrintBrm Command-Line Tool](/Removable-Packages/Microsoft-Windows-Printing-PremiumTools)** </br> Print services migration command-line tool printbrm.exe |     460&nbsp;KB |     397&nbsp;KB |
|⬜| **[Recovery Drive](/Removable-Packages/Microsoft-Windows-RecoveryDrive)** </br> Create a recovery drive user experience invoked from Control Panel - Recovery |     473&nbsp;KB |     451&nbsp;KB |
|⬜| **[3D Screensavers](/Removable-Packages/Microsoft-Windows-ScreenSavers-3D)** </br> Screensavers: 3D Text, Bubbles, Mystify and Ribbons |   1,591&nbsp;KB |   1,173&nbsp;KB |
|⬜| **[Sensor Data Service](/Removable-Packages/Microsoft-Windows-SensorDataService)** </br> Component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) supporting data acquisition from  various sensors.  Supports Windows Hello.  |        &nbsp;KB |        &nbsp;KB |
|⬜| **[Shell Accessories](/Removable-Packages/Microsoft-Windows-ShellOptions)** </br> Modern Calculator, Character Map, More Icons DLL |        &nbsp;KB |        &nbsp;KB |
|✅| **[Window Tab Manager](/Removable-Packages/Microsoft-Windows-UI-Shell-WindowTabManager.md)** </br> |        &nbsp;KB |        &nbsp;KB |
|⬜| **[Desktop Wallpaper](/Removable-Packages/Microsoft-Windows-Shell-Wallpaper-Common)** </br> Wallpaper images |        &nbsp;KB |        &nbsp;KB |
|⬜| **[Webcam Experience](/Removable-Packages/Microsoft-Windows-WebcamExperience)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing webcam user experience. |        &nbsp;KB |        &nbsp;KB |
|⬜| **[Legacy Calculator App](/Removable-Packages/Microsoft-Windows-win32calc)** </br> Legacy Calculator Application |        &nbsp;KB |        &nbsp;KB |
|⬜| **[WinSAT Media Files](/Removable-Packages/Microsoft-Windows-WinSATMediaFiles)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of media files for Windows System Assessment Tool. |        &nbsp;KB |        &nbsp;KB |

# [Windows 10 IoT Enterprise LTSC 2021](#tab/LTSC2021)

The following packages can be removed from Windows IoT Enterprise LTSC 2021.  Select on each package name to see more details about the package payload.

| Removable Package  | Description | x64 | ARM64 |
|:-------------------|-------------|-----:|:----:|
| [Language Word Breaking Legacy](/Removable-Packages/LanguageFeatures-Wordbreaking-Common-legacy)   | Legacy neutral word breaker should only be needed in occasional application compatibility scenarios. | 1,542&nbsp;KB | TBD |
| [Media Foundation](/Removable-Packages/Microsoft-Media-Foundation) | Component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk) enables the development of applications and components for using digital media. [Supported Media Formats in Media Foundation](/windows/win32/medfound/supported-media-formats-in-media-foundation).   | 63,747&nbsp;KB | TBD |
| [Supplemental Fonts](/Removable-Packages/Microsoft-OneCore-Fonts-DesktopFonts-NonLeanSupplement) | Fonts: [Malgun Gothic](/typography/font-list/malgun-gothic), [Microsoft JhengHei](/typography/font-list/microsoft-jhenghei), [Microsoft YaHei](/typography/font-list/microsoft-yahei), [Yu Gothic](/typography/font-list/yu-gothic) | 113,251&nbsp;KB | TBD |
| [User Experience Virtualization](/Removable-Packages/Microsoft-Windows-AppManagement-UEV)                   | [User Experience Virtualization](/windows/configuration/ue-v/uev-for-windows) | 13,752&nbsp;KB | TBD |
| [Bio Enrollment Experience](/Removable-Packages/Microsoft-Windows-BioEnrollment-UX) | [Windows Hello](/windows-hardware/design/device-experiences/windows-hello) | 3,589&nbsp;KB | TBD |
| [Boot Environment DVD](/Removable-Packages/Microsoft-Windows-BootEnvironment-Dvd) | Boot from DVD | 9,108&nbsp;KB | TBD |
| [Windows Media Format](/Removable-Packages/Microsoft-Windows-Media-Format) | A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of support for [Windows Media Device Manager](/windows/win32/wmdm/windows-media-device-manager-architecture),  [Advanced Systems Format](/windows/win32/wmformat/overview-of-the-asf-format) (ASF) file container, Windows Media audio and video codecs, basic network streaming, and [Digital Rights Management](/windows/win32/wmformat/overview-of-windows-media-drm). | 5,559&nbsp;KB | TBD |
| [Media Features Optional Component](/Removable-Packages/Microsoft-Windows-MediaPlayback-OC) | Controls availability of the "Media Features" and "Windows Media Player" options for the *Turn Windows features on or off* user experience in Control Panel. | 0&nbsp;KB | TBD |
| [Windows Media Streaming](/Removable-Packages/Microsoft-Windows-Media-Streaming) | A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing support for [Windows Media Streaming](/windows/win32/mediastreaming/media-streaming-api-portal). | 6,644&nbsp;KB | TBD |
| [Windows Portable Devices](/Removable-Packages/Microsoft-Windows-Portable-Devices) | A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing connectivity to portable devices for [Windows Media Device Manager](/windows/win32/wmdm/windows-media-device-manager-architecture). | 6,405&nbsp;KB | TBD |
| [Printer Drivers](/Removable-Packages/Microsoft-Windows-Printer-Drivers) | Generic / Text Only, Generic IBM Graphics 9pin, Generic IBM Graphics 9-pin wide, MS Publisher Color Printer, MS Publisher Imagesetter, Microsoft Shared Fax Driver | 8,200&nbsp;KB | TBD |
| [PrintBrm Command-Line Tool](/Removable-Packages/Microsoft-Windows-Printing-PremiumTools) | Print services migration command-line tool printbrm.exe | 381&nbsp;KB | TBD |
| [Recovery Drive](/Removable-Packages/Microsoft-Windows-RecoveryDrive) | Create a recovery drive user experience invoked from Control Panel - Recovery | 1.041&nbsp;KB | TBD |
| [3D Screensavers](/Removable-Packages/Microsoft-Windows-ScreenSavers-3D) | Screensavers: 3D Text, Bubbles, Mystify and Ribbons | 1,312&nbsp;KB | TBD |
| [Sensor Data Service](/Removable-Packages/Microsoft-Windows-SensorDataService) | Component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) supporting data acquisition from  various sensors.  Supports Windows Hello.  | 1,367&nbsp;KB | TBD |
| [Shell Accessories](/Removable-Packages/Microsoft-Windows-ShellOptions) | Modern Calculator, Character Map, More Icons DLL | 657&nbsp;KB | TBD |
| [Desktop Wallpaper](/Removable-Packages/Microsoft-Windows-Shell-Wallpaper-Common) | Wallpaper images |  8,538&nbsp;KB | TBD |
| [Webcam Experience](/Removable-Packages/Microsoft-Windows-WebcamExperience) | A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing webcam user experience. | 1,394&nbsp;KB | TBD |
| [Legacy Calculator App](/Removable-Packages/Microsoft-Windows-win32calc) | Legacy Calculator Application | 1,394&nbsp;KB | TBD |
| [WinSAT Media Files](/Removable-Packages/Microsoft-Windows-WinSATMediaFiles) | A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of media files for Windows System Assessment Tool. | 0&nbsp;KB | TBD |

---

## More Resources

- [Reduce Disk Footprint](/Reduce-Disk-Footprint)
- [Device Optimization Overview](/Overview)
- [Removable Packages Blog](https://aka.ms/RemovablePackagesBlog)
- [Removable Packages Script](https://aka.ms/RemovablePackagesScript)
