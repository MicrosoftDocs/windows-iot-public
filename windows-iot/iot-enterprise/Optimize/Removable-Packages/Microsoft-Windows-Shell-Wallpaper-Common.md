---
title: Package - Desktop Wallpaper
titleSuffix: Windows IoT Enterprise
author: twarwick
ms.author: twarwick
ms.date: 01/31/2024
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Removable Package Details for Microsoft-Windows-Shell-Wallpaper
keywords: IoT Enterprise, removable packages, storage
---

# Desktop Wallpaper

| Applies to                          |  Version            |
|:------------------------------------|:--------------------|
| Windows 10 IoT Enterprise LTSC 2021 | 19044.1741 or later |

## Description

Wallpaper images

**Package Name:** Microsoft-Windows-Shell-Wallpaper

**Size:** Approximately 8,538 KB

> [!IMPORTANT]
>
> This feature is only supported on the Windows IoT Entrprise LTSC edition.  If you choose to remove any of this package from Windows IoT Enterprise, you must ensure that your solution does not rely on functionality of the removed package. You cannot restore the package without a full reinstall of Windows IoT Enterprise LTSC.  
> For more information, see [Removable Packages System Requirements](../Removable-Packages.md#system-requirements).

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-Shell-Wallpaper /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-Windows-Shell-Wallpaper /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Windows-Shell-Wallpaper /PackageName:@Package
   ````

## File List

| File Name | Installed Location |
|-----------|--------------------|
| img0_1024x768.jpg  | %windir%\web\4k\wallpaper\windows\img0_1024x768.jpg |
| img0_1200x1920.jpg | %windir%\web\4k\wallpaper\windows\img0_1200x1920.jpg |
| img0_1366x768.jpg  | %windir%\web\4k\wallpaper\windows\img0_1366x768.jpg |
| img0_1600x2560.jpg | %windir%\web\4k\wallpaper\windows\img0_1600x2560.jpg |
| img0_2160x3840.jpg | %windir%\web\4k\wallpaper\windows\img0_2160x3840.jpg |
| img0_2560x1600.jpg | %windir%\web\4k\wallpaper\windows\img0_2560x1600.jpg |
| img0_3840x2160.jpg | %windir%\web\4k\wallpaper\windows\img0_3840x2160.jpg |
| img0_768x1024.jpg  | %windir%\web\4k\wallpaper\windows\img0_768x1024.jpg |
| img0_768x1366.jpg  | %windir%\web\4k\wallpaper\windows\img0_768x1366.jpg |
| desktop.ini        | %windir%\web\wallpaper\theme1\desktop.ini |
| img1.jpg           | %windir%\web\wallpaper\theme1\img1.jpg |
| img13.jpg          | %windir%\web\wallpaper\theme1\img13.jpg |
| img2.jpg           | %windir%\web\wallpaper\theme1\img2.jpg |
| img3.jpg           | %windir%\web\wallpaper\theme1\img3.jpg |
| img4.jpg           | %windir%\web\wallpaper\theme1\img4.jpg |
| desktop.ini        | %windir%\web\wallpaper\theme2\desktop.ini |
| img10.jpg          | %windir%\web\wallpaper\theme2\img10.jpg |
| img11.jpg          | %windir%\web\wallpaper\theme2\img11.jpg |
| img12.jpg          | %windir%\web\wallpaper\theme2\img12.jpg |
| img7.jpg           | %windir%\web\wallpaper\theme2\img7.jpg |
| img8.jpg           | %windir%\web\wallpaper\theme2\img8.jpg |
| img9.jpg           | %windir%\web\wallpaper\theme2\img9.jpg |
| img0.jpg           | %windir%\web\wallpaper\windows\img0.jpg |

## More Resources

- [Removable Packages](../Removable-Packages.md)
- [Device Optimization Overview](../Overview.md)
