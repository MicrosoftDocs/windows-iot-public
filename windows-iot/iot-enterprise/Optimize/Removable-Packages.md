---
title: Removable Packages Overview
author: twarwick
ms.author: twarwick
ms.date: 12/20/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Windows IoT Enterprise feature to assist with reducing disk footprint
keywords: IoT Enterprise, removable packages, storage
---

# Removable Packages

Applies to:  
✅ Windows 11 IoT Enterprise LTSC 2024  
✅ Windows 10 IoT Enterprise LTSC 2021 (19044.1741 or later)  

## Overview

The methods described in this article allow a device builder to remove specific feature packages from Windows IoT Enterprise LTSC.  These removable packages are in addition to the capabilities provided by [Enable or Disable Windows Features using DISM](/windows-hardware/manufacture/desktop/enable-or-disable-windows-features-using-dism) and [Features on Demand](/windows-hardware/manufacture/desktop/features-on-demand-v2--capabilities)

Using the desktop manufacturing process to [Modify a Windows image](/windows-hardware/manufacture/desktop/modify-an-image), a device maker can use either [Online servicing](/windows-hardware/manufacture/desktop/audit-mode-overview) or [Offline Servicing](/windows-hardware/manufacture/desktop/mount-and-modify-a-windows-image-using-dism) methods to completely remove packages supported packages from the [Windows Component Store](/windows-hardware/manufacture/desktop/manage-the-component-store). Once packages are removed from the Windows Component Store, they can't be added back to the operating system. Restoring removed packages requires a reinstallation of the operating system.

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

# [Windows 11 IoT Enterprise LTSC 2024](#tab/LTSC2024)

The following packages can be removed from Windows IoT Enterprise LTSC 2024.  Select on each package name to see more details about the package payload.

