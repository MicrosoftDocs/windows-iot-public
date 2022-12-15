---
title: Removable Packages
author: twarwick
ms.author: twarwick
ms.date: 12/7/2022
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Windows-Media-Streaming
keywords: IoT Enterprise, removable packages, storage
---

# Removable Package: Microsoft-Windows-Media-Streaming
## Microsoft-Windows-Media-Streaming
Provides support for [Windows Media Streaming](/windows/win32/mediastreaming/media-streaming-api-portal)

Approximate on-disk footprint: 6,644 KB

## Removing Package

### Online Servicing (audit mode)
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Online``` command-line parammeter to remove a single package via online servicing (audit mode).

```powershell
Dism.exe /Online /LogPath:%WINDIR%\Temp\Microsoft-Windows-Media-Streaming.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-Media-Streaming /PackageName:@Package
````
### Offline Servicing
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Image:<image path>``` command-line parameter to remove a single package via offline servicing.

```powershell
Dism.exe /Image:c:\offline /LogPath:%WINDIR%\Temp\Microsoft-Windows-Media-Streaming.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-Media-Streaming /PackageName:@Package
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
| File Name                         | Installed Location |
|-----------------------------------|--------------------|
| castingshellext.dll	            | %windir%\system32\castingshellext.dll
| dlnashext.dll                     | %windir%\system32\dlnashext.dll
| dmrserver.dll	                    | %windir%\system32\dmrserver.dll
| mdeserver.exe	                    | %windir%\system32\mdeserver.exe
| playtoreceiver.dll	            | %windir%\system32\playtoreceiver.dll
| windows.media.streaming.dll	    | %windir%\system32\windows.media.streaming.dll
| windows.media.streaming.ps.dll    | %windir%\system32\windows.media.streaming.ps.dll
| winmde.dll	                    | %windir%\system32\winmde.dll
| wmpdmc.exe	                    | %windir%\system32\wmpdmc.exe
| wmpdui.dll	                    | %windir%\system32\wmpdui.dll

