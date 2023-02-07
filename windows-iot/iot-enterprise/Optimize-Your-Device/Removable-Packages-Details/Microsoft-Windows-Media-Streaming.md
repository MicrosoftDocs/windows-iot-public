---
title: Package - Windows Media Streaming
author: twarwick
ms.author: twarwick
ms.date: 1/12/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Windows-Media-Streaming
keywords: IoT Enterprise, removable packages, storage
---

# Package: Windows Media Streaming
** Applies to **
| Operating System                    |  Version            |
|:------------------------------------|:--------------------|
| Windows 10 IoT Enterprise LTSC 2021 | 19044.1741 or later |

## Description
A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing support for [Windows Media Streaming](/windows/win32/mediastreaming/media-streaming-api-portal).

**Package Name:**  Microsoft-Windows-Media-Streaming

**Size:** Approximately 6,644 KB

## To remove a package using DISM

1. To remove a specific package from the image type:
   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-Media-Streaming /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:
   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-Windows-Media-Streaming /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:
   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Windows-Media-Streaming /PackageName:@Package
   ````

## Related Packages
These packages collectively provide the functionality represented by the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture).  There are dependencies between each of these packages.  If you elect to remove a subset of these packages, it is recommended that you thoroughly test your scenarios to ensure that your customers do not encounter the interaction between the packages you retain and the packages that you remove.

- [Microsoft-Media-Foundation](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Media-Foundation)
- [Microsoft-Windows-Media-Format](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-Media-Format)
- [Microsoft-Windows-Media-Streaming](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-Media-Streaming) 
- [Microsoft-Windows-MediaPlayback-OC](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-MediaPlayback-OC)    
- [Microsoft-Windows-Portable-Devices](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-Portable-Devices)   
- [Microsoft-Windows-WebcamExperience](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-WebcamExperience) 
- [Microsoft-Windows-WinSATMediaFiles](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-WinSATMediaFiles) 

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

## More Resources
- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview)