<!-- Build 26021 -->
| New | Removable Package  | x64  | ARM64 |
|-----|:-------------------|-----:|-----:|
| | **[LanguageFeatures-Wordbreaking-Common-legacy](/Removable-Packages/LanguageFeatures-Wordbreaking-Common-legacy.md)** </br> Legacy neutral word breaker should only be needed in occasional application compatibility scenarios. | <!-- x64 -->  1,568&nbsp;KB | <!-- arm64 --> 1,756&nbsp;KB |
| | **[Microsoft-Media-Foundation](/Removable-Packages/Microsoft-Media-Foundation.md)** </br> Component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk) enables the development of applications and components for using digital media. [Supported Media Formats in Media Foundation](/windows/win32/medfound/supported-media-formats-in-media-foundation).   |  <!-- x64 --> 56,959&nbsp;KB | <!-- arm64 --> 99,210&nbsp;KB |
|✅| **[Microsoft-OneCore-Connectivity-UsbConnectorManager](/Removable-Packages/Microsoft-OneCore-Connectivity-UsbConnectorManager.md)** </br> | <!-- x64 -->  1,111&nbsp;KB | <!-- arm64 --> 853&nbsp;KB |
|✅| **[Microsoft-OneCore-Connectivity-UsbFunction](/Removable-Packages/Microsoft-OneCore-Connectivity-UsbFunction.md)** </br> | <!-- x64 --> 747&nbsp;KB | <!-- arm64 --> 622&nbsp;KB |
| | **[Microsoft-OneCore-Fonts-DesktopFonts-NonLeanSupplement](/Removable-Packages/Microsoft-OneCore-Fonts-DesktopFonts-NonLeanSupplement.md)** </br> Fonts: [Malgun Gothic](/typography/font-list/malgun-gothic), [Microsoft JhengHei](/typography/font-list/microsoft-jhenghei), [Microsoft YaHei](/typography/font-list/microsoft-yahei), [Yu Gothic](/typography/font-list/yu-gothic) | <!-- x64 --> 28,383&nbsp;KB | <!-- arm64 --> 28,383&nbsp;KB |
|✅| **[Microsoft-OneCore-PointOfService-CameraBarcodeScanner](/Removable-Packages/Microsoft-OneCore-PointOfService-CameraBarcodeScanner.md)** </br> | <!-- x64 --> 4,022&nbsp;KB | <!-- arm64 --> 4,661&nbsp;KB |
|✅| **[Microsoft-OneCore-RemoteDesktopServices-Collaboration](/Removable-Packages/Microsoft-OneCore-RemoteDesktopServices-Collaboration.md)** </br> | <!-- x64 --> 1,460&nbsp;KB | <!-- arm64 --> 2,517&nbsp;KB |
|✅| **[Microsoft-OneCore-SD](/Removable-Packages/Microsoft-OneCore-SD.md)** </br> | <!-- x64 --> 928&nbsp;KB | <!-- arm64 --> 764&nbsp;KB |
|✅| **[Microsoft-OneCore-SystemSettings-Devices](/Removable-Packages/Microsoft-OneCore-SystemSettings-Devices.md)** </br> | <!-- x64 --> 824&nbsp;KB | <!-- arm64 -->    980&nbsp;KB |
|✅| **[Microsoft-OneCore-SystemSettings-NetworkMobileHandlers](/Removable-Packages/Microsoft-OneCore-SystemSettings-NetworkMobileHandlers.md)** </br> | <!-- x64 --> 3,340&nbsp;KB | <!-- arm64 --> 3,842&nbsp;KB |
|✅| **[Microsoft-Windows-3DAudio-HrtfData](/Removable-Packages/Microsoft-Windows-3DAudio-HrtfData.md)** </br> | <!-- x64 --> &nbsp;KB | <!-- arm64 --> 6,171&nbsp;KB |
| | **[Microsoft-Windows-AppManagement-UEV](/Removable-Packages/Microsoft-Windows-AppManagement-UEV.md)** </br> [User Experience Virtualization](/windows/configuration/ue-v/uev-for-windows) | <!-- x64 --> 13,752&nbsp;KB | <!-- arm64 --> ???  &nbsp;KB |
| | **[Microsoft-Windows-BioEnrollment-UX](/Removable-Packages/Microsoft-Windows-BioEnrollment-UX.md)** </br> [Windows Hello](/windows-hardware/design/device-experiences/windows-hello) | <!-- x64 --> 3,589&nbsp;KB | <!-- arm64 --> 4,867&nbsp;KB |
| | **[Microsoft-Windows-BootEnvironment-Dvd](/Removable-Packages/Microsoft-Windows-BootEnvironment-Dvd.md)** </br> Boot from DVD | <!-- x64 --> 9,108&nbsp;KB | <!-- arm64 --> 3,112&nbsp;KB |
|✅| **[Microsoft-Windows-ComputerManagerLauncher](/Removable-Packages/Microsoft-Windows-ComputerManagerLauncher.md)** </br> | <!-- x64 --> 483&nbsp;KB | <!-- arm64 --> 604&nbsp;KB |
|✅| **[Microsoft-Windows-Defrag-UI](/Removable-Packages/Microsoft-Windows-Defrag-UI.md)** </br> | <!-- x64 --> 604&nbsp;KB | <!-- arm64 --> 583&nbsp;KB |
|✅| **[Microsoft-Windows-DesktopFileExplorer](/Removable-Packages/Microsoft-Windows-DesktopFileExplorer.md)** </br> | <!-- x64 --> 2,738&nbsp;KB | <!-- arm64 --> 3,787&nbsp;KB |
| | **[Microsoft-Windows-Media-Format](/Removable-Packages/Microsoft-Windows-Media-Format.md)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of support for [Windows Media Device Manager](/windows/win32/wmdm/windows-media-device-manager-architecture),  [Advanced Systems Format](/windows/win32/wmformat/overview-of-the-asf-format) (ASF) file container, Windows Media audio and video codecs, basic network streaming, and [Digital Rights Management](/windows/win32/wmformat/overview-of-windows-media-drm). | <!-- x64 --> 5,202&nbsp;KB | <!-- arm64 --> 8,908&nbsp;KB |
| | **[Microsoft-Windows-Media-Streaming](/Removable-Packages/Microsoft-Windows-Media-Streaming.md)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing support for [Windows Media Streaming](/windows/win32/mediastreaming/media-streaming-api-portal). | <!-- x64 --> 7,028&nbsp;KB | <!-- arm64 --> 10,195&nbsp;KB |
| | **[Microsoft-Windows-MediaPlayback-OC](/Removable-Packages/Microsoft-Windows-MediaPlayback-OC.md)** </br> Controls availability of the "Media Features" and "Windows Media Player" options for the *Turn Windows features on or off* user experience in Control Panel. | <!-- x64 --> 0&nbsp;KB | <!-- arm64 --> 0&nbsp;KB |
|✅| **[Microsoft-Windows-MicrosoftEdgeDevToolsClient](/Removable-Packages/Microsoft-Windows-MicrosoftEdgeDevToolsClient.md)** </br> | <!-- x64 --> 10,811&nbsp;KB | <!-- arm64 --> 10,792&nbsp;KB |
|✅| **[Microsoft-Windows-MobilePC-Client-Basic](/Removable-Packages/Microsoft-Windows-MobilePC-Client-Basic.md)** </br> | <!-- x64 --> 823&nbsp;KB | <!-- arm64 --> 797&nbsp;KB |
|✅| **[Microsoft-Windows-NetProfilesUX](/Removable-Packages/Microsoft-Windows-NetProfilesUX.md)** </br> | <!-- x64 --> 899&nbsp;KB | <!-- arm64 --> 1,106&nbsp;KB |
|✅| **[Microsoft-Windows-PEAuth-OneCore](/Removable-Packages/Microsoft-Windows-PEAuth-OneCore.md)** </br> | <!-- x64 --> 0&nbsp;KB | <!-- arm64 --> 0&nbsp;KB |
| | **[Microsoft-Windows-Portable-Devices](/Removable-Packages/Microsoft-Windows-Portable-Devices.md)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing connectivity to portable devices for [Windows Media Device Manager](/windows/win32/wmdm/windows-media-device-manager-architecture). | <!-- x64 --> 6,830&nbsp;KB | <!-- arm64 --> 7,979&nbsp;KB |
| | **[Microsoft-Windows-Printer-Drivers](/Removable-Packages/Microsoft-Windows-Printer-Drivers.md)** </br> Generic / Text Only, Generic IBM Graphics 9pin, Generic IBM Graphics 9-pin wide, MS Publisher Color Printer, MS Publisher Imagesetter, Microsoft Shared Fax Driver | <!-- x64 --> 8,578&nbsp;KB | <!-- arm64 --> 94&nbsp;KB |
| | **[Microsoft-Windows-Printing-PremiumTools](/Removable-Packages/Microsoft-Windows-Printing-PremiumTools.md)** </br> Print services migration command-line tool printbrm.exe | <!-- x64 --> 460&nbsp;KB | <!-- arm64 --> 397&nbsp;KB |
| | **[Microsoft-Windows-RecoveryDrive](/Removable-Packages/Microsoft-Windows-RecoveryDrive.md)** </br> Create a recovery drive user experience invoked from Control Panel - Recovery | <!-- x64 --> 473&nbsp;KB | <!-- arm64 --> 451&nbsp;KB |
| | **[Microsoft-Windows-ScreenSavers-3D](/Removable-Packages/Microsoft-Windows-ScreenSavers-3D.md)** </br> Screensavers: 3D Text, Bubbles, Mystify and Ribbons | <!-- x64 --> 1,396&nbsp;KB | <!-- arm64 --> 1,173&nbsp;KB |
| | **[Microsoft-Windows-SensorDataService](/Removable-Packages/Microsoft-Windows-SensorDataService.md)** </br> Component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) supporting data acquisition from  various sensors.  Supports Windows Hello.  | <!-- x64 --> 0&nbsp;KB | <!-- arm64 --> 0&nbsp;KB |
| | **[Microsoft-Windows-ShellOptions](/Removable-Packages/Microsoft-Windows-ShellOptions.md)** </br> Modern Calculator, Character Map, More Icons DLL | <!-- x64 --> 787&nbsp;KB | <!-- arm64 --> 745&nbsp;KB |
|✅| **[Microsoft-Windows-UI-Shell-WindowTabManager](/Removable-Packages/Microsoft-Windows-UI-Shell-WindowTabManager.md)** </br> | <!-- x64 --> 408&nbsp;KB | <!-- arm64 --> 947&nbsp;KB |
| | **[Microsoft-Windows-Shell-Wallpaper-Common](/Removable-Packages/Microsoft-Windows-Shell-Wallpaper-Common.md)** </br> Wallpaper images | <!-- x64 --> 21,493&nbsp;KB | <!-- arm64 --> 21,493&nbsp;KB |
| | **[Microsoft-Windows-WebcamExperience](/Removable-Packages/Microsoft-Windows-WebcamExperience.md)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing webcam user experience. | <!-- x64 --> 1,013&nbsp;KB | <!-- arm64 --> 980&nbsp;KB |
| | **[Microsoft-Windows-win32calc](/Removable-Packages/Microsoft-Windows-win32calc.md)** </br> Legacy Calculator Application | <!-- x64 --> 709&nbsp;KB | <!-- arm64 --> 704&nbsp;KB |
| | **[Microsoft-Windows-WinSATMediaFiles](/Removable-Packages/Microsoft-Windows-WinSATMediaFiles.md)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of media files for Windows System Assessment Tool. | <!-- x64 --> 0&nbsp;KB | <!-- arm64 --> 0&nbsp;KB |

