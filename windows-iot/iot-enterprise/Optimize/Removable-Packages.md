---
title: Removable Packages Overview
titleSuffix: Windows IoT Enterprise
author: twarwick
ms.author: twarwick
ms.date: 05/22/2024
ms.topic: content
ms.service: windows-iot
ms.subservice: iot
description: Removable Packages is a Windows IoT Enterprise LTSC exclusive feature to assist with reducing disk footprint.
customerintent:
keywords: IoT Enterprise, removable packages, storage
---

# What is Removable Packages

Applies to:  
✅ Windows 11 IoT Enterprise LTSC 2024  
✅ Windows 10 IoT Enterprise LTSC 2021 (19044.1741 or later)  

## Overview

The methods described in this article allow a device builder to remove specific feature packages from Windows IoT Enterprise LTSC. These removable packages are in addition to the capabilities provided by [Enable or Disable Windows Features using DISM](/windows-hardware/manufacture/desktop/enable-or-disable-windows-features-using-dism) and [Features on Demand](/windows-hardware/manufacture/desktop/features-on-demand-v2--capabilities).

Using the desktop manufacturing process to [Modify a Windows image](/windows-hardware/manufacture/desktop/modify-an-image), a device maker can use either [Online servicing](/windows-hardware/manufacture/desktop/audit-mode-overview) or [Offline Servicing](/windows-hardware/manufacture/desktop/mount-and-modify-a-windows-image-using-dism) methods to completely remove packages supported packages from the [Windows Component Store](/windows-hardware/manufacture/desktop/manage-the-component-store). Once packages are removed from the Windows Component Store, they can't be added back to the operating system. Restoring removed packages requires a reinstallation of the operating system.

> [!IMPORTANT]
>
>If you choose to remove any of these packages from Windows IoT Enterprise, you must ensure that your  solution does not rely on functionality of the removed package(s). You cannot restore the package without a full reinstall of Windows IoT Enterprise LTSC.

## System Requirements

This feature is supported on Windows 10 IoT Enterprise LTSC 2021 (build 19044.1741) or later.

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

<!--markdownlint-disable-next-line -->
# [Windows 11 IoT Enterprise LTSC 2024](#tab/LTSC2024)

The following packages can be removed from Windows IoT Enterprise LTSC 2024. Select on each package name to see more details about the package payload.

