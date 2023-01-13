---
title: Removable Package Microsoft-Windows-Media-Format
author: twarwick
ms.author: twarwick
ms.date: 12/20/2022
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Windows-Media-Format
keywords: IoT Enterprise, removable packages, storage
---

# Removable Package: Microsoft-Windows-Media-Format
## Microsoft-Windows-Media-Format
A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of support for [Windows Media Device Manager](/windows/win32/wmdm/windows-media-device-manager-architecture),  [Advanced Systems Format](/windows/win32/wmformat/overview-of-the-asf-format) (ASF) file container, Windows Media audio and video codecs, basic network streaming, and [Digital Rights Management](/windows/win32/wmformat/overview-of-windows-media-drm).

Approximate on-disk footprint: 5,559 KB

## Removing Package

### Online Servicing 
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Online``` command-line parameter to remove a single package via online servicing.

```powershell
Dism.exe /Online /LogPath:%WINDIR%\Temp\Microsoft-Windows-BootEnvironment-Dvd.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-BootEnvironment-Dvd /PackageName:@Package
````
### Offline Servicing
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Image:<image path>``` command-line parameter to remove a single package via offline servicing.

```powershell
Dism.exe /Image:c:\offline /LogPath:%WINDIR%\Temp\Microsoft-Windows-BootEnvironment-Dvd.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-BootEnvironment-Dvd /PackageName:@Package
````

## Related Packages
These packages collectively provide the functionality represented by the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture).  There are dependencies between each of these packages.  If you elect to remove a subset of these packages, it is recommended that you thoroughly test your scenarios to ensure that your customers do not encounter the interaction between the packages you retain and the packages that you remove.

- [Microsoft-Media-Foundation](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Media-Foundation)
- [Microsoft-Windows-Media-Format](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-Media-Format)
- [Microsoft-Windows-Media-Streaming](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-Media-Streaming) 
- [Microsoft-Windows-MediaPlayback-OC](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-MediaPlayback-OC)    
- [Microsoft-Windows-Portable-Devices](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-Portable-Devices)   
- [Microsoft-Windows-WebcamExperience](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-WebcamExperience.md) 
- [Microsoft-Windows-WinSATMediaFiles](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-WinSATMediaFiles.md) 

## File List
| File Name | Installed Location |
|-----------|--------------------|
| asferror.dll			| %windir%\system32\asferror.dll
| cewmdm.dll			| %windir%\system32\cewmdm.dll
| laprxy.dll			| %windir%\system32\laprxy.dll
| logagent.exe			| %windir%\system32\logagent.exe
| mswmdm.dll			| %windir%\system32\mswmdm.dll
| mswmdm.mof			| %windir%\system32\wbem\mswmdm.mof
| sqmapi.dll			| %programfiles%\windows multimedia platform\sqmapi.dll
| windowsmediadrm.admx 	| %windir%\policydefinitions\windowsmediadrm.admx |
| wmasf.dll				| %windir%\system32\wmasf.dll
| wmdmlog.dll			| %windir%\system32\wmdmlog.dll
| wmdmps.dll			| %windir%\system32\wmdmps.dll
| wmidx.dll				| %windir%\system32\wmidx.dll
| wmnetmgr.dll			| %windir%\system32\wmnetmgr.dll
| wmsyspr9.prx			| %windir%\wmsyspr9.prx
| wmvcore.dll			| %windir%\system32\wmvcore.dll

## More Resources
- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Removable-Packages.md)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint.md)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview.md)
