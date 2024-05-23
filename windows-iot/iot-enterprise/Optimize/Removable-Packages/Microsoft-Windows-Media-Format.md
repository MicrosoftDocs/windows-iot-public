---
title: Package - Windows Media Format
titleSuffix: Windows IoT Enterprise
author: TerryWarwick
ms.author: twarwick
ms.date: 05/22/2024
ms.topic: reference
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

> [!IMPORTANT]
>
> This feature is only supported on the Windows IoT Entrprise LTSC edition.  If you choose to remove any of this package from Windows IoT Enterprise, you must ensure that your solution does not rely on functionality of the removed package. You cannot restore the package without a full reinstall of Windows IoT Enterprise LTSC.  
> For more information, see [Removable Packages System Requirements](../Removable-Packages.md#system-requirements).

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

These packages collectively provide the functionality represented by the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture). There are dependencies between each of these packages. If you elect to remove a subset of these packages, you must thoroughly test your scenarios to ensure that your customers don't encounter an issue with missing dependencies.

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
| Windows 11 IoT Enterprise LTSC 2024 | 5,200 KB  | 8,764 KB    |
| Windows 10 IoT Enterprise LTSC 2021 | 5,559 KB  |             |

### File List

| File Name | Installed Location |
|-----------|--------------------|
| asferror.dll            | %windir%\system32\asferror.dll |
| cewmdm.dll              | %windir%\system32\cewmdm.dll |
| laprxy.dll              | %windir%\system32\laprxy.dll |
| logagent.exe            | %windir%\system32\logagent.exe |
| mswmdm.dll              | %windir%\system32\mswmdm.dll |
| mswmdm.mof              | %windir%\system32\wbem\mswmdm.mof |
| sqmapi.dll              | %programfiles%\windows multimedia platform\sqmapi.dll |
| windowsmediadrm.admx    | %windir%\policydefinitions\windowsmediadrm.admx |
| wmasf.dll               | %windir%\system32\wmasf.dll |
| wmdmlog.dll             | %windir%\system32\wmdmlog.dll |
| wmdmps.dll              | %windir%\system32\wmdmps.dll |
| wmidx.dll               | %windir%\system32\wmidx.dll |
| wmnetmgr.dll            | %windir%\system32\wmnetmgr.dll |
| wmsyspr9.prx            | %windir%\wmsyspr9.prx |
| wmvcore.dll             | %windir%\system32\wmvcore.dll |

## Related Content

- [Removable Packages](../Removable-Packages.md)
- [Device Optimization Overview](../Overview.md)
