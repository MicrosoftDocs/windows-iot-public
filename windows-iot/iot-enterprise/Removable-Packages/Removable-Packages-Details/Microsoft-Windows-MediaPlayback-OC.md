---
title: Removable Packages
author: twarwick
ms.author: twarwick
ms.date: 12/7/2022
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Winodws-MediaPlayback-OC
keywords: IoT Enterprise, removable packages, storage
---

# Removable Package: Microsoft-Windows-MediaPlayback-OC
## Microsoft-Windows-MediaPlayback-OC
Supports Windows Media Player

Approximate on-disk footprint: 6,445

## Removing Package

### Online Servicing (audit mode)
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Online``` command-line parammeter to remove a single package via online servicing (audit mode).

```powershell
Dism.exe /Online /LogPath:%TEMP%\Microsoft-Windows-MediaPlayback-OC.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-MediaPlayback-OC /PackageName:@Package
````
### Offline Servicing
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Image:<image path>``` command-line parameter to remove a single package via offline servicing.

```powershell
Dism.exe /Image:c:\offline /LogPath:%TEMP%\Microsoft-Windows-MediaPlayback-OC.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-MediaPlayback-OC /PackageName:@Package
````

## Related Packages
- Microsoft-Media-Foundation
- Microsoft-Windows-Media-Format  
- Microsoft-Windows-Media-Streaming  
- Microsoft-Windows-MediaPlayback-OC  
- Microsoft-Windows-Portable-Devices  
- Microsoft-Windows-WebcamExperience  
- Microsoft-Windows-WinSATMediaFiles 


## File List
| File Name | Installed Location |
|-----------|--------------------|
|           |                    |
