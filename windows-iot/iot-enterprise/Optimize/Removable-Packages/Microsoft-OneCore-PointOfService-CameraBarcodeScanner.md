---
title: Package - Camera Barcode Scanner
titleSuffix: Windows IoT Enterprise
author: TerryWarwick
ms.author: twarwick
ms.date: 04/29/2024
ms.topic: reference
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Camera Barcode Scanner
keywords: IoT Enterprise, removable packages, storage
---

# Camera Barcode Scanner

Applies to:  
✅ Windows 11 IoT Enterprise LTSC 2024  
⛔ Windows 10 IoT Enterprise LTSC 2021

## Package Description

Package: **Microsoft-OneCore-PointOfService-CameraBarcodeScanner** </br>  Software decoder supporting detection of barcodes using a standard camera lens. For more information, see [Camera Barcode Decoder](/windows/uwp/devices-sensors/pos-camerabarcode).

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-OneCore-PointOfService-CameraBarcodeScanner /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-OneCore-PointOfService-CameraBarcodeScanner /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-OneCore-PointOfService-CameraBarcodeScanner /PackageName:@Package
   ````

## Package Details

### Package Size

| Release                             |   x64     |    ARM64    |
|-------------------------------------|:---------:|:-----------:|
| Windows 11 IoT Enterprise LTSC 2024 | 4,025 KB  | 4,664 KB    |

### File List

| File Name | Installed Location |
|-----------|--------------------|
| camerabarcodescannerpreview.exe | %windir%\systemapps\windows.cbspreview_cw5n1h2txyewy\camerabarcodescannerpreview.exe |
| app.xbf | %windir%\systemapps\windows.cbspreview_cw5n1h2txyewy\app.xbf |
| appxblockmap.xml | %windir%\systemapps\windows.cbspreview_cw5n1h2txyewy\appxblockmap.xml |
| appxmanifest.xml | %windir%\systemapps\windows.cbspreview_cw5n1h2txyewy\appxmanifest.xml |
| appxsignature.p7x | %windir%\systemapps\windows.cbspreview_cw5n1h2txyewy\appxsignature.p7x |
| assets\digimarc-logo.png | %windir%\systemapps\windows.cbspreview_cw5n1h2txyewy\assets\digimarc-logo.png |
| assets\splashscreen.png | %windir%\systemapps\windows.cbspreview_cw5n1h2txyewy\assets\splashscreen.png |
| assets\square150x150logo.png | %windir%\systemapps\windows.cbspreview_cw5n1h2txyewy\assets\square150x150logo.png |
| assets\square44x44logo.png | %windir%\systemapps\windows.cbspreview_cw5n1h2txyewy\assets\square44x44logo.png |
| assets\storelogo.png | %windir%\systemapps\windows.cbspreview_cw5n1h2txyewy\assets\storelogo.png |
| assets\wide310x150logo.png | %windir%\systemapps\windows.cbspreview_cw5n1h2txyewy\assets\wide310x150logo.png |
| mainpage.xbf | %windir%\systemapps\windows.cbspreview_cw5n1h2txyewy\mainpage.xbf |
| neutral.pri | %windir%\systemapps\windows.cbspreview_cw5n1h2txyewy\resources.pri |
| dmrcdecoder.dll | %windir%\system32\dmrcdecoder.dll |

## Related Content

- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview)
