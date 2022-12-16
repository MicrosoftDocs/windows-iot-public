---
title: Removable Package Microsoft-Windows-Shell-Wallpaper
author: twarwick
ms.author: twarwick
ms.date: 12/7/2022
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Windows-Shell-Wallpaper
keywords: IoT Enterprise, removable packages, storage
---

# Removable Package: Microsoft-Windows-Shell-Wallpaper
## Microsoft-Windows-Shell-Wallpaper
Wallpaper images

Approximate on-disk footprint: 8,538 KB

## Removing Package

### Online Servicing (audit mode)
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Online``` command-line parammeter to remove a single package via online servicing (audit mode).

```powershell
Dism.exe /Online /LogPath:%WINDIR%\Temp\Microsoft-Windows-Shell-Wallpaper.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-Shell-Wallpaper /PackageName:@Package
````
### Offline Servicing
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Image:<image path>``` command-line parameter to remove a single package via offline servicing.

```powershell
Dism.exe /Image:c:\offline /LogPath:%WINDIR%\Temp\Microsoft-Windows-Shell-Wallpaper.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-Shell-Wallpaper /PackageName:@Package
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
