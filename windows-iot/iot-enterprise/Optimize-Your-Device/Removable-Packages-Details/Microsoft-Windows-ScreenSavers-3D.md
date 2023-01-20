---
title: Package - 3D Screensavers
author: twarwick
ms.author: twarwick
ms.date: 1/12/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Windows-ScreenSavers-3d
keywords: IoT Enterprise, removable packages, storage
---

# Package: 3D Screensavers

## Description
Screensavers: 3D Text, Bubbles, Mystify and Ribbons

**Package Name:** Microsoft-Windows-ScreenSavers-3dMicrosoft-Windows-ScreenSavers-3d

**Size:** Approximately 1,312 KB

## Removing Package

### Online Servicing 
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Online``` command-line parameter to remove a single package via online servicing.

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

## More Resources
- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview)