<!-- Build 26021 -->
| New | Removable Package  | x64  | ARM64 |
|-----|:-------------------|-----:|-----:|
| | **[LanguageFeatures-Wordbreaking-Common-legacy](Removable-Packages/LanguageFeatures-Wordbreaking-Common-legacy.md)** </br> Legacy neutral word breaker should only be needed in occasional application compatibility scenarios. | <!-- x64 -->  1,568&nbsp;KB | <!-- arm64 --> 1,764&nbsp;KB |
| | **[Microsoft-Media-Foundation](Removable-Packages/Microsoft-Media-Foundation.md)** </br> Component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk) enables the development of applications and components for using digital media. [Supported Media Formats in Media Foundation](/windows/win32/medfound/supported-media-formats-in-media-foundation).   |  <!-- x64 --> 56,977&nbsp;KB | <!-- arm64 --> 99,584&nbsp;KB |
|✅| **[Microsoft-OneCore-Connectivity-UsbConnectorManager](Removable-Packages/Microsoft-OneCore-Connectivity-UsbConnectorManager.md)** </br> USB Connection Manager (UCM), USB Type-C port controller interface (TCPCI), and USB Type-C connector system software interface (UCSI) class extensions,  USB Connector and USB Policy Manager APIs. For more information, see [USB Type-C connector system software interface (UCSI) driver](/windows-hardware/drivers/usbcon/ucsi), [Write a USB Type-C port controller driver](/windows-hardware/drivers/usbcon/write-a-usb-type-c-port-controller-driver) and [Write a USB Type-connector driver](/windows-hardware/drivers/usbcon/bring-up-a-usb-type-c-connector-on-a-windows-system). | <!-- x64 -->  1,103&nbsp;KB | <!-- arm64 --> 863&nbsp;KB |
|✅| **[Microsoft-OneCore-Connectivity-UsbFunction](Removable-Packages/Microsoft-OneCore-Connectivity-UsbFunction.md)** </br> UFX, UFX Synopsis Events. For more information, see [Overview of developing Windows drivers for USB function controllers](/windows-hardware/drivers/usbcon/developing-windows-drivers-for-usb-function-controllers) and [Overview of developing Windows applications for USB devices](/windows-hardware/drivers/usbcon/developing-windows-applications-that-communicate-with-a-usb-device). | <!-- x64 --> 762&nbsp;KB | <!-- arm64 --> 646&nbsp;KB |
| | **[Microsoft-OneCore-Fonts-DesktopFonts-NonLeanSupplement](Removable-Packages/Microsoft-OneCore-Fonts-DesktopFonts-NonLeanSupplement.md)** </br> Fonts: [Malgun Gothic](/typography/font-list/malgun-gothic), [Microsoft JhengHei](/typography/font-list/microsoft-jhenghei), [Microsoft YaHei](/typography/font-list/microsoft-yahei), [Yu Gothic](/typography/font-list/yu-gothic) | <!-- x64 --> 28,383&nbsp;KB | <!-- arm64 --> 28,383&nbsp;KB |
|✅| **[Microsoft-OneCore-PointOfService-CameraBarcodeScanner](Removable-Packages/Microsoft-OneCore-PointOfService-CameraBarcodeScanner.md)** </br> Software decoder supporting detection of barcodes using a standard camera lens. For more information, see [Camera Barcode Decoder](/windows/uwp/devices-sensors/pos-camerabarcode). | <!-- x64 --> 4,025&nbsp;KB | <!-- arm64 --> 4,664&nbsp;KB |
|✅| **[Microsoft-OneCore-RemoteDesktopServices-Collaboration](Removable-Packages/Microsoft-OneCore-RemoteDesktopServices-Collaboration.md)** </br> Terminal Services Collaboration feature and sharer APIs. | <!-- x64 --> 1,460&nbsp;KB | <!-- arm64 --> 2,526&nbsp;KB |
|✅| **[Microsoft-OneCore-SD](Removable-Packages/Microsoft-OneCore-SD.md)** </br> SD Port and Dump SD Port. | <!-- x64 --> 956&nbsp;KB | <!-- arm64 --> 804&nbsp;KB |
|✅| **[Microsoft-OneCore-SystemSettings-Devices](Removable-Packages/Microsoft-OneCore-SystemSettings-Devices.md)** </br> Systems Settings handlers for Devices. | <!-- x64 --> 840&nbsp;KB | <!-- arm64 -->    997&nbsp;KB |
|✅| **[Microsoft-OneCore-SystemSettings-NetworkMobileHandlers](Removable-Packages/Microsoft-OneCore-SystemSettings-NetworkMobileHandlers.md)** </br> System Settings handlers for mobile network. | <!-- x64 --> 3,332&nbsp;KB | <!-- arm64 --> 3,832&nbsp;KB |
|✅| **[Microsoft-Windows-3DAudio-HrtfData](Removable-Packages/Microsoft-Windows-3DAudio-HrtfData.md)** </br> 3D Audio Head-related transfer function (HRTF) also known as Spatial Sound. For more information, see [Spatial Sound for App Developers](/windows/win32/coreaudio/spatial-sound). | <!-- x64 --> 6,171&nbsp;KB | <!-- arm64 --> 6,171&nbsp;KB |
| | **[Microsoft-Windows-AppManagement-UEV](Removable-Packages/Microsoft-Windows-AppManagement-UEV.md)** </br> [User Experience Virtualization](/windows/configuration/ue-v/uev-for-windows) | <!-- x64 --> 10,818&nbsp;KB | <!-- arm64 --> 0&nbsp;KB |
| | **[Microsoft-Windows-BioEnrollment-UX](Removable-Packages/Microsoft-Windows-BioEnrollment-UX.md)** </br> [Windows Hello](/windows-hardware/design/device-experiences/windows-hello) | <!-- x64 --> 3,483&nbsp;KB | <!-- arm64 --> 4,884&nbsp;KB |
| | **[Microsoft-Windows-BootEnvironment-Dvd](Removable-Packages/Microsoft-Windows-BootEnvironment-Dvd.md)** </br> Boot from DVD | <!-- x64 --> 6,224&nbsp;KB | <!-- arm64 --> 3,112&nbsp;KB |
|✅| **[Microsoft-Windows-ComputerManagerLauncher](Removable-Packages/Microsoft-Windows-ComputerManagerLauncher.md)** </br> Computer Management App and Computer Management Snap-in for the Microsoft Management Console (MMC). For more information, see [What is Microsoft Management Console?](/troubleshoot/windows-server/system-management-components/what-is-microsoft-management-console).| <!-- x64 --> 483&nbsp;KB | <!-- arm64 --> 610&nbsp;KB |
|✅| **[Microsoft-Windows-Defrag-UI](Removable-Packages/Microsoft-Windows-Defrag-UI.md)** </br> Defragment and Optimize Drives graphical user experience.  | <!-- x64 --> 604&nbsp;KB | <!-- arm64 --> 583&nbsp;KB |
|✅| **[Microsoft-Windows-DesktopFileExplorer](Removable-Packages/Microsoft-Windows-DesktopFileExplorer.md)** </br> A special version of File Explorer used in mixed-reality scenarios for navigating the file system. For more information, see [What is mixed reality?](/windows/mixed-reality/discover/mixed-reality) | <!-- x64 --> 2,757&nbsp;KB | <!-- arm64 --> 3,818&nbsp;KB |
| | **[Microsoft-Windows-Media-Format](Removable-Packages/Microsoft-Windows-Media-Format.md)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of support for [Windows Media Device Manager](/windows/win32/wmdm/windows-media-device-manager-architecture),  [Advanced Systems Format](/windows/win32/wmformat/overview-of-the-asf-format) (ASF) file container, Windows Media audio and video codecs, basic network streaming, and [Digital Rights Management](/windows/win32/wmformat/overview-of-windows-media-drm). | <!-- x64 --> 5,200&nbsp;KB | <!-- arm64 --> 8,764&nbsp;KB |
| | **[Microsoft-Windows-Media-Streaming](Removable-Packages/Microsoft-Windows-Media-Streaming.md)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing support for [Windows Media Streaming](/windows/win32/mediastreaming/media-streaming-api-portal). | <!-- x64 --> 7,030&nbsp;KB | <!-- arm64 --> 10,264&nbsp;KB |
| | **[Microsoft-Windows-MediaPlayback-OC](Removable-Packages/Microsoft-Windows-MediaPlayback-OC.md)** </br> Controls availability of the "Media Features" and "Windows Media Player" options for the *Turn Windows features on or off* user experience in Control Panel. | <!-- x64 --> 0&nbsp;KB | <!-- arm64 --> 0&nbsp;KB |
|✅| **[Microsoft-Windows-MicrosoftEdgeDevToolsClient](Removable-Packages/Microsoft-Windows-MicrosoftEdgeDevToolsClient.md)** </br> Microsoft Edge developer tools. For more information, see [Microsoft Edge DevTools documentation](/microsoft-edge/devtools-guide-chromium/landing/). | <!-- x64 --> 10,816&nbsp;KB | <!-- arm64 --> 10,797&nbsp;KB |
|✅| **[Microsoft-Windows-MobilePC-Client-Basic](Removable-Packages/Microsoft-Windows-MobilePC-Client-Basic.md)** </br> Windows Mobility Center Control Panel application. | <!-- x64 --> 827&nbsp;KB | <!-- arm64 --> 796&nbsp;KB |
|✅| **[Microsoft-Windows-NetProfilesUX](Removable-Packages/Microsoft-Windows-NetProfilesUX.md)** </br> Network and Sharing Center Control Panel application. | <!-- x64 --> 899&nbsp;KB | <!-- arm64 --> 1,115&nbsp;KB |
|✅| **[Microsoft-Windows-PEAuth-OneCore](Removable-Packages/Microsoft-Windows-PEAuth-OneCore.md)** </br> Protected Environment authorization supporting playback of protected media. For more information, see [How to Play Protected Media Files](/windows/win32/medfound/how-to-play-protected-media-files). | <!-- x64 --> 0&nbsp;KB | <!-- arm64 --> 0&nbsp;KB |
| | **[Microsoft-Windows-Portable-Devices](Removable-Packages/Microsoft-Windows-Portable-Devices.md)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing connectivity to portable devices for [Windows Media Device Manager](/windows/win32/wmdm/windows-media-device-manager-architecture). | <!-- x64 --> 6,847&nbsp;KB | <!-- arm64 --> 8,037&nbsp;KB |
| | **[Microsoft-Windows-Printer-Drivers](Removable-Packages/Microsoft-Windows-Printer-Drivers.md)** </br> Generic / Text Only, Generic IBM Graphics 9pin, Generic IBM Graphics 9-pin wide, MS Publisher Color Printer, MS Publisher Imagesetter, Microsoft Shared Fax Driver | <!-- x64 --> 8,592&nbsp;KB | <!-- arm64 --> 94&nbsp;KB |
| | **[Microsoft-Windows-Printing-PremiumTools](Removable-Packages/Microsoft-Windows-Printing-PremiumTools.md)** </br> Print services migration command-line tool printbrm.exe | <!-- x64 --> 460&nbsp;KB | <!-- arm64 --> 397&nbsp;KB |
| | **[Microsoft-Windows-RecoveryDrive](Removable-Packages/Microsoft-Windows-RecoveryDrive.md)** </br> Create a recovery drive user experience invoked from Control Panel - Recovery | <!-- x64 --> 473&nbsp;KB | <!-- arm64 --> 451&nbsp;KB |
| | **[Microsoft-Windows-ScreenSavers-3D](Removable-Packages/Microsoft-Windows-ScreenSavers-3D.md)** </br> Screensavers: 3D Text, Bubbles, Mystify, and Ribbons | <!-- x64 --> 1,400&nbsp;KB | <!-- arm64 --> 1,173&nbsp;KB |
| | **[Microsoft-Windows-SensorDataService](Removable-Packages/Microsoft-Windows-SensorDataService.md)** </br> Component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) supporting data acquisition from  various sensors. Supports Windows Hello.  | <!-- x64 --> 0&nbsp;KB | <!-- arm64 --> 0&nbsp;KB |
| | **[Microsoft-Windows-ShellOptions](Removable-Packages/Microsoft-Windows-ShellOptions.md)** </br> Modern Calculator, Character Map, More Icons DLL | <!-- x64 --> 783&nbsp;KB | <!-- arm64 --> 748&nbsp;KB |
|✅| **[Microsoft-Windows-UI-Shell-WindowTabManager](Removable-Packages/Microsoft-Windows-UI-Shell-WindowTabManager.md)** </br> Lets an app manage the relationship between its in-app UI tabs and representations of the tabs in the system shell UI. For more information, see [WindowTabManager Class](/uwp/api/windows.ui.shell.windowtabmanager). | <!-- x64 --> 404&nbsp;KB | <!-- arm64 --> 953&nbsp;KB |
| | **[Microsoft-Windows-Shell-Wallpaper-Common](Removable-Packages/Microsoft-Windows-Shell-Wallpaper-Common.md)** </br> Wallpaper images | <!-- x64 --> 21,493&nbsp;KB | <!-- arm64 --> 21,493&nbsp;KB |
| | **[Microsoft-Windows-WebcamExperience](Removable-Packages/Microsoft-Windows-WebcamExperience.md)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing webcam user experience. | <!-- x64 --> 1,018&nbsp;KB | <!-- arm64 --> 986&nbsp;KB |
| | **[Microsoft-Windows-win32calc](Removable-Packages/Microsoft-Windows-win32calc.md)** </br> Legacy Calculator Application | <!-- x64 --> 709&nbsp;KB | <!-- arm64 --> 703&nbsp;KB |
| | **[Microsoft-Windows-WinSATMediaFiles](Removable-Packages/Microsoft-Windows-WinSATMediaFiles.md)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of media files for Windows System Assessment Tool. | <!-- x64 --> 0&nbsp;KB | <!-- arm64 --> 0&nbsp;KB |

<!--markdownlint-disable-next-line -->
# [Windows 10 IoT Enterprise LTSC 2021](#tab/LTSC2021)

The following packages can be removed from Windows IoT Enterprise LTSC 2021. Select on each package name to see more details about the package payload.

| Removable Package  |  Approximate Size |
|:-------------------|------:|
| **[LanguageFeatures-Wordbreaking-Common-legacy](Removable-Packages/LanguageFeatures-Wordbreaking-Common-legacy.md)** </br> Legacy neutral word breaker should only be needed in occasional application compatibility scenarios. | 1,542&nbsp;KB |
| **[Microsoft-Media-Foundation](Removable-Packages/Microsoft-Media-Foundation.md)** </br> Component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk) enables the development of applications and components for using digital media. [Supported Media Formats in Media Foundation](/windows/win32/medfound/supported-media-formats-in-media-foundation).   | 63,747&nbsp;KB |
| **[Microsoft-OneCore-Fonts-DesktopFonts-NonLeanSupplement](Removable-Packages/Microsoft-OneCore-Fonts-DesktopFonts-NonLeanSupplement.md)** </br> Fonts: [Malgun Gothic](/typography/font-list/malgun-gothic), [Microsoft JhengHei](/typography/font-list/microsoft-jhenghei), [Microsoft YaHei](/typography/font-list/microsoft-yahei), [Yu Gothic](/typography/font-list/yu-gothic) | 113,251&nbsp;KB |
| **[Microsoft-Windows-AppManagement-UEV)](Removable-Packages/Microsoft-Windows-AppManagement-UEV.md)** </br> [User Experience Virtualization](/windows/configuration/ue-v/uev-for-windows) | 13,752&nbsp;KB |
| **[BMicrosoft-Windows-BioEnrollment-UX](Removable-Packages/Microsoft-Windows-BioEnrollment-UX.md)** </br> [Windows Hello](/windows-hardware/design/device-experiences/windows-hello) | 3,589&nbsp;KB |
| **[Microsoft-Windows-BootEnvironment-Dvd](Removable-Packages/Microsoft-Windows-BootEnvironment-Dvd.md)** </br> Boot from DVD | 9,108&nbsp;KB |
| **[Microsoft-Windows-Media-Format](Removable-Packages/Microsoft-Windows-Media-Format.md)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of support for [Windows Media Device Manager](/windows/win32/wmdm/windows-media-device-manager-architecture),  [Advanced Systems Format](/windows/win32/wmformat/overview-of-the-asf-format) (ASF) file container, Windows Media audio and video codecs, basic network streaming, and [Digital Rights Management](/windows/win32/wmformat/overview-of-windows-media-drm). | 5,559&nbsp;KB |
| **[Microsoft-Windows-MediaPlayback-OC](Removable-Packages/Microsoft-Windows-MediaPlayback-OC.md)** </br> Controls availability of the "Media Features" and "Windows Media Player" options for the *Turn Windows features on or off* user experience in Control Panel. | 0&nbsp;KB |
| **[Microsoft-Windows-Media-Streaming](Removable-Packages/Microsoft-Windows-Media-Streaming.md)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing support for [Windows Media Streaming](/windows/win32/mediastreaming/media-streaming-api-portal). | 6,644&nbsp;KB |
| **[Microsoft-Windows-Portable-Devices](Removable-Packages/Microsoft-Windows-Portable-Devices.md)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing connectivity to portable devices for [Windows Media Device Manager](/windows/win32/wmdm/windows-media-device-manager-architecture). | 6,405&nbsp;KB |
| **[Microsoft-Windows-Printer-Drivers](Removable-Packages/Microsoft-Windows-Printer-Drivers.md)** </br> Generic / Text Only, Generic IBM Graphics 9pin, Generic IBM Graphics 9-pin wide, MS Publisher Color Printer, MS Publisher Imagesetter, Microsoft Shared Fax Driver | 8,200&nbsp;KB |
| **[Microsoft-Windows-Printing-PremiumTools](Removable-Packages/Microsoft-Windows-Printing-PremiumTools.md)** </br> Print services migration command-line tool printbrm.exe | 381&nbsp;KB |
| **[Microsoft-Windows-RecoveryDrive](Removable-Packages/Microsoft-Windows-RecoveryDrive.md)** </br> Create a recovery drive user experience invoked from Control Panel - Recovery | 1.041&nbsp;KB |
| **[Microsoft-Windows-ScreenSavers-3D](Removable-Packages/Microsoft-Windows-ScreenSavers-3D.md)** </br> Screensavers: 3D Text, Bubbles, Mystify, and Ribbons | 1,312&nbsp;KB |
| **[Microsoft-Windows-SensorDataService](Removable-Packages/Microsoft-Windows-SensorDataService.md)** </br> Component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) supporting data acquisition from  various sensors. Supports Windows Hello.  | 1,367&nbsp;KB |
| **[Microsoft-Windows-ShellOptions](Removable-Packages/Microsoft-Windows-ShellOptions.md)** </br> Modern Calculator, Character Map, More Icons DLL | 657&nbsp;KB |
| **[Microsoft-Windows-Shell-Wallpaper-Common](Removable-Packages/Microsoft-Windows-Shell-Wallpaper-Common.md)** </br> Wallpaper images |  8,538&nbsp;KB |
| **[Microsoft-Windows-WebcamExperience](Removable-Packages/Microsoft-Windows-WebcamExperience.md)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing webcam user experience. | 1,394&nbsp;KB |
| **[Microsoft-Windows-win32calc](Removable-Packages/Microsoft-Windows-win32calc.md)** </br> Legacy Calculator Application | 1,394&nbsp;KB |
| **[Microsoft-Windows-WinSATMediaFiles](Removable-Packages/Microsoft-Windows-WinSATMediaFiles.md)** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of media files for Windows System Assessment Tool. | 0&nbsp;KB |

---

## Related content

- [Device Optimization Overview](Overview.md)
- [Removable Packages Blog](https://aka.ms/RemovablePackagesBlog)
- [Removable Packages Script](https://aka.ms/RemovablePackagesScript)