# [Windows 10 IoT Enterprise LTSC 2021](#tab/LTSC2021)

The following packages can be removed from Windows IoT Enterprise LTSC 2021.  Select on each package name to see more details about the package payload.

| Removable Package  |  Approximate Size |
|:-------------------|------:|
| **[LanguageFeatures-Wordbreaking-Common-legacy](/Removable-Packages/LanguageFeatures-Wordbreaking-Common-legacy.md)** </br> Legacy neutral word breaker should only be needed in occasional application compatibility scenarios. | 1,542&nbsp;KB |
| **[Microsoft-Media-Foundation](/Removable-Packages/Microsoft-Media-Foundation.md)** </br> Component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk) enables the development of applications and components for using digital media. [Supported Media Formats in Media Foundation](/windows/win32/medfound/supported-media-formats-in-media-foundation).   | 63,747&nbsp;KB |
| **[Microsoft-OneCore-Fonts-DesktopFonts-NonLeanSupplement](/Removable-Packages/Microsoft-OneCore-Fonts-DesktopFonts-NonLeanSupplement.md)** </br> Fonts: [Malgun Gothic](/typography/font-list/malgun-gothic), [Microsoft JhengHei](/typography/font-list/microsoft-jhenghei), [Microsoft YaHei](/typography/font-list/microsoft-yahei), [Yu Gothic](/typography/font-list/yu-gothic) | 113,251&nbsp;KB |
| **[Microsoft-Windows-AppManagement-UEV)](/Removable-Packages/Microsoft-Windows-AppManagement-UEV.md)** </br> [User Experience Virtualization](/windows/configuration/ue-v/uev-for-windows) | 13,752&nbsp;KB |
| **[BMicrosoft-Windows-BioEnrollment-UX](/Removable-Packages/Microsoft-Windows-BioEnrollment-UX.md)** </br> [Windows Hello](/windows-hardware/design/device-experiences/windows-hello) | 3,589&nbsp;KB |
| **[Microsoft-Windows-BootEnvironment-Dvd](/Removable-Packages/Microsoft-Windows-BootEnvironment-Dvd.md)** </br> Boot from DVD | 9,108&nbsp;KB |
| **[Microsoft-Windows-Media-Format](/Removable-Packages/Microsoft-Windows-Media-Format.md)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of support for [Windows Media Device Manager](/windows/win32/wmdm/windows-media-device-manager-architecture),  [Advanced Systems Format](/windows/win32/wmformat/overview-of-the-asf-format) (ASF) file container, Windows Media audio and video codecs, basic network streaming, and [Digital Rights Management](/windows/win32/wmformat/overview-of-windows-media-drm). | 5,559&nbsp;KB |
| **[Microsoft-Windows-MediaPlayback-OC](/Removable-Packages/Microsoft-Windows-MediaPlayback-OC.md)** </br> Controls availability of the "Media Features" and "Windows Media Player" options for the *Turn Windows features on or off* user experience in Control Panel. | 0&nbsp;KB |
| **[Microsoft-Windows-Media-Streaming](/Removable-Packages/Microsoft-Windows-Media-Streaming.md)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing support for [Windows Media Streaming](/windows/win32/mediastreaming/media-streaming-api-portal). | 6,644&nbsp;KB |
| **[Microsoft-Windows-Portable-Devices](/Removable-Packages/Microsoft-Windows-Portable-Devices.md)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing connectivity to portable devices for [Windows Media Device Manager](/windows/win32/wmdm/windows-media-device-manager-architecture). | 6,405&nbsp;KB |
| **[Microsoft-Windows-Printer-Drivers](/Removable-Packages/Microsoft-Windows-Printer-Drivers.md)** </br> Generic / Text Only, Generic IBM Graphics 9pin, Generic IBM Graphics 9-pin wide, MS Publisher Color Printer, MS Publisher Imagesetter, Microsoft Shared Fax Driver | 8,200&nbsp;KB |
| **[Microsoft-Windows-Printing-PremiumTools](/Removable-Packages/Microsoft-Windows-Printing-PremiumTools.md)** </br> Print services migration command-line tool printbrm.exe | 381&nbsp;KB |
| **[Microsoft-Windows-RecoveryDrive](/Removable-Packages/Microsoft-Windows-RecoveryDrive.md)** </br> Create a recovery drive user experience invoked from Control Panel - Recovery | 1.041&nbsp;KB |
| **[Microsoft-Windows-ScreenSavers-3D](/Removable-Packages/Microsoft-Windows-ScreenSavers-3D.md)** </br> Screensavers: 3D Text, Bubbles, Mystify and Ribbons | 1,312&nbsp;KB |
| **[Microsoft-Windows-SensorDataService](/Removable-Packages/Microsoft-Windows-SensorDataService.md)** </br> Component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) supporting data acquisition from  various sensors.  Supports Windows Hello.  | 1,367&nbsp;KB |
| **[Microsoft-Windows-ShellOptions](/Removable-Packages/Microsoft-Windows-ShellOptions.md)** </br> Modern Calculator, Character Map, More Icons DLL | 657&nbsp;KB |
| **[Microsoft-Windows-Shell-Wallpaper-Common](/Removable-Packages/Microsoft-Windows-Shell-Wallpaper-Common.md)** </br> Wallpaper images |  8,538&nbsp;KB |
| **[Microsoft-Windows-WebcamExperience](/Removable-Packages/Microsoft-Windows-WebcamExperience.md)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing webcam user experience. | 1,394&nbsp;KB |
| **[Microsoft-Windows-win32calc](/Removable-Packages/Microsoft-Windows-win32calc.md)** </br> Legacy Calculator Application | 1,394&nbsp;KB |
| **[Microsoft-Windows-WinSATMediaFiles](/Removable-Packages/Microsoft-Windows-WinSATMediaFiles.md)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of media files for Windows System Assessment Tool. | 0&nbsp;KB |

---

## More Resources

- [Reduce Disk Footprint](/Reduce-Disk-Footprint)
- [Device Optimization Overview](/Overview)
- [Removable Packages Blog](https://aka.ms/RemovablePackagesBlog)
- [Removable Packages Script](https://aka.ms/RemovablePackagesScript)
