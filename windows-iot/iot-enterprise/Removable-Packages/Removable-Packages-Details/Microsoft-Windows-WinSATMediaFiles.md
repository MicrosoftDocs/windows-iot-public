---
title: Removable Packages
author: twarwick
ms.author: twarwick
ms.date: 12/7/2022
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Windows-WinSATMediaFiles
keywords: IoT Enterprise, removable packages, storage
---

# Removable Package: Microsoft-Windows-WinSATMediaFiles
## Microsoft-Windows-WinSATMediaFiles
Media files for Windows System Assessment Tool

Approximate on-disk footprint: TBD


## Removing Package

### Online Servicing (audit mode)
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Online``` command-line parammeter to remove a single package via online servicing (audit mode).

```powershell
Dism.exe /Online /LogPath:%WINDIR%\Temp\Microsoft-Windows-WinSATMediaFiles.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-WinSATMediaFiles /PackageName:@Package
````
### Offline Servicing
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Image:<image path>``` command-line parameter to remove a single package via offline servicing.

```powershell
Dism.exe /Image:c:\offline /LogPath:%WINDIR%\Temp\Microsoft-Windows-WinSATMediaFiles.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-WinSATMediaFiles /PackageName:@Package
````

## Related Packages
These packages collectively provide the functionality represented by the the [Media Feature Pack](https://learn.microsoft.com/en-us/windows/win32/wmdm/windows-media-device-manager-architecture).  There are dependencies between each of these packages.  Although it is possible, it is not recommended to remove a subset of these packages.
- [Microsoft-Media-Foundation](/windows/iot/iot-enterprise/Removable-Packages/Removable-Packages-Details/Microsoft-Media-Foundation)
- [Microsoft-Windows-Media-Format](/windows/iot/iot-enterprise/Removable-Packages/Removable-Packages-Details/Microsoft-Windows-Media-Format)
- [Microsoft-Windows-Media-Streaming](/windows/iot/iot-enterprise/Removable-Packages/Removable-Packages-Details/Microsoft-Windows-Media-Streaming) 
- [Microsoft-Windows-MediaPlayback-OC](/windows/iot/iot-enterprise/Removable-Packages/Removable-Packages-Details/Microsoft-Windows-MediaPlayback-OC)    
- [Microsoft-Windows-Portable-Devices](/windows/iot/iot-enterprise/Removable-Packages/Removable-Packages-Details/Microsoft-Windows-Portable-Devices)   
- [Microsoft-Windows-WebcamExperience](/windows/iot/iot-enterprise/Removable-Packages/Removable-Packages-Details/Microsoft-Windows-WebcamExperience.md) 
- [Microsoft-Windows-WinSATMediaFiles](/windows/iot/iot-enterprise/Removable-Packages/Removable-Packages-Details/Microsoft-Windows-WinSATMediaFiles.md) 

## File List
| File Name | Installed Location |
|-----------|--------------------|
|           |                    |
