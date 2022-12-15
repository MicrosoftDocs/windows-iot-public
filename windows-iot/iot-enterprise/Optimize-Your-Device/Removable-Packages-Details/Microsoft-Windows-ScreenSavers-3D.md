---
title: Removable Packages
author: twarwick
ms.author: twarwick
ms.date: 12/7/2022
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Windows-ScreenSavers-3d
keywords: IoT Enterprise, removable packages, storage
---

# Removable Package: Microsoft-Windows-ScreenSavers-3d
## Microsoft-Windows-ScreenSavers-3d
Screensavers: 3D Text, Bubbles, Mystify and Ribbons

Approximate on-disk footprint: 1,312 KB

## Removing Package

### Online Servicing (audit mode)
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Online``` command-line parammeter to remove a single package via online servicing (audit mode).

```powershell
Dism.exe /Online /LogPath:%WINDIR%\Temp\Microsoft-Windows-ScreenSavers-3d.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-ScreenSavers-3d /PackageName:@Package
````
### Offline Servicing
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Image:<image path>``` command-line parameter to remove a single package via offline servicing.

```powershell
Dism.exe /Image:c:\offline /LogPath:%WINDIR%\Temp\Microsoft-Windows-ScreenSavers-3d.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-ScreenSavers-3d /PackageName:@Package
````

## File List
| File Name    | Installed Location |
|-----------   |--------------------|
| bubbles.scr  | %windir%\system32\bubbles.scr |
| mystify.scr  | %windir%\system32\mystify.scr |
| ribbons.scr  | %windir%\system32\ribbons.scr |
| sstext3d.scr | %windir%\system32\sstext3d.scr |