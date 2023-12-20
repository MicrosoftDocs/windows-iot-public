---
title: Package - Supplemental Fonts
author: twarwick
ms.author: twarwick
ms.date: 03/30/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Fonts_DesktopFonts_NonLeanSupplement
keywords: IoT Enterprise, removable packages, storage
---

# Supplemental Fonts

Applies to:  
✅ Windows 11 IoT Enterprise LTSC 2024  
✅ Windows 10 IoT Enterprise LTSC 2021 (19044.1741 or later)  

## Package Description  

Package: **Microsoft-OneCore-Fonts-DesktopFonts-NonLeanSupplement** </br> Fonts: [Malgun Gothic](/typography/font-list/malgun-gothic), [Microsoft JhengHei](/typography/font-list/microsoft-jhenghei), [Microsoft YaHei](/typography/font-list/microsoft-yahei), [Yu Gothic](/typography/font-list/yu-gothic).

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Onecore-Fonts-DesktopFonts-NonLeanSupplement /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-Onecore-Fonts-DesktopFonts-NonLeanSupplement /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Onecore-Fonts-DesktopFonts-NonLeanSupplement /PackageName:@Package
   ````

## Package Details

### Package Size

| Release                             |   x64      |    ARM64    |
|-------------------------------------|:----------:|:-----------:|
| Windows 11 IoT Enterprise LTSC 2024 | 28,383 KB  | 28,383 KB   |
| Windows 10 IoT Enterprise LTSC 2021 | 113,251 KB |             |

### File List

| File Name     | Installed Location |
|---------------|--------------------|
| malgunbd.ttf | %windir%\fonts\malgunbd.ttf |
| malgunsl.ttf | %windir%\fonts\malgunsl.ttf |
| msjhbd.ttc | %windir%\fonts\msjhbd.ttc |
| msjhl.ttc | %windir%\fonts\msjhl.ttc  |
| msyhbd.ttc | %windir%\fonts\msyhbd.ttc |
| msyhl.ttc | %windir%\fonts\msyhl.ttc  |
| yugothb.ttc | %windir%\fonts\yugothb.ttc  |
| yugothl.ttc | %windir%\fonts\yugothl.ttc |
| yugothr.ttc | %windir%\fonts\yugothr.ttc |

## More Resources

- [Removable Packages](../Removable-Packages.md)
- [Reduce Disk Footprint](../Reduce-Disk-Footprint.md)
- [Device Optimization Overview](../Overview.md)
