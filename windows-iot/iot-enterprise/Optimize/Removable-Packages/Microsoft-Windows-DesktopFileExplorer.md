---
title: Package - Desktop File Explorer
author: twarwick
ms.author: twarwick
ms.date: 03/30/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Desktop File Explorer
keywords: IoT Enterprise, removable packages, storage
---

# Desktop File Explorer

> [!WARNING]
> THIS IS AN IN-PROGRESS ROUGH DRAFT. The wording and feature list may change before publishing.

Applies to:  
✅ Windows 11 IoT Enterprise LTSC 2024  
⛔ Windows 10 IoT Enterprise LTSC 2021

## Package Description

Package: **Microsoft-Windows-DesktopFileExplorer** </br>  `Add Description Here`

| Release                             |   x64     |    ARM64    |
|-------------------------------------|:---------:|:-----------:|
| Windows 11 IoT Enterprise LTSC 2024 | 2,738 KB  | 3,787 KB    |

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-DesktopFileExplorer /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-Windows-DesktopFileExplorer /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Windows-DesktopFileExplorer /PackageName:@Package
   ````

## File List

| File Name | Installed Location |
|-----------|--------------------|
| appxblockmap.xml | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\appxblockmap.xml |
| appxmanifest.xml | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\appxmanifest.xml |
| appxsignature.p7x | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\appxsignature.p7x |
| bitmdl2.ttf | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\bitmdl2.ttf |
| folder_large.scale-100.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\folder_large.scale-100.png |
| folder_large.scale-200.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\folder_large.scale-200.png |
| folder_large.scale-400.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\folder_large.scale-400.png |
| folder_small.scale-100.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\folder_small.scale-100.png |
| folder_small.scale-200.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\folder_small.scale-200.png |
| folder_small.scale-400.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\folder_small.scale-400.png |
| ppiremovablestoragedevicessquaretile150x150.scale-100.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\ppiremovablestoragedevicessquaretile150x150.scale-100.png |
| ppiremovablestoragedevicessquaretile150x150.scale-200.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\ppiremovablestoragedevicessquaretile150x150.scale-200.png |
| ppiremovablestoragedevicessquaretile150x150.scale-400.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\ppiremovablestoragedevicessquaretile150x150.scale-400.png |
| ppiremovablestoragedevicessquaretile44x44.scale-100.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\ppiremovablestoragedevicessquaretile44x44.scale-100.png |
| ppiremovablestoragedevicessquaretile44x44.scale-200.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\ppiremovablestoragedevicessquaretile44x44.scale-200.png |
| ppiremovablestoragedevicessquaretile44x44.scale-400.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\ppiremovablestoragedevicessquaretile44x44.scale-400.png |
| splashscreen.scale-100.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\splashscreen.scale-100.png |
| squaretile150x150.scale-100.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\squaretile150x150.scale-100.png |
| squaretile150x150.scale-200.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\squaretile150x150.scale-200.png |
| squaretile150x150.scale-400.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\squaretile150x150.scale-400.png |
| squaretile310x150.scale-100.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\squaretile310x150.scale-100.png |
| squaretile310x150.scale-200.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\squaretile310x150.scale-200.png |
| squaretile310x150.scale-400.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\squaretile310x150.scale-400.png |
| squaretile44x44.scale-100.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\squaretile44x44.scale-100.png |
| squaretile44x44.scale-200.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\squaretile44x44.scale-200.png |
| squaretile44x44.scale-400.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\squaretile44x44.scale-400.png |
| squaretile44x44.targetsize-24.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\squaretile44x44.targetsize-24.png |
| squaretile44x44.targetsize-256_altform-lightunplated_devicefamily-colorfulunplated.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\squaretile44x44.targetsize-256_altform-lightunplated_devicefamily-colorfulunplated.png |
| squaretile44x44.targetsize-256_altform-unplated_contrast-black_devicefamily-colorfulunplated.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\squaretile44x44.targetsize-256_altform-unplated_contrast-black_devicefamily-colorfulunplated.png |
| squaretile44x44.targetsize-256_altform-unplated_contrast-white_devicefamily-colorfulunplated.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\squaretile44x44.targetsize-256_altform-unplated_contrast-white_devicefamily-colorfulunplated.png |
| squaretile44x44.targetsize-256_altform-unplated_devicefamily-colorfulunplated.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\squaretile44x44.targetsize-256_altform-unplated_devicefamily-colorfulunplated.png |
| squaretile44x44.targetsize-48_altform-lightunplated_devicefamily-colorfulunplated.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\squaretile44x44.targetsize-48_altform-lightunplated_devicefamily-colorfulunplated.png |
| squaretile44x44.targetsize-48_altform-unplated_contrast-black_devicefamily-colorfulunplated.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\squaretile44x44.targetsize-48_altform-unplated_contrast-black_devicefamily-colorfulunplated.png |
| squaretile44x44.targetsize-48_altform-unplated_contrast-white_devicefamily-colorfulunplated.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\squaretile44x44.targetsize-48_altform-unplated_contrast-white_devicefamily-colorfulunplated.png |
| squaretile44x44.targetsize-48_altform-unplated_devicefamily-colorfulunplated.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\squaretile44x44.targetsize-48_altform-unplated_devicefamily-colorfulunplated.png |
| squaretile44x44.targetsize-96_altform-lightunplated_devicefamily-colorfulunplated.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\squaretile44x44.targetsize-96_altform-lightunplated_devicefamily-colorfulunplated.png |
| squaretile44x44.targetsize-96_altform-unplated_contrast-black_devicefamily-colorfulunplated.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\squaretile44x44.targetsize-96_altform-unplated_contrast-black_devicefamily-colorfulunplated.png |
| squaretile44x44.targetsize-96_altform-unplated_contrast-white_devicefamily-colorfulunplated.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\squaretile44x44.targetsize-96_altform-unplated_contrast-white_devicefamily-colorfulunplated.png |
| squaretile44x44.targetsize-96_altform-unplated_devicefamily-colorfulunplated.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\squaretile44x44.targetsize-96_altform-unplated_devicefamily-colorfulunplated.png |
| squaretile71x71.scale-100.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\squaretile71x71.scale-100.png |
| squaretile71x71.scale-200.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\squaretile71x71.scale-200.png |
| squaretile71x71.scale-400.png | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\assets\squaretile71x71.scale-400.png |
| fileexplorer.exe | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\fileexplorer.exe |
| resources.pri | %windir%\systemapps\microsoft.windows.fileexplorer_cw5n1h2txyewy\resources.pri |

## More Resources

- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview)
