---
title: Package - 3D Screensavers
titleSuffix: Windows IoT Enterprise
author: TerryWarwick
ms.author: twarwick
ms.date: 02/13/2024
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Removable Package Details for Microsoft-Windows-ScreenSavers-3d
keywords: IoT Enterprise, removable packages, storage
---

# 3D  Screensavers

Applies to:  
✅ Windows 11 IoT Enterprise LTSC 2024  
✅ Windows 10 IoT Enterprise LTSC 2021 (19044.1741 or later)  

## Package Description

Package: **Microsoft-Windows-ScreenSavers-3D** </br> Screensavers: 3D Text, Bubbles, Mystify, and Ribbons.

> [!IMPORTANT]
>
> This feature is only supported on the Windows IoT Entrprise LTSC edition.  If you choose to remove any of this package from Windows IoT Enterprise, you must ensure that your solution does not rely on functionality of the removed package. You cannot restore the package without a full reinstall of Windows IoT Enterprise LTSC.  
> For more information, see [Removable Packages System Requirements](../Removable-Packages.md#system-requirements).

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-ScreenSavers-3d /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-Windows-ScreenSavers-3d /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Windows-ScreenSavers-3d /PackageName:@Package
   ````

## Package Details

### Package Size

| Release                             |   x64     |    ARM64    |
|-------------------------------------|:---------:|:-----------:|
| Windows 11 IoT Enterprise LTSC 2024 | 1,396 KB  | 1,173 KB    |
| Windows 10 IoT Enterprise LTSC 2021 | 1,312 KB  |             |

### File List

| File Name    | Installed Location |
|-----------   |--------------------|
| bubbles.scr  | %windir%\system32\bubbles.scr |
| mystify.scr  | %windir%\system32\mystify.scr |
| ribbons.scr  | %windir%\system32\ribbons.scr |
| sstext3d.scr | %windir%\system32\sstext3d.scr |

## More Resources

- [Removable Packages](../Removable-Packages.md)
- [Device Optimization Overview](../Overview.md)
