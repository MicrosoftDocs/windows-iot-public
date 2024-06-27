---
title: Package - Desktop Wallpaper
titleSuffix: Windows IoT Enterprise
author: TerryWarwick
ms.author: twarwick
ms.date: 05/22/2024
ms.topic: reference
ms.service: windows-iot
ms.subservice: iot
description: Removable Package Details for Microsoft-Windows-Shell-Wallpaper
keywords: IoT Enterprise, removable packages, storage
---

# Desktop Wallpaper

Applies to:  
✅ Windows 11 IoT Enterprise LTSC 2024  
✅ Windows 10 IoT Enterprise LTSC 2021 (19044.1741 or later)  

## Package Description

Package: **Microsoft-Windows-Shell-Wallpaper-Common** </br> Wallpaper images.

> [!IMPORTANT]
>
> This feature is only supported on the Windows IoT Enterprise LTSC edition.  If you choose to remove any of this package from Windows IoT Enterprise, you must ensure that your solution does not rely on functionality of the removed package. You cannot restore the package without a full reinstall of Windows IoT Enterprise LTSC.  
> For more information, see [Removable Packages System Requirements](../Removable-Packages.md#system-requirements).

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-Shell-Wallpaper-Common /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-Windows-Shell-Wallpaper-Common /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Windows-Shell-Wallpaper-Common /PackageName:@Package
   ````

## Package Details

### Package Size

| Release                             |   x64     |    ARM64    |
|-------------------------------------|:---------:|:-----------:|
| Windows 11 IoT Enterprise LTSC 2024 | 21,493 KB | 21,493 KB   |
| Windows 10 IoT Enterprise LTSC 2021 | 8,538 KB  |             |

### File List

| File Name | Installed Location |
|-----------|--------------------|
| img0.jpg | %windir%\web\wallpaper\windows\img0.jpg |
| img0_1920x1200.jpg | %windir%\web\4k\wallpaper\windows\img0_1920x1200.jpg |
| img14.jpg | %windir%\web\wallpaper\spotlight\img14.jpg |
| img19.jpg | %windir%\web\wallpaper\windows\img19.jpg |
| img19_1920x1200.jpg | %windir%\web\4k\wallpaper\windows\img19_1920x1200.jpg |
| img20.jpg | %windir%\web\wallpaper\themea\img20.jpg |
| img21.jpg | %windir%\web\wallpaper\themea\img21.jpg |
| img22.jpg | %windir%\web\wallpaper\themea\img22.jpg |
| img23.jpg | %windir%\web\wallpaper\themea\img23.jpg |
| img24.jpg | %windir%\web\wallpaper\themeb\img24.jpg |
| img25.jpg | %windir%\web\wallpaper\themeb\img25.jpg |
| img26.jpg | %windir%\web\wallpaper\themeb\img26.jpg |
| img27.jpg | %windir%\web\wallpaper\themeb\img27.jpg |
| img28.jpg | %windir%\web\wallpaper\themec\img28.jpg |
| img29.jpg | %windir%\web\wallpaper\themec\img29.jpg |
| img30.jpg | %windir%\web\wallpaper\themec\img30.jpg |
| img31.jpg | %windir%\web\wallpaper\themec\img31.jpg |
| img32.jpg | %windir%\web\wallpaper\themed\img32.jpg |
| img33.jpg | %windir%\web\wallpaper\themed\img33.jpg |
| img34.jpg | %windir%\web\wallpaper\themed\img34.jpg |
| img35.jpg | %windir%\web\wallpaper\themed\img35.jpg |
| img50.jpg | %windir%\web\wallpaper\spotlight\img50.jpg |
| themea.ini | %windir%\web\wallpaper\themea\desktop.ini |
| themeb.ini | %windir%\web\wallpaper\themeb\desktop.ini |
| themec.ini | %windir%\web\wallpaper\themec\desktop.ini |
| themed.ini | %windir%\web\wallpaper\themed\desktop.ini |

## Related Content

- [Removable Packages](../Removable-Packages.md)
- [Device Optimization Overview](../Overview.md)
