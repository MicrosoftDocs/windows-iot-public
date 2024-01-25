---
title: Package - Windows Media Format
author: twarwick
ms.author: twarwick
ms.date: 03/30/2023
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Removable Package Details for Microsoft-Windows-Media-Format
keywords: IoT Enterprise, removable packages, storage
---

# Windows Media Format

Applies to:  
✅ Windows 11 IoT Enterprise LTSC 2024  
✅ Windows 10 IoT Enterprise LTSC 2021 (19044.1741 or later)  

## Package Description  

Package: **Microsoft-Windows-Media-Format** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) comprised of support for [Windows Media Device Manager](/windows/win32/wmdm/windows-media-device-manager-architecture),  [Advanced Systems Format](/windows/win32/wmformat/overview-of-the-asf-format) (ASF) file container, Windows Media audio and video codecs, basic network streaming, and [Digital Rights Management](/windows/win32/wmformat/overview-of-windows-media-drm).

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-Media-Format /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-Windows-Media-Format /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Windows-Media-Format /PackageName:@Package
   ````

## Related Packages

These packages collectively provide the functionality represented by the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture).  There are dependencies between each of these packages.  If you elect to remove a subset of these packages, it is recommended that you thoroughly test your scenarios to ensure that your customers do not encounter the interaction between the packages you retain and the packages that you remove.

- [Microsoft-Media-Foundation](Microsoft-Media-Foundation.md)
- [Microsoft-Windows-Media-Format](Microsoft-Windows-Media-Format.md)
- [Microsoft-Windows-Media-Streaming](Microsoft-Windows-Media-Streaming.md)
- [Microsoft-Windows-MediaPlayback-OC](Microsoft-Windows-MediaPlayback-OC.md)
- [Microsoft-Windows-Portable-Devices](Microsoft-Windows-Portable-Devices.md)
- [Microsoft-Windows-WebcamExperience](Microsoft-Windows-WebcamExperience.md)
- [Microsoft-Windows-WinSATMediaFiles](Microsoft-Windows-WinSATMediaFiles.md)

## Package Details

### Package Size

| Release                             |   x64     |    ARM64    |
|-------------------------------------|:---------:|:-----------:|
| Windows 11 IoT Enterprise LTSC 2024 | 5,202 KB  | 8,908 KB    |
| Windows 10 IoT Enterprise LTSC 2021 | 5,559 KB  |             |

### File List

| File Name | Installed Location |
|-----------|--------------------|
| asferror.dll            | %windir%\system32\asferror.dll
| cewmdm.dll              | %windir%\system32\cewmdm.dll
| laprxy.dll              | %windir%\system32\laprxy.dll
| logagent.exe            | %windir%\system32\logagent.exe
| mswmdm.dll              | %windir%\system32\mswmdm.dll
| mswmdm.mof              | %windir%\system32\wbem\mswmdm.mof
| sqmapi.dll              | %programfiles%\windows multimedia platform\sqmapi.dll
| windowsmediadrm.admx    | %windir%\policydefinitions\windowsmediadrm.admx |
| wmasf.dll               | %windir%\system32\wmasf.dll
| wmdmlog.dll             | %windir%\system32\wmdmlog.dll
| wmdmps.dll              | %windir%\system32\wmdmps.dll
| wmidx.dll               | %windir%\system32\wmidx.dll
| wmnetmgr.dll            | %windir%\system32\wmnetmgr.dll
| wmsyspr9.prx            | %windir%\wmsyspr9.prx
| wmvcore.dll             | %windir%\system32\wmvcore.dll

## More Resources

- [Removable Packages](../Removable-Packages.md)
- [Device Optimization Overview](../Overview.md)
